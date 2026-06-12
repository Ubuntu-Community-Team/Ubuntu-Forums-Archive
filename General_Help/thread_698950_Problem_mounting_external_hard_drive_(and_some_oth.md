---
title: "Problem mounting external hard drive (and some other problems unrelated to that)"
date: 2008-02-16
forum: General Help
---

### Post by Stoodle on 2008-02-16
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda9
UUID=f8911c5b-5ebf-4eae-938e-6ec00ccd2a66 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda3
UUID=98381371-8aae-4180-9112-87b1783aca8f /boot           ext3    defaults        0       2
# /dev/hda7
UUID=175c2e46-aabe-4fbf-a591-bf2cb73a278e /home           ext3    defaults        0       2
# /dev/hda1
UUID=3F51-2587  /media/hda1     vfat    defaults,utf8,umask=007,gid=46 0       1
# /dev/hda2
UUID=12B8A58AB8A56D43 /media/hda2     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hda6
UUID=99c43720-1986-4ffa-8bc9-5a20449d96d5 /usr            ext3    defaults        0       2
# /dev/hda8
UUID=a3edf542-acca-4056-9b2a-0b1d7d19b156 /var            ext3    defaults        0       2
# /dev/hda5
UUID=bc9755c8-b6b2-4b1a-8941-56c6897de281 none            swap    sw              0       0
/dev/cdrom        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0
/dev/sdc2 /media/iPod vfat
nosuid,noauto,nodev,rw,umask=077,gid=1000,user,defaults,noatime,iocharset=utf8 0 0
/dev/sda1 /media/Seagate\040Drive vfat auto rw,auto,user,sync umask=700 0 0

```

Okay. The problem is, I can't get my external hard drive to mount. I want it to mount automatically and I want read-write access. Also, I was thinking of changing the file system from vfat to ext3. Any suggestions?

The resolution looks really weird every time I log in, and it's from a time where I tried to change the resolution but it didn't happen because my monitor can't do it. The resolution is correct when I log in but not at the login screen.

Another problem is the fact that nothing appears on my desktop but the background. I can't click on it, can't see anything on it (though there are items in its folder). When I click on desktop from places, it takes me to the home directory instead. I don't like what I named the home directory. Is there anyway to change it (In terminal. I want to learn as much as I can for the terminal)?

Thanks in advance!

---

### Post by geo909 on 2008-02-17
Hi again!

Some comments (External viewers, please ignore this one!). The reason why "no one likes" multiple problems in one thread is, I think, organizing issues. Think about the answers you will get and your replies.. It will be a mess (you will see that in practice in this very thread!!!).
 Also, the thing about forums is the potential benefit of others who have the same problem with you. I must say I have solved the 60% of my ubuntu-related problems  by searching some keywords in this forum and see the stuff already said. You can't imagine how many problems are widely common! Anyway, I would recommend to post different threads for your unrelated problems.
 


OK  now, one at a time. Please answer the questions below, in order to have a clearer idea:

1) Have you changed anything in your xorg.conf in your etc/X11 file before you get to have problems in resolution or it was like that from the beginning? 

2) Can you tell me your graphics card and your monitor's brand, type and recommended resolution?

3)Go to System->Administration->Screen & Graphics and tell us what you have set in "monitor", "resolution", "Hz" under "Screen" tab and your graphic card and "drivers" under "Graphics Card" tab.

4)
> Another problem is the fact that nothing appears on my desktop but the background. I can't click on it, can't see anything on it (though there are items in its folder).

It seems like nautilus doesn't manage your desktop at all.. Have you ever executed a script or command that had to do with nautilus? Anything like "change default window manager" or something?

5)Are you sure your Seagate HD is not being mounted? Maybe it IS mounted but you're not getting anything on the desktop. Please try this again:
Make a backup copy of your fstab file.
Remove the lines below:
```
/dev/sdc2 /media/iPod vfat
nosuid,noauto,nodev,rw,umask=077,gid=1000,user,defaults,noatime,iocharset=utf8 0 0
/dev/sda1 /media/Seagate\040Drive vfat auto rw,auto,user,sync umask=700 0 0
```
Restart.
Plug in your Seagate HD.

If you are not getting anything, like a window pop up, please open a terminal and type:
```
mount
```
That will list your mounted devices. Give us the output.

6)As for the name of your home folder, it really looks to me you have a bunch of other important issues to take care of right now. I won't be surprised if you end up with a format..:(

---

### Post by Stoodle on 2008-02-17
Thanks for replying. I don't think that I modified xorg.conf (I'm still easing into messing with configuration files).

My monitor is a Compaq 7550 with a recommended resolution of 1024x768 at 87 Hz (what is that anyway?) I know I messed with its settings here but when the monitor couldn't handle it, it just reset it. The settings I gave it were wide-screen and a different resolution.
I removed those lines and saved it (though I didn't restart because I'm low on time and doing these things as I type) but I didn't get anything.

mount gives me this:
```

/dev/hda9 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw,noexec,nosuid,nodev)
/sys on /sys type sysfs (rw,noexec,nosuid,nodev)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
lrm on /lib/modules/2.6.22-14-generic/volatile type tmpfs (rw)
/dev/hda3 on /boot type ext3 (rw)
/dev/hda7 on /home type ext3 (rw)
/dev/hda1 on /media/hda1 type vfat (rw,utf8,umask=007,gid=46)
/dev/hda2 on /media/hda2 type fuseblk (rw,nosuid,nodev,noatime,allow_other,default_permissions,blksize=4096)
/dev/hda6 on /usr type ext3 (rw)
/dev/hda8 on /var type ext3 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)

```

---

### Post by geo909 on 2008-02-17
Well, from what i see your seagate is not mounted, indeed.
But do the same with the 'restart' thing. Maybe it will fix that. If not, restore your fstab like before, I don't know what else you should do. Have you tried to connect your HD while running XP? Does it work from there?


EDIT:[/B] If you have a seagate Freeagent drive you have to know there is an issue about them and Linux systems:
[http://hardware.slashdot.org/article.pl?sid=07/12/09/0651200]("http://hardware.slashdot.org/article.pl?sid=07/12/09/0651200")
Try to do this: Unplug the power of the drive, let it cool down for a couple of seconds and then plug it back in.
That worked for my freeagent drive.


Now, the resolution thing:
I assume that after messing up with xorg.conf, you have restored a previous backuped file, right?!  :shock:
Are there any settings of yours left in the currently used xorg.conf file?

From "System->Administration->Screen&Graphics" menu, play a little with the settings.
Under the "screen" tab, play a little with the "model" option.
Try for example "Plug 'n Play" or "LCD Panel 1024X768" and keep the MHz right (that is,up to 87MHz).

Though, you're not so specific. For example, you didn't mention your gr. card. See what graphics card you have and under "graphic card" tab on the same menu & choose an appropriate driver from the "driver" scroll down menu. 

 If you have the time, do answer questions 2,3 and 4 in detail.
[B]

---

### Post by geo909 on 2008-02-17
Sorry for pressing on that, but -believe me- you will more likely get answers to your questions if you post different threads like:

1)HELP! Can't set my resolution right!
2)SOS! My external USB HD can't be mounted automatically, whatever I do.
3)ALAS! My Desktop disappeared. No ~/Desktop folder. No response to  right clicks etc.

And most importantly:

4)PLZZZZ, someone help me change my home folder's name MANUALLY from Terminal!!

:):):)(Hope you don't mind teasing you a little!)

I'm not being weird, you WILL get your answers better if you do like this.

---

### Post by Stoodle on 2008-02-20
Well, my external hard drive is auto-mounting. Here's its line.
```

/dev/sda1 /media/Seagate vfat rw,auto,user, 0 0

```However, I'm still not getting read-write for some reason. That's about all. At least it's mounting. :)

I NEED rw access (really, what's the point of a hard drive otherwise?). A little off-topic, if music from my internal hard drive skips, does this indicate impending failure? I was thinking I might want to back it up onto this ext hard drive which I can't write on to.

When this gets solved, how to I mark it [SOLVED]. Also, how can I change the title of this thread?

---

