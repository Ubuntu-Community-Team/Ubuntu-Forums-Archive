---
title: "Where do I find hardware information in hardy?"
date: 2008-04-27
forum: General Help
---

### Post by sternkanz on 2008-04-27
Hi, title says it all. There used to be a "Hardware Information" you could click on under one of the "System" menus and I cannot find it now. Could anyone tell me how to get to it?

Also, where do I mess around with graphics cards and drivers and all that? It used to be covered under "Screen and Graphics" but that is gone now too.

Thanks!

Stern

---

### Post by ghost_ryder35 on 2008-04-27
for drivers and what not there under
system, administration, hardware drivers
 
if you need to activate some restricted drivers make sure you have third party reposotories activated under system,administration,software sources
 
for hardware information i think it moved to the applications menu some where (but dont quote me on that)

---

### Post by sternkanz on 2008-04-27
Thanks for the quick reply,

System->Administration->Hardware drivers 
just shows a blank window saying: "No proprietary drivers are in use on this system."

I found "Screen and Graphics" if I edit the "Applications" menus. It's in "Other->Screens and Graphics". I still haven't found Hardware Information though.

Stern

---

### Post by ghost_ryder35 on 2008-04-27
check out system, prefrences, personalize or something along those lines

---

### Post by sternkanz on 2008-04-27
I can't seem to find it...

---

### Post by olskar on 2008-04-27
run "sudo aptitude install hardinfo" in a terminal.
For some strange reason I think hardwareinfo has been removed by default.

---

### Post by sternkanz on 2008-04-27
Many thanks!

Stern

---

### Post by pastalavista on 2008-04-27
In terminal just type: lshw

You can also right click on the applications panel and "edit menus" where you'll see all your installed applications and check or uncheck what you want to appear in the menus.

---

### Post by mark.kristos on 2008-06-15
> **olskar said:**
> run "sudo aptitude install hardinfo" in a terminal.
For some strange reason I think hardwareinfo has been removed by default.

mark@ubuntu-laptop:~$ sudo aptitude install hardinfo
[sudo] password for mark: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following NEW packages will be automatically installed:
  libsoup2.2-8 
The following NEW packages will be installed:
  hardinfo libsoup2.2-8 
0 packages upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 337kB of archives. After unpacking 995kB will be used.
Do you want to continue? [Y/n/?] y
Writing extended state information... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/main libsoup2.2-8 2.2.105-4 [96.8kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe hardinfo 0.4.2.3-3 [240kB]    
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hardy/universe hardinfo 0.4.2.3-3 [240kB]    
Fetched 247kB in 4min49s (853B/s)                                               
Selecting previously deselected package libsoup2.2-8.
(Reading database ... 127073 files and directories currently installed.)
Unpacking libsoup2.2-8 (from .../libsoup2.2-8_2.2.105-4_amd64.deb) ...
Selecting previously deselected package hardinfo.
Unpacking hardinfo (from .../hardinfo_0.4.2.3-3_amd64.deb) ...
Setting up libsoup2.2-8 (2.2.105-4) ...

Setting up hardinfo (0.4.2.3-3) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
mark@ubuntu-laptop:~$ hardinfo

This adds an icon to System>Preferences> System Profiler and Benchmark

Thumbs up, now we are jammin :guitar:

---

