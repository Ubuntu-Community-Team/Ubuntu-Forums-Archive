---
title: "Dropbox 2.0.0 behind proxy"
date: 2013-03-26
forum: General Help
---

### Post by Jake the Peg on 2013-03-26
Hello, 
I've used dropbox without problems for several years. When I use my laptop at work, it doesn't sync immediately: I have to click on the applet and change the proxy settings from "none" to our work proxy setting. Then it syncs.

However, dropbox has upgraded from 1.6 to 2.0 (on windows it seems to offer various sharing functions, but not on ubuntu). Now the dropdown menu on the applet doesn't work when I am at work, so I can't access the option to change the proxy. At home, the default "none" proxy setting allows the program to connect to the internet and then the dropdown menu functions and I can access the proxy settings option of the applet.

So, it seems to me that Dropbox 2.0.0 has to connect first to make the dropdown menus function - perhaps related to the new sharing functions. If it doesn't connect because of proxy setting, you can't access the menu to change them.

Has anyone else this problem? Any suggestions to change the proxy settings of Dropbox in another way? This happens in both Ubuntu and Lubuntu desktop environments.

Thanks,
Jake.

---

### Post by n00b on 2013-04-17
bump.

Just want to to bump this post as I have the exact problem. 
Does anyone have a work around for this ?

---

### Post by apmcd47 on 2013-04-17
what happens if you set (export) HTTPS_PROXY, HTTP_PROXY, https_proxy and http_proxy prior to running dropboxd?

---

### Post by apmcd47 on 2013-04-18
I have just tried Dropbox 2 on my system which is behind a proxy server. My findings:

[LIST=1]
[*]I have "Proxy settings" set to "Auto-detect" by default;
[*]Upgrading from Dropbox 1 to Dropbox 2 needs no extra setting up;
[*]Removing $HOME/.dropbox resets to factory default, ie the first-time-run dialog is run;
[*]If I change the Proxy settings to "No proxy" and the restart dropbox 2 I get the same empty menu from the SysTray as mentioned by OP;
[*]I was able to restart Dropbox 1 and change the Proxy Settings to normal.
[*]
[/LIST]
So basically if you still have Dropbox 1, you can run that to reset the Proxy Settings and then run Dropbox 2. If you don't, you can remove the $HOME/.dropbox directory and go back to factory default. I would suggest that you should set the Proxy Settings to Auto-Detect if they work for you.

Andrew

---

### Post by rajhanschinmay on 2013-08-29
You can download the same from,
[https://www.dropbox.com/install?os=lnx](https://www.dropbox.com/install?os=lnx)

or
use the command line:
[h=2]Install Dropbox via command line[/h]The Dropbox daemon works  fine on all 32-bit and 64-bit Linux servers. To install, run the  following command in your Linux terminal.
**32-bit**:
cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86" | tar xzf -**64-bit**:
cd ~ && wget -O - "https://www.dropbox.com/download?plat=lnx.x86_64" | tar xzf -Next, run the Dropbox daemon from the newly created .dropbox-dist folder.
~/.dropbox-dist/dropboxd

If not then download it from:
for 32 bit, use [https://www.dropbox.com/download?plat=lnx.x86](https://www.dropbox.com/download?plat=lnx.x86)
and
for 64 bit, use [https://www.dropbox.com/download?plat=lnx.x86_64](https://www.dropbox.com/download?plat=lnx.x86_64)

and extract it manually to /home/user folder.

Hope this helps.
Thank you.

---

