---
title: "Desperate for an alternative for filemon, no linux app which does this?!"
date: 2006-10-13
forum: General Help
---

### Post by Zaggy on 2006-10-13
Hi, to come to the point:
I'm looking for an alternative for the windows application called 'Filemon' as can be seen/downloaded for free at [http://www.sysinternals.com/Utilities/Filemon.html]("http://www.sysinternals.com/Utilities/Filemon.html")

Filemon basically monitors EVERY read/write to the WHOLE harddisk, not just a single file.

[They]("http://www.sysinternals.com/AboutUs.html") did attempt to create a Linux version, but it was abandoned as it [seems]("http://forum.sysinternals.com/forum_posts.asp?TID=179&PN=1").

I've tried compiling [glsof]("http://glsof.sourceforge.net/?q=node/3") (which seems to a GUI for lsof).
The compiling part works, but the application did not present any information, neither did any part of the gui work.

Now I tried using lsof with zenity, but that would just dump the data (including net data?!) to a simple textfield over and over again.

I really would like to have a Filemon'isk application back.
Nothing annoys me more then see my hdd usage spike (while looking at the gnome system monitor) and hearing my hdd churn while not having a singe **clue** what the heck it's doing.

---

### Post by skierkegaard on 2006-10-13
I guess I don't understand what functionality you hope to gain from this windows app in linux.  Linux's file system is drastically different so that file fragmentation in the Windows sense should not be an issue.

---

### Post by doobit on 2006-10-13
> **Zaggy said:**
> I really would like to have a Filemon'isk application back.
Nothing annoys me more then see my hdd usage spike (while looking at the gnome system monitor) and hearing my hdd churn while not having a singe **clue** what the heck it's doing.

You can see everything that's going on in your computer with the top command in an open terminal. It runs in realtime so just keep a terminal open while you work and you will see every process.

---

### Post by Zaggy on 2006-10-13
This tool is **not** to do **anything** with file fragmentation, also top does not (by my knowledge) show **which** files are accessed/written by what program by which user.

---

### Post by ssalman on 2006-10-13
> **Zaggy said:**
> This tool is **not** to do **anything** with file fragmentation, also top does not (by my knowledge) show **which** files are accessed/written by what program by which user.

I've used filemonitor on windows before, so I know what you are looking for... I'm not sure I've ever seen one for linux... but I'm a newbie...

A quick search on google turnes out [this]("http://threebit.net/mail-archive/linux-kernel/msg02391.html") similar question. I'm not on my linux machine so I can't test it... give "inotify" a try and post back... may be it is the answer.

Good luck.

---

### Post by Zaggy on 2006-10-13
> **ssalman said:**
> I've used filemonitor on windows before, so I know what you are looking for... I'm not sure I've ever seen one for linux... but I'm a newbie...

A quick search on google turnes out [this]("http://threebit.net/mail-archive/linux-kernel/msg02391.html") similar question. I'm not on my linux machine so I can't test it... give "inotify" a try and post back... may be it is the answer.

Good luck.

Thanks for the response, I'll look into it!

---

### Post by Zaggy on 2006-10-13
Well, it seems Linux isn't as far as Windows with this, I have to put things in the kernel myself and use a script to get this to work.

I found the package fam in the ubuntu repository,(File Alteration Monitor
FAM monitors files and directories, notifying interested applications
of changes.) but after marking it for install I see it wants to uninstall a whole bunch of usefull apps: alacarte, eclipse, gedit and a lot more.

I'll keep waiting :/

---

### Post by Ipsissimus on 2007-04-04
We've been using Tripwire, also in the repositories.  It monitors all files for any changes via hash checking.  Can be used for security purposes, its quite robust.

-- Ipsissimus

---

### Post by yonatanz on 2007-04-07
Zaggy, I got good news for you. It is possible to achieve similar functionality to filemon with a linux 2.6.1 or newer kernel.
what you need to do is the following:
1. Make sure that syslog doesn't log kern.debug to a file(check /etc/syslog.conf). if it does, disable it temporarily (better), or stop syslog altogether (worse, because you will eliminate one possible cause of the disk activity)
2. type:
echo 1 > /proc/sys/vm/block_dump
3. in bash, type (modify to fit your favourite shell):
while true; do dmesg -c; sleep 1; done;

This effectively gives you a realtime live view of all disk activity
note that if you didn't dmesg -c since you booted, dmesg might contain a lot of info in the buffer, so let it barf everything onto the screen before attempting to actually read it.

remember to restore things back to the way they were when you are done:
1. echo 0 > /proc/sys/vm/block_dump
2. restore syslog activity and/or kern.debug logging

Enjoy!

---

### Post by Zaggy on 2007-04-18
Thanks for the responses, I'll give it a try :)

---

### Post by motin on 2008-03-01
Maybe you could explain what your main goal with this application is?

lsof (great guide here: [http://dmiessler.com/study/lsof/](http://dmiessler.com/study/lsof/)) will get you all information you want - albeit without a stable GUI as of now. 

If you want to monitor disk read/write activity per process, you need to recompile your kernel with the CONFIG_TASK_IO_ACCOUNTING option enabled, as well as install the sysstat package from the Hardy repos using prevu.

---

### Post by Zaggy on 2008-05-23
> **motin said:**
> Maybe you could explain what your main goal with this application is?

lsof (great guide here: [http://dmiessler.com/study/lsof/](http://dmiessler.com/study/lsof/)) will get you all information you want - albeit without a stable GUI as of now. 

If you want to monitor disk read/write activity per process, you need to recompile your kernel with the CONFIG_TASK_IO_ACCOUNTING option enabled, as well as install the sysstat package from the Hardy repos using prevu.

Sorry for the late response.

To put it blunt, I get tired of seeing disk activity and not being able to see what application is responsible for it.

Now in Windows (being the lazy GUI user I am) I can fire up FileMon and I can see whatever program is reading/writing/whatever to whichever path.

Now in Linux I have to recompile the kernel and use a CLI application? 
I sure wish I was a coder so I could make it myself :(

---

### Post by roaldz on 2008-05-23
> **Zaggy said:**
> Sorry for the late response.

To put it blunt, I get tired of seeing disk activity and not being able to see what application is responsible for it.

Now in Windows (being the lazy GUI user I am) I can fire up FileMon and I can see whatever program is reading/writing/whatever to whichever path.

Now in Linux I have to recompile the kernel and use a CLI application? 
I sure wish I was a coder so I could make it myself :(

This is caused by the trust people have in windows. I know that in Ubuntu (and linux in general) it´s not necessary to do these things to make sure it´s running well.
I always use ¨top¨ to monitor which process is using the disk. It´s all I need.

---

### Post by Zaggy on 2008-05-23
> **roaldz said:**
> This is caused by the trust people have in windows. I know that in Ubuntu (and linux in general) it´s not necessary to do these things to make sure it´s running well.
I always use ¨top¨ to monitor which process is using the disk. It´s all I need.

How do I use top for disk activity?

---

