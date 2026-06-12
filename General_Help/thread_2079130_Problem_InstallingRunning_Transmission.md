---
title: "Problem Installing/Running Transmission"
date: 2012-11-01
forum: General Help
---

### Post by darkforcesjedi on 2012-11-01
I am having a problem setting up the transmission bt client (Ubuntu 12.04.1 LTS (GNU/Linux 3.2.0-30-generic i686)).

When installing I get the following error:
```
Setting up transmission-daemon (2.51-0ubuntu1.1) ...
 * Starting bittorrent daemon transmission-daemon                                     /usr/bin/transmission-daemon: error while loading shared libraries: librtmp.so.0: cannot open shared object file: No such file or directory
invoke-rc.d: initscript transmission-daemon, action "start" failed.
dpkg: error processing transmission-daemon (--configure):
 subprocess installed post-installation script returned error exit status 127
Setting up transmission-cli (2.51-0ubuntu1.1) ...
Errors were encountered while processing:
 transmission-daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up transmission-daemon (2.51-0ubuntu1.1) ...
 * Starting bittorrent daemon transmission-daemon                                     **/usr/bin/transmission-daemon: error while loading shared libraries: librtmp.so.0: cannot open shared object file: No such file or directory**
invoke-rc.d: initscript transmission-daemon, action "start" failed.
dpkg: error processing transmission-daemon (--configure):
 subprocess installed post-installation script returned error exit status 127
Errors were encountered while processing:
 transmission-daemon

```

I was about to ask what to do to fix this but I figured it out while researching the problem so I am posting the result here in case someone else has a similar issue.

I used find to locate librtmp.so.0:
```
find / | grep librtmp.so.0
```

It located the file at "/usr/lib/i486-linux-gnu/librtmp.so.0" so I created a link in /lib:
```
sudo ln -s /usr/lib/i486-linux-gnu/librtmp.so.0 librtmp.so.0
```

Then I reinstalled the transmission packages using synaptic.

:KS

---

### Post by Temujin_12 on 2012-12-03
BTW, ran into the following error installing "curl" on Ubuntu 12.04 server:

> 
$ curl
curl: error while loading shared libraries: librtmp.so.0: cannot open shared object file: No such file or directory


This symlinking approach fixed this issue with curl for me.

---

