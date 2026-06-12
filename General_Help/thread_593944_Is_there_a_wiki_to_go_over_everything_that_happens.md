---
title: "Is there a wiki to go over everything that happens during statup?"
date: 2007-10-27
forum: General Help
---

### Post by thelocust on 2007-10-27
[COLOR=#666666]I am looking for a manual/wiki that goes over step by step of everything that goes on during the startup. I want this mainly for general knowledge and to break the crap out of my system. If this doesn't exist which I am guessing is the case, were do all the commands come from so that I can dig through that file (hopefully just one) and figure stuff out for my self. Thanks for any inputs.[/COLOR]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]

---

### Post by linfidel on 2007-10-27
> **thelocust said:**
> [COLOR=#666666]I am looking for a manual/wiki that goes over step by step of everything that goes on during the startup. I want this mainly for general knowledge and to break the crap out of my system. If this doesn't exist which I am guessing is the case, were do all the commands come from so that I can dig through that file (hopefully just one) and figure stuff out for my self. Thanks for any inputs.[/COLOR]
[FONT=Times New Roman][/FONT]I've seen the information that would at least give a starting point; from there, you can follow it through because it's basically just a shell script that runs various other scripts, depending on configuration files.

Now, I know this isn't much help, but I've been thinking about doing the same thing as you.  I want to document the the flow for the same reasons you do, and perhaps put them on a web site, like a blog perhaps.  If there is enough interest, maybe we could start a wiki somewhere.

I'll keep checking back here, and post info when I get it.  You can do the same.

---

### Post by thelocust on 2007-10-27
> **linfidel said:**
> I've seen the information that would at least give a starting point Were did you see it? 
 
[COLOR=#666666]I definitely think a wiki would be very helpful to allot of people. I just want to know what my system is doing and maybe get rid of some stuff that I don't use.[/COLOR]

---

### Post by Rinzwind on 2007-10-27
Semi-offtopic: You can get alot of info from bootlog and syslog (gnome: system -> admin -> systemlogs)
This is the WIKI page for all the logs: [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)
There's also a kernel log.

A ubuntu how to about speeding up the boot process:
[http://ubuntuforums.org/showthread.php?t=89491&highlight=boot+proces](http://ubuntuforums.org/showthread.php?t=89491&highlight=boot+proces)
Is not what you asked but this explains what is started en when it's started during boot. There's a bit in the startpost about the runlevels.

On-topic:
[http://itreviews.blogspot.com/2006/05/linuxs-boot-process-explained.html](http://itreviews.blogspot.com/2006/05/linuxs-boot-process-explained.html) 
It explains the boot from turning on your machine and all the files inside /etc/rc.d/.

---

### Post by thelocust on 2007-10-27
Thanks I'll have to dig into that stuff on my day off.

---

### Post by linfidel on 2007-10-27
> **thelocust said:**
> Were did you see it? 
 
[COLOR=#666666]I definitely think a wiki would be very helpful to allot of people. I just want to know what my system is doing and maybe get rid of some stuff that I don't use.[/COLOR]I've started a blog and an online google document, although nothing that's ready for viewing.  I hope to digest a lot of the general knowledge, and regurgitate it into something that's oriented toward Ubuntu and Debian.  I'll try to include examples from existing config files on my system, which are fairly standard, so far.

One good source I came across is here: [http://users.rsise.anu.edu.au/~okeefe/p2b/power2bash/power2bash.html]("http://users.rsise.anu.edu.au/~okeefe/p2b/power2bash/power2bash.html")

Also, wikipedia has a lot of good info.

---

