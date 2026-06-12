---
title: "xfburn won't burn image"
date: 2006-11-22
forum: General Help
---

### Post by leetrefz on 2006-11-22
xfburn cleared my cdrw very well, but when I ask it to burn my new xubuntu iso it immediately says finished with no output to view. 

Perhaps my blank disk should be mounted? it doesn't want to mount via the mount disks menu in the xfce panel so I assumed it didn't need to be though I'd think it would.

---

### Post by ingo on 2006-11-22
I've had problems with cdrws and srewed up a lot of them before I realised that a quick wipe clean doesn't work, its got to be done thoroughly every time. Could your issue be related? Try a normal cd first...

---

### Post by kerry_s on 2006-11-22
If your using edgy xfburn its screwed, You can down grade it to dapper & it will work. Just use synaptic & change the top repo to say dapper instead of edgy then reload and uninstall xfburn then reinstall the dapper version.Don't forget to change the repo back to edgy after your done. Then just don't update xfburn.

---

### Post by leetrefz on 2006-11-22
great!
but maybe I'm an idiot, I go to repositories under settings and only see third party repositories.

And it's really ok i can't mount the blank disk?

---

### Post by kerry_s on 2006-11-22
Uninstall xfburn and download and install this, it's the dapper version.-> [http://mirrors.kernel.org/ubuntu/pool/main/x/xfburn/xfburn_0.0.3svn+r21611-0ubuntu2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/x/xfburn/xfburn_0.0.3svn+r21611-0ubuntu2_i386.deb)

---

### Post by leetrefz on 2006-11-24
hey thanks man, I ended up running some gnome program that worked. gburn or somethign like that, dont know, happily running my new clean xubuntu installation. probably should follow those instructions anyway now though. 

cheers.

---

### Post by Magni on 2006-12-25
> **kerry_s said:**
> You no what, just scrap all that just uninstall xfburn and download and install this, it's the dapper version.-> [http://mirrors.kernel.org/ubuntu/pool/main/x/xfburn/xfburn_0.0.3svn+r21611-0ubuntu2_i386.deb](http://mirrors.kernel.org/ubuntu/pool/main/x/xfburn/xfburn_0.0.3svn+r21611-0ubuntu2_i386.deb)

thats a good workaround, thanks

---

