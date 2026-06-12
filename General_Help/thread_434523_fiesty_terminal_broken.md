---
title: "fiesty terminal broken"
date: 2007-05-06
forum: General Help
---

### Post by ejohnston on 2007-05-06
i just installed xubuntu 7.04 on my desktop and every time i try to open my terminal xubuntu reboots. this is a fresh install not an upgrade and i cant find anyone else who has encountered this problem. If any one knows what is causing this any help would be appreciated.

---

### Post by jfinkels on 2007-05-06
[http://ubuntuforums.org/showthread.php?t=433345](http://ubuntuforums.org/showthread.php?t=433345)

[http://ubuntuforums.org/showthread.php?t=434239&page=2](http://ubuntuforums.org/showthread.php?t=434239&page=2)

There's two other people who have your problem. Seems to happen with Xubuntu Feisty :(

Try this: press alt+F2 to open the Run Application dialog, then type "xterm". See if that works.

---

### Post by ejohnston on 2007-05-07
thank you running it that way never produced a problem.

---

### Post by jfinkels on 2007-05-07
> **ejohnston said:**
> thank you running it that way never produced a problem.

I guess you'll just have to avoid using xfce4term, the default xubuntu terminal. Or file a bug if you're feeling adventurous.

---

### Post by andyviar on 2007-05-11
I had the same trouble with a fresh install of Xubuntu 7.04 and I solved it by downloading and using [aterm]("http://www.afterstep.org/aterm.php"). Good luck!

--Andy

---

### Post by KingArthur on 2007-05-12
I'm having the same problem.  I've tried a fresh install (after wiping the disk) from either the xubuntu 7.04 live CD or the Alt CD.  I'm installing onto a 533 mhz Celeron w/256 meg ram and 20 Gig HD.  I ran xubuntu 6.10 with no problems.  I'm currently using the xterm work-around.  I just wanted to add myself to the list of those suffering with this problem.

---

### Post by jfinkels on 2007-05-12
Somebody with this problem should DEFINITELY file a bug (if there isn't one already), especially if it is replicable by several other users!

---

### Post by ILYA99 on 2007-05-14
Suffering from the same problem.

Using xterm solves that.

---

### Post by mannantai on 2007-05-15
Hi, i saw there's a bug already reported on this and i found the solution to the problem in the bug report thread. 
[https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/91849](https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/91849)
You just need to find xorg.conf in etc/x11 and change colour depth from 24 to 16. That does the trick. :guitar: 
I have no idea why, though. :lolflag: 
Does anybody know exactly what colour depth is all about?

---

### Post by jfinkels on 2007-05-15
> **mannantai said:**
> Hi, i saw there's a bug already reported on this and i found the solution to the problem in the bug report thread. 
[https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/91849](https://bugs.launchpad.net/ubuntu/+source/xfce4-terminal/+bug/91849)
You just need to find xorg.conf in etc/x11 and change colour depth from 24 to 16. That does the trick. :guitar: 
I have no idea why, though. :lolflag: 
Does anybody know exactly what colour depth is all about?

[http://en.wikipedia.org/wiki/Color_depth](http://en.wikipedia.org/wiki/Color_depth)

You may notice a small decrease in the "range" (or, quite aptly, the "depth") of colors if you change your color depth from 24 to 16. 24 is "True Color" and 16 is just "High Color".

---

### Post by mannantai on 2007-05-15
Thanks. Do you know if there's a way to have 24 colours normally and 16 when terminal starts, or something like that? Or will i need to switch to another terminal?

---

### Post by jfinkels on 2007-05-15
> **mannantai said:**
> Thanks. Do you know if there's a way to have 24 colours normally and 16 when terminal starts, or something like that? Or will i need to switch to another terminal?

That might not be possible, because every time you edit the xorg.conf file, you must restart the X server (which means logging out of your current session). Here's something you can do to make your life a little easier: make xfce4term point to xterm
```

sudo mv /usr/bin/xfce4-terminal /usr/bin/xfce4-terminal.backup
sudo ln -s /usr/bin/xfce4-terminal /usr/bin/xterm

```
This will create a symbolic link from the command for xfce4-terminal to xterm. Not necessary, but just in case you accidentally click on something that opens the xfceterm.

Keep in mind that I'm using GNOME, not XFCE, so I don't really know if /usr/bin/xfce4-terminal is the actual name of the command to open the terminal. You should probably check on that before doing this...

---

