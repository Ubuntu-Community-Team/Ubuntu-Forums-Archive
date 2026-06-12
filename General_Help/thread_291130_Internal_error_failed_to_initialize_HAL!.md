---
title: "Internal error: failed to initialize HAL!"
date: 2006-11-02
forum: General Help
---

### Post by elvisd on 2006-11-02
Hi all,

since 2-3 days when i logon i have an error box saying:

Internal error: failed to initialize HAL!

But seems that  everything is working.
I have tried to reinstall hal and acpi as found on another post. problem persists.

Can someone tell me where can i find more log messages?
Or better, how can i resolve this?

I don't know what have i done to generate this problem. maybe an update or some installation... 

thank you very much

---

### Post by lordgibbness on 2006-11-02
Sounds like similar issue to the one I had. Take a look at [http://ubuntuforums.org/showthread.php?t=289654](http://ubuntuforums.org/showthread.php?t=289654)

---

### Post by elvisd on 2006-11-02
My services are correctly accessible and dbus is started. Other ideas?
Before posting i tried lordgibbness solution but doesn't solve my situation.

---

### Post by Ecthelion on 2006-11-03
I've sometimes the same problem:
Starting up, "Failed to initialize HAL!" message and my cpu turning crazy
When I then reboot my xserver (Ctrl-Alt-Backspace), mostly the problem is gone...
I've this problem since I installed Beryl... maybe it's related...
Have you installed Beryl or Compiz or... ?

---

### Post by nickmcg on 2006-11-04
I get this message every time I boot up, yet everything seems to be working.

I can't find any error messages in any logs, and I would like to get to the root of this irritating problem.

I've tried reinstalling HAL etc. to no avail.

I do use automatic user logon, I have no samba mounts defined. No Beryl or compiz.

Nick

---

### Post by Ecthelion on 2006-11-04
Because of network problems (no network when I used automatic logon, I had to go to System > ... > network and then switch it off and back on, then it worked) I changed that automatic login to a timed login...
So it logs in after 5 sec...

Since then I never get that message again and I don't have those network problems anymore...

Maybe it's worth trying...

---

### Post by nickmcg on 2006-11-04
The 5 sec delay seems to work - it would be interesting to find out what the timing issue might be as I still haven't found any error messages.

Thanks for your suggestion

Nick

---

### Post by MrJokester on 2008-03-06
just reinstal hal and it must work like it usual
use this comand
```
sudo apt-get --reinstall install hal
```
and restart your mashin whit CTRL+ALT+BACKSPACE
after do this
start nautilus as a root
go to /etc/ look for the folder rc2.d rename s12hal to s13hal, or S50dbus to S12dbus.
then
```
sudo gedit /etc/init.d/rc
```
and change this line 
"CONCURRENCY=shell"
to "CONCURRENCY=none"
save it and thats it

---

### Post by klco on 2008-03-10
MrJokester, 
Thanks for the tip!

---

### Post by sosipator on 2008-03-20
i have exactly the same error message on the startup. 
CONCURRENCY=none, and when I try to reinstall Hal it gives me this:

sosipator@ubuntu:~$ sudo apt-get --reinstall install hal
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  pulseaudio
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 2 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up hal (0.5.9.1-6ubuntu5) ...
 * Reloading system message bus config...                                [ OK ] 
 * Starting Hardware abstraction layer hald                                     invoke-rc.d: initscript hal, action "start" failed.
dpkg: error processing hal (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 hal
E: Sub-process /usr/bin/dpkg returned an error code (1)


any ideas?

---

### Post by oldgoat on 2008-03-21
MrJokester - nice post - thank you!  After having to run fsck manually and rewriting a bunch of what looked like hardware locations? I was getting the HAL error.  It only took reinstalling HAL to fix the problems.

---

