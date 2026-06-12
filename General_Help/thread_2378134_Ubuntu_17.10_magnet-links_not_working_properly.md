---
title: "Ubuntu 17.10 magnet-links not working properly"
date: 2017-11-20
forum: General Help
---

### Post by Hasimir on 2017-11-20
Hi :)
I'm having a problem with magnet-links.
When I click on a **magnet-link** in Chrome I receive a popup prompt from **xdg-open** asking me if I want to allow the action.
If I do, it launches Transmission and starts the download. No problem here.
There is also a nice box to "**Always open these types of links in the associated app**".

My problem is: if I check the box the setting is NOT saved. Next time i click a magnet-link I will still see a popup asking me what to do.
Is there a way to fix this behaviour?

Thanks! :D

---

### Post by #&amp;thj^% on 2017-11-20
> **Hasimir said:**
> Hi :)
I'm having a problem with magnet-links.
When I click on a **magnet-link** in Chrome I receive a popup prompt from **xdg-open** asking me if I want to allow the action.
If I do, it launches Transmission and starts the download. No problem here.
There is also a nice box to "**Always open these types of links in the associated app**".

My problem is: if I check the box the setting is NOT saved. Next time i click a magnet-link I will still see a popup asking me what to do.
Is there a way to fix this behaviour?

Thanks! :D

Do you have this file?
**".local/share/applications/mimeapps.list"**
And if you do, may i see the contents of that file.
```
gedit .local/share/applications/mimeapps.list
```
Paste back please.

---

### Post by Hasimir on 2017-11-20
the result is this:
> 
[Default Applications]
text/html=google-chrome-unstable.desktop
x-scheme-handler/http=google-chrome-unstable.desktop
x-scheme-handler/https=google-chrome-unstable.desktop
x-scheme-handler/about=google-chrome-unstable.desktop
x-scheme-handler/unknown=google-chrome-unstable.desktop
application/vnd.adobe.air-application-installer-package+zip=AdobeAIR-application-vnd.adobe.air-application-installer-package+zip.desktop;


---

### Post by #&amp;thj^% on 2017-11-20
> **Hasimir said:**
> the result is this:


I had to add these in that same file. Add the association to the two sections in the file like this (leaving other entries in those sections intact):

```
[Default Applications]
x-scheme-handler/magnet=transmission-gtk.desktop

[Added Associations]
x-scheme-handler/magnet=transmission-gtk.desktop

```
Log out and log back in for the change to take effect.

---

### Post by Hasimir on 2017-11-20
Done.
Log out and in included.
No effect.

This is how the file looks like with the modifications:
> 


[Default Applications]
text/html=google-chrome-unstable.desktop
x-scheme-handler/http=google-chrome-unstable.desktop
x-scheme-handler/https=google-chrome-unstable.desktop
x-scheme-handler/about=google-chrome-unstable.desktop
x-scheme-handler/unknown=google-chrome-unstable.desktop
application/vnd.adobe.air-application-installer-package+zip=AdobeAIR-application-vnd.adobe.air-application-installer-package+zip.desktop;


[Default Applications]
x-scheme-handler/magnet=transmission-gtk.desktop


[Added Associations]
x-scheme-handler/magnet=transmission-gtk.desktop


---

### Post by Hasimir on 2017-11-20
I noticed, running the command **whereis** I can find transmission-gtk but not transmission-gtk.desktop
is this normal?

---

### Post by #&amp;thj^% on 2017-11-20
> **Hasimir said:**
> Done.
Log out and in included.
No effect.

This is how the file looks like with the modifications:

Hmmm?
Lets see what you have installed then:
```
apt policy transmission-gtk
```

---

### Post by Hasimir on 2017-11-20
this...
> 
transmission-gtk:
  Installed: 2.92-2ubuntu3
  Candidate: 2.92-2ubuntu3
  Version table:
 *** 2.92-2ubuntu3 500
        500 [http://de.archive.ubuntu.com/ubuntu](http://de.archive.ubuntu.com/ubuntu) artful/main amd64 Packages
        100 /var/lib/dpkg/status




---

### Post by #&amp;thj^% on 2017-11-20
Well run these two commands:
```
xdg-mime default transmission-gtk.desktop application/x-bittorrent
xdg-mime default transmission-gtk.desktop x-scheme-handler/magnet

```
Now we can check if that  worked with:
```
xdg-open "magnet:?xt=urn:btih:f41989f9797a88505f9e258d5e5d1354c3731a99" 
```
Transmission should now open for to download Ubuntu 13.04.

---

### Post by Hasimir on 2017-11-20
Immediately after executing the two commands I tried opening the link you provided by using the third command.
It works.
So I went over to Chrome and tried clicking on a magnet-link from there.
Same old problem.
I restarted and tried again.
Same problem.


( PS: thanks a lot for the support! :) )

---

### Post by #&amp;thj^% on 2017-11-20
This might have something to do with why..
"google-**chrome-unstable**"
I'm at a loss then.

---

