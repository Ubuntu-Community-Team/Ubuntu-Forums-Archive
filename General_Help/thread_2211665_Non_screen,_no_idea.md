---
title: "Non screen, no idea"
date: 2014-03-17
forum: General Help
---

### Post by GettingNowhere on 2014-03-17
I have 12.04 LTS on an HP computer with Radeon 880 graphics inbuilt.

I only have 1024x768 or 640x480 ever since I upgraded. I wanted it back to 1280 by whatever it is, and looking up the forums I loaded fglrx.  I went for experimental for some unknown reason, and have lost everything.  

The screen comes up "you're running in low graphics mode and a button for OK.
I press enter (there's no mouse)
and get a similar screen with options, none of which work  They just loop back to each other.

If I press escape I get vertical and horizontal blue lines and big redd blotches randomly around the screen.  Ctrl Alt F1 does nothing.  This is every time I boot there is no way out of it.

I have the 12.04 disk, but have no idea how to get into my hard drive or what to do when I get there.  The screen works using  the CD so I have the F1 to F6 options looking at me. I have to go next door to someone elses computer just to write this.

For God's sake there must be something I can do.

---

### Post by dragonfly41 on 2014-03-17
Some basic threads which might help you .. although note that I have no experience of fglrx drivers ...

[http://askubuntu.com/questions/78675/how-do-i-remove-the-fglrx-drivers-after-ive-installed-them-by-hand](http://askubuntu.com/questions/78675/how-do-i-remove-the-fglrx-drivers-after-ive-installed-them-by-hand)

[http://askubuntu.com/questions/190184/ubuntu-12-04-cannot-remove-fglrx](http://askubuntu.com/questions/190184/ubuntu-12-04-cannot-remove-fglrx)

---

### Post by GettingNowhere on 2014-03-17
How? I can't get a working screen.  The only reasonable thing I can do is "boot to disk" and then back to square 1.

I managed a root terminal without the disk and tried the suggested post, but every time I enter something, I get:

sh:O: Can't open /usr/share/ati/fglrz-uninstall.sh

If I try aptitude to uninstall, I get:

W:Not using locking for read only lock file /var/lib/dpkg/lock
E: unable to write to /var/cache/apt
E: The package lists or status file could not be opened

---

### Post by grahammechanical on 2014-03-17
May I make a suggestion? At the boot menu Select Recovery Mode. At the Recovery Menu select Resume. That will try to load to a desktop without loading the proprietary video driver. If you succeed in getting to a user interface you can use the Additional Drivers utility to change video drivers.

Regards.

---

### Post by GettingNowhere on 2014-03-17
And back to square 1

---

### Post by GettingNowhere on 2014-03-17
Come on guys, there's got to be something I can do.

---

### Post by deadflowr on 2014-03-17
Turn on your computer and leave it for a couple of minutes.

Come back and enter
crtl+alt+F1
You should get a login prompt in a fullscreen terminal-looking thing(console session)
Login like you would normally and,
then follow this
[http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Removing_Catalyst.2Ffglrx](http://wiki.cchtml.com/index.php/Ubuntu_Saucy_Installation_Guide#Removing_Catalyst.2Ffglrx)

---

### Post by GettingNowhere on 2014-03-17
I'm already on the root terminal, that's all I can get.

The link is just about the same as the previous one.  Same result.
sh:O: Can't open /usr/share/ati/fglrx-uninstall.sh

I tried sudo rm /var/lib/apt/lists/lock
and I get:
rm: cannot remove 'var/lib/lock' read only file system.

---

### Post by slooksterpsv on 2014-03-17
So it's a radeon HD 4250G chipset I'm assuming. 

Try to remove the xorg.conf file via sudo rm /etc/X11/xorg.conf  then restart the computer. If that doesn't work continue.

If you've removed fglrx try this, if you can get to a terminal prompt (either recovery or a tty before you get to any GUI interface) type the following:

sudo Xorg -configure && mv ./xorg.conf.new /etc/X11/xorg.conf

---

### Post by GettingNowhere on 2014-03-17
rm /etc/X11/xorg.conf
No such file or directory

Also it says in the recovery screen before I go to root prompt, that it's read only.  What use is that?

Obviously the only thing that will give me write privelidges is the CD, but how?

---

### Post by slooksterpsv on 2014-03-17
Read only will allow you to diagnose the problem before making any changes which could be destructive to the system. You will have to mount the system with rw privledges for my commands in the "continue" section to work via:

mount -o remount,rw /

---

### Post by deadflowr on 2014-03-17
> **GettingNowhere said:**
> I'm already on the root terminal, that's all I can get.

The link is just about the same as the previous one.  Same result.
sh:O: Can't open /usr/share/ati/fglrx-uninstall.sh

I tried sudo rm /var/lib/apt/lists/lock
and I get:
rm: cannot remove 'var/lib/lock' read only file system.

The root session in recovery mode is as it says "Read-Only".
So you can go one of two ways, the easy way is to exit and reboot and do as I stated to do, or run
```
mount -o rw,remount /
```
which will remount the system read/write.
Since you've not installed the drivers from amd, the first command
 /usr/share/ati/fglrx-uninstall.sh
is not needed.
but the one to remove flgrx* is.
Then follow rest of the guide.

Edit: mount command ninja'd:D

---

### Post by GettingNowhere on 2014-03-17
If I try and use the CD, I can get the full ubuntu screen, but I can't get superuser privelidges to do anything with it.

The neighbour is going to go to bed soon, so I can't use his computer any more.

WHAT DO I DO!!!!!!!!

---

### Post by GettingNowhere on 2014-03-17
Sorry about the previous panic post.
Rushing to and from houses, in between one tends to forget little things, like the instructions given.

I managed to get my computer working with the CD and get into Firefox and a terminal.
Then went to [http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd#.UyddTJjRHFI](http://howtoubuntu.org/how-to-repair-restore-reinstall-grub-2-with-a-ubuntu-live-cd#.UyddTJjRHFI)
Reinstalling Grub didn't work, but I now had the info needed to mount the drive.

sudo mount /dev/sda1 /mnt
sudo mount --bind /dev /mnt/dev && sudo mount --bind /dev/pts /mnt/dev/pts && sudo mount --bind /proc /mnt/proc && sudo mount --bind /sys /mnt/sys
sudo chroot /mnt

Then I could do what you suggested

mount -o remount,rw /
sudo apt-get remove --purge fglrx fglrx_* fglrx-amdcccle* fglrx-dev*

Now I've got my crummy screen back
The reason I started this adventure into the unknown is because Ubuntu seem to have removed the driver, leaving me with a screen that is only 1024x768 and it's "frazzling": thousands of tiny wavy lines going up the screen, giving me a headache after 10 minutes.
I just can't live with this. 

It is as Slooksterpsv theorised it is a Radeon HD 4200 RS880.
Is there no way forward with this chip?

Anyway, thanks very much for your help
Much appreciated.  The double glazing is still intact and the computer hasn't been through it, but it was close. (it would have been nearer the neighbours house...)

---

