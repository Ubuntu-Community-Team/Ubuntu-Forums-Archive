---
title: "Vino to TightVNC Viewer on Windows 7: target actively refused"
date: 2014-07-12
forum: General Help
---

### Post by quadrplax on 2014-07-12
I have an Ubuntu machine (the laptop in my signature) that I am using as a server. I got it set up to use with Vino and TightVNC to access it. In order to do this, I had to disable encryption for some odd reason:
```
gsettings set org.gnome.Vino require-encryption false
```
Otherwise TightVNC would say it didn't understand the encryption type. For a while it worked, but now I get this error message whenever I try to connect:
```
Error in TightVNC Viewer: No connection could be made because the target machine actively refused it.
```
I can still connect via PuTTY just fine.

EDIT: It just worked after a reboot, but I tried rebooting before, so it seems like it's inconsistent. The server will be on suspend overnight and I first lost access when waking from a suspend, so therefor my problem is not solved. Also not sure if this is related but I got a system problem detected dialog box in the center and top-left of the screen. The top left one doesn't go away no matter how many times I report it.

---

### Post by steeldriver on 2014-07-12
In my experience, that particular message indicates that Vino has been configured to only accept connections on the loopback interface, and you are trying to connect without first setting up an SSH tunnel. How are you connecting exactly?

---

### Post by quadrplax on 2014-07-13
I open TightVNC, enter the IP, and click Connect. I've looked through  the options and nothing looks important. If it wants me to do something  like that, I may as well disable it, this is all over intranet so I  don't need security.

---

### Post by quadrplax on 2014-07-16
Bump, because today the host is deciding to actively refuse my connection even after reboot

---

### Post by steeldriver on 2014-07-16
Are you sure the VNC port is not visible from outside your LAN? it has the symptoms of vino-server collapsing under the weight of intrusion attempts

Is your ~/.xsession-errors file filling with messages from vino-server by any chance?

---

### Post by quadrplax on 2014-07-16
.xsession-errors:
```
Script for ibus started at run_im.
Script for auto started at run_im.
Script for default started at run_im.
```
Doesn't look like much of an error log to me. The only ports I have forwarded to that computer are 7 and 9 for Wake On Lan -- One of my main purposes for this server right now is to host a Minecraft server, but I don't want it to be running 24/7, so if they want to play they can just turn it on with wakeonlan.me.

---

### Post by steeldriver on 2014-07-16
OK in that case I'm out of ideas

---

### Post by sp40140 on 2014-07-16
Try this:
[https://bugs.launchpad.net/ubuntu/+source/vino/+bug/1290666](https://bugs.launchpad.net/ubuntu/+source/vino/+bug/1290666)
The fixes suggested worked for me. Also, I had same issue. The only diff was that when I used ubuntu (Reminna) as client to vnc it worked but didn't work from any other pltaform (iOS, android, windows). The suggested fix on this bug page fixed it.

---

### Post by quadrplax on 2014-07-17
>                         Kyle Jackson (kylejackson)
-1.
sudo apt-get install dconf-editor

 and start it...
-2.
org > gnome > desktop > applications > remote-access
-3.
disable "REQUIRE-ENCRYPTION"


              

I had already done this via command line, as you can see in my first post. As I said, occasionally it will work, but not most of the time.

---

### Post by epachamo on 2015-04-23
I had the same problem.  Then tried connecting to a port higher than 5900 and was able to connect.

Try connecting to port 5901.

---

