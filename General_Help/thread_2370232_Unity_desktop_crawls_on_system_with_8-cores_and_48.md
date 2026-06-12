---
title: "Unity desktop crawls on system with 8-cores and 48gb of RAM"
date: 2017-08-31
forum: General Help
---

### Post by gbambo on 2017-08-31
I checked minimum system requirements. I meet them. Did they forget to mention the need for an exotic graphics card? I am only using mobo integrated video. Windows would scream on this system. And Windows is supposed to be a pig.

I tried to tweak it to be less graphic intensive. Followed an in depth article with step-by-step instructions on which settings to adjust and where to find them. Only I can't find a single item mentioned! All relevant menus, apps, and applications appear missing from my desktop.

By crawl, I mean I could redraw the screen faster using a crayon than the system does using whatever inappropriate peripheral it appears to have delegated the task to.

How on Earth is this outcome possible?

Maybe I am not experienced enough to use this OS? I only have 40 years experience with computers.

I have been installing Ubuntu over and over on the same server. Everytime it comes up crippled. Debian installs show no similar issue, but I wanted to deploy LXD. I have downloaded installer anew each time, so this is not about a corrupted install image.

---

### Post by TheFu on 2017-09-02
What do the log files say?
Which drivers are being used for storage and the GPU?

40 yrs on Windows or OS/2 means nothing.  It usually warps minds. ;)  

To use LXD, you don't need a GUI.

---

### Post by gbambo on 2017-09-02
I know I don't need a GUI, but on occassion I get exhausted by the CLI.

Afraid I can not provide much more detail as I overwrote that install already.

Which log files. Exactly what is there full path? At least I can try to consult them next time.

I think you overstate 40 years on Windows or OS/2 means nothing. For one thing, no those OS's are not 40 years old. But there are transferable skills. I know what a kernel is, how a command line works, and what the flavors of RAID are and how to configure them. The GUI interfaces have more in common than distinguished them. The terminology even more so. I have configured Linux before and used it. What ever I might be, I am not a Class 0 Noob.

---

### Post by TheFu on 2017-09-02
Log files: [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)  (I googled "ubuntu log files" ).
I would use **egrep** to find issues, warnings, errors across all the log files, but you are free to use whatever tools you like for searching. There are many.

Still would like to know which drivers are being used too.  Sometimes the driver options need to be tweaked or the wrong driver is being used.  **lshw** can show that.

---

### Post by vasa1 on 2017-09-02
> **gbambo said:**
> ... Followed an in depth article with step-by-step instructions on which settings to adjust and where to find them. Only I can't find a single item mentioned! All relevant menus, apps, and applications appear missing from my desktop.

...
Do you have some issue with providing the link to this "in depth article" article you followed?

---

