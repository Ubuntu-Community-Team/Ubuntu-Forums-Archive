---
title: "Changing Filesystem Letter?"
date: 2007-12-02
forum: General Help
---

### Post by Planets on 2007-12-02
Hello,

Wubi didn't seem to want to install on my C:\ drive, so I installed it to E:\ and then copied to to C:\. Problem is now, Ubuntu seems to think it's still on E:\. Any way to fix this?

---

### Post by njparton on 2007-12-02
You probably need to update the registry so I'd try again and leave it on e:\ if possible.

Otherwise you need to run regedit and find the appropriate location. Not for beginners so don't attempt if you don't know what you're doing.

---

### Post by Planets on 2007-12-02
I would leave it on E:\, but that is a portable/back up drive. Could you point me in the right direction?

---

### Post by anon2243 on 2007-12-02
that sounds like a bootmenu file issue maybe try easybcd?

---

### Post by Planets on 2007-12-03
It boots just fine, but I can only see the files in my E:\ drive.

---

### Post by ago on 2007-12-03
You can move a Wubi installation to different drive, the issue is that the uninstaller will get confused and will not work properly. 

Wubi will always mount the partition containing wubi under /host, any other partition can be mounted as usual

---

### Post by Planets on 2007-12-03
Right. The problem though is that Wubi is on C:\ right now, but it thinks the host folder is on E:\. Basically this means I have no host folder to view if E:\ is not turned on (it's in an external case).

---

### Post by ago on 2007-12-03
You also have to edit /ubuntu/disks/boot/grub/menu.lst

And change the root device

---

### Post by Planets on 2007-12-03
Would you mind explaining how to do that, sir?

---

### Post by ago on 2007-12-03
What version of wubi are we talking about?

---

### Post by Planets on 2007-12-03
The latest revision from the devel/minefield site for the 7.10 installer.

---

### Post by ago on 2007-12-03
Then edit the line that starts with "kernel" there should be something like:

root=UUID=FAA4EAD3A4EA9205

change it to root=/dev/sda1

where "sda1" indicates the first partition (1) on the first disk (a), modify to point to the correct disk/partition.

---

### Post by Planets on 2007-12-03
Didn't seem to work. For example, when I try to install something, I get this error in the terminal:

E: Couldn't find package avant-window-navigator-svn

---

### Post by Planets on 2007-12-04
Hello Ago,

I decided to attempt to re-install Wubi on my C:\ drive to try to resolve this issue. There's a problem, however. Wubi won't start now. I double click it, a UAC prompt comes up, then nothing happens. Any ideas?

---

### Post by ago on 2007-12-04
> **Planets said:**
> Didn't seem to work. For example, when I try to install something, I get this error in the terminal:

E: Couldn't find package avant-window-navigator-svn

that might be a completely different issue

---

### Post by ago on 2007-12-04
> **Planets said:**
> Hello Ago,

I decided to attempt to re-install Wubi on my C:\ drive to try to resolve this issue. There's a problem, however. Wubi won't start now. I double click it, a UAC prompt comes up, then nothing happens. Any ideas?

Type %temp% in your file browser and look at the log in there

---

### Post by Planets on 2007-12-04
I fixed it. It seems Wubi won't start if an external HD is connected (and turned on) as a USB drive. That was my case, anyway.

---

### Post by Planets on 2007-12-04
Ago, did you have any ideas as to why I am getting the error from the E:\ drive from the earlier post?

---

### Post by ago on 2007-12-05
Wubi scans all disks for an ISO/previous installations, it might be that some USB disk make it crash when it tries to access them, but it's difficult to say for sure without the logs

---

### Post by Planets on 2007-12-05
I believe this is the new log.

---

### Post by Planets on 2007-12-09
Ago? Any ideas?

---

### Post by ago on 2007-12-10
Can you provide me with a clean log? Delete the previous log and make it crash then send the log. In the log above there are several runs stopped at different times

---

