---
title: "Utorrentz installation documentation for Ubantu 12.10 for Intel 64 bit processor"
date: 2013-03-16
forum: General Help
---

### Post by karansingh27 on 2013-03-16
Hi,

If you are using a Intel 64 bit processor, usual documented process for installing and running the utorrentz might not work properly.

Tried and tested process include:

usual downloadable version is 32 bit and will not work properly with 64 bit processors. so, download from below link

download from : [http://www.utorrent.com/downloads/complete?os=lin&track=stablex64](http://www.utorrent.com/downloads/complete?os=lin&track=stablex64)


Remember: you will be required to use the sudo before commands as its required to access the root commands even in case you are an admin/ single user

Below command will extract the files from the downloaded file name: "utorrent-server-3.0-ubuntu-10.10-27079.x64.tar.gz" to location local/opt folder**sudo tar utorrent-server-3.0-ubuntu-10.10-27079.x64.tar.gz -C /opt/**


Below command will change the permissions for the extracted folder
**sudo chmod -R 777 /opt/utorrent-server-v3_0/**


Below command will do the required configuration and will create required files into the usr/bin/utserve folder
**sudo ln -s /opt/utorrent-server-v3_0/utserver /usr/bin/utserve**


You will be required to run this command every time you require the utorrentz to start
**utserver -settingspath /opt/utorrent-server-v3_0/**


If you encounter an error in starting the utorrentz then: (it is required to be done only once/ first time)
Below command will install the required library:[B]
sudo apt-get install libssl0.9.8[/B]


Now that uTorrent server is started, open your web browser (Firefox) and type the address below.
[B][http://localhost:8080/gui/](http://localhost:8080/gui/)

[/B]Hurry!! your utorrentz is up and running.
By default all the downloaded files will be saved in home. (change location if require).

Also, if you are experiencing the utorrentz is not working at its optimum download speed, try disabling the Firefox IPv6.

---

