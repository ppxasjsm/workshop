# Workshop Server (and how to download at home)

The workshops are running on a set of cloud servers provided by the [Microsoft Azure Kubernetes Service](https://docs.microsoft.com/en-us/azure/aks/).

This has been configured to provide enough resource for *up to 40 people* to log in at the same time. There are no usernames or passwords. To log in, please click the below link (will open in new tab):

<a href="http://137.117.134.245/hub/tmplogin" target="_blank">Login to server</a>

Please only click this once, as it will log you into a new session. This may take between 30-60 seconds, so please be patient. *DO NOT CLICK MULTIPLE TIMES*, else you will launch too many sessions and will block anyone else from connecting.

## Reconnecting to the server

If you accidentally close the browser page you can reconnect to the server with your existing login using the below link (opens in new tab):

<a href="http://137.117.134.245" target="_blank">Reconnect to server</a>

## Logging out when you are finished

*PLEASE LOG OUT WHEN YOU ARE FINISHED*. You can log out by clicking on the "Logout" icon in the top right of the screen. Logging out will free up your session so that it can be used by someone else.

Note that you will be kept logged in for as long as the server page is open in your browser. You will only be automatically logged out about 40 minutes after you have closed the server page. 

Also please note that all of your files will be deleted after you log out from the server. There is no way for us to save or retrieve your files. Please ensure you download anything you need before logging out.

## Backup servers

If for some reason the workshop server above is not available, you can try
one of the backup servers below.

* Backup 1 (Azure-Europe) : <a href="http://51.145.134.181/hub/tmplogin" target="_blank">Log in</a> | <a href="http://51.145.134.181" target="_blank">Reconnect</a>
* Backup 2 (Azure-USA) : <a href="https://workshop.biosimspace.org/hub/tmplogin" target="_blank">Log in</a> | <a href="https://workshop.biosimspace.org" target="_blank">Reconnect</a>
* Backup 3 (Oracle-Europe) : <a href="http://130.61.69.221/hub/tmplogin" target="_blank">Log in</a> | <a href="http://130.61.69.221" target="_blank">Reconnect</a>

(note that Backup Server 3 is kindly provided by the 
[Oracle Cloud Infrastructure](https://cloud.oracle.com/home))

## Browser compatibility

The 3D molecule viewer embedded in the Jupyter notebooks requires that you 
access the workshop using a modern browser that supports WebSockets (e.g
chrome, firefox, safari, edge and modern versions of internet explorer).
You can test if your browser supports WebSockets by 
<a href="http://websocketstest.com" target="_blank">visiting this page</a>.

## Server details

Once logged in, you will find a [JupyterHub](https://jupyter.org) browser with directories for all of the workshops. The instructions that come with each workshop will tell you which directory to use.

You will be allocated up to 2 cores and 1.8 GB of memory on the server, as it is intended for demonstration and training rather than production calculations.

## Running the workshop at home

The server will remain online for the foreseeable future, and you are welcome to log in and use it after the workshop week is over. Please do not use the server during the workshop week when it is in use by other people (unless you are signed up to attend that workshop).

All software used during the workshop is open source, and so the workshop server image is available for free download. It is available on [docker](https://cloud.docker.com/swarm/chryswoods/repository/docker/chryswoods/bss-workshop/general). You can download and run it on your own computer by installing docker and then typing;

```
docker run -it --rm chryswoods/bss-workshop:latest
```

The image is at least 10GB in size, so may take a while to download (and you must have at least 10GB of free disk space).

This will download and run the image, starting a Jupyter browser which you can connect to using the URL that will be printed out, looking something like;

```
    Copy/paste this URL into your browser when you connect for the first time,
    to login with a token:
        http://localhost:8888/?token=2759c17079a3922e7942946e4933b92a1cc06013d22615f7
```

Note that the image can only be run on computers with X86-64 processors that support AVX instructions (e.g. like most Intel processors since 2011).

The workshop image will be updated over time. To get the latest version please run 

```
docker pull chryswoods/bss-workshop:latest
```

You should also run the command 

```
update_workshops
```

inside the bash terminal in the Jupyter session to ensure that you have updated the workshop material itself to the latest version.

If you are running the image on a Mac in OS X, then be aware that the OS X version of docker can silently corrupt libraries. If you find that Python modules cannot import because the library is not recognised as "elf", then you need to re-install the module. For example, if `mdtraj` cannot import, then you can reinstall using

```
conda install mdtraj
```