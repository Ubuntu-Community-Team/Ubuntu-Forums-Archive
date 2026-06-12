---
title: "Edit .profile with recovery/bootable USB"
date: 2020-10-22
forum: General Help
---

### Post by grxgghxrpxr on 2020-10-22
Hello everyone.

I'm new to Ubuntu and have been enjoying it but it hasn't been without its issues. I had to add a custom screen resolution due to it not being available out of the box. To stop me from doing this everytime, I had to add two command to the bottom of the .profile file. I must have copied the wrong commands or something because after restarting, the screen won't come up - just the Ubuntu password thing asking me to authenticate. I don't know how to revert these changes in recovery mode or with bootable media. Could somebody help me with this?

Also, could somebody pinpoint where I went wrong with this?
I left a space between the last part of .profile then entered the following 2 commands:
sudo xrandr --newmode ‘“1920x1080_60.00” 
173.00 1920 2048 2248 2576 1080 1083 1088 1120 -hsync 
+vsync
sudo xrandr –-addmode Virtual1
“1920x1080_60.00”

Is this correct?

Thank you 
Gregg

---

### Post by cd-site-manager on 2020-10-22
Hi,
well the .profile file gets executed only when you log in, so you basicly need to enter in your profile to get it executed.
I'm not sure what you are trying to do, but if you manage to get to your login screen, that mean you can get to your console mode to change it, just ctrl+alt+f3 to pass in console mode, from there you should be able to remove the faulty lines.
For the xrandr part, what graphics driver are you using (also graphics card) and what resolution does your monitor support ? and frequency ?

also can you add the code beacons around the lines you added, to be able to copy paste ?

---

### Post by grxgghxrpxr on 2020-10-22
Thank you.

I haven't installed any specific drivers, I'm just using Ubuntu on Virtualbox. I was trying to add my screen resolution which is 1920x1080 at 60 Hz. I followed this tutorial which has worked before but I must've done something wrong this time [http://ubuntuhandbook.org/index.php/2017/04/custom-screen-resolution-ubuntu-desktop/](http://ubuntuhandbook.org/index.php/2017/04/custom-screen-resolution-ubuntu-desktop/)

---

### Post by TheFu on 2020-10-22
Try ~/.xprofile instead for any post-GUI settings.

~/.profile is used for all logins, including those without a GUI. Actually, we would use ~/.bashrc most of the time, not ~/.profile which is normally used by Borne hell, but bash supports it too.

Also, you need to put commands onto a single line per command or tell the interpreter that you want to use multiple lines.

Don't use sudo. That will break things when unnecessary.

I wouldn't do what you want in this way, but, this seems to be what you really intend:
```
 /usr/bin/xrandr  --newmode &#8216;&#8220;1920x1080_60.00&#8221; 173.00 1920 2048 2248 2576 1080 1083 1088 1120 -hsync +vsync
 /usr/bin/xrandr  &#8211;-addmode Virtual1 &#8220;1920x1080_60.00&#8221;
```
Put those lines into ~/.xprofile.  I have no idea if the mode is correct or not.  I'd add those to a file in the  /etc/X11/xorg.conf.d directory myself. Probably named 10-custom-thefu.conf.  That name and a comment inside will help me to know to include the file in my backups and to restore the file later.

---

### Post by cd-site-manager on 2020-10-22
yep but the reason I asked you to put your lines into code beacons, is like @TheFu said, it should only on one line, so can you give us the EXACT lines that you put into your files ?
Also, in this case, did you check the VirtualBox monitor resolution options ?
Did you try the solution of @TheFu ?

---

### Post by TheFu on 2020-10-22
cd-site-manager asked for good info.

For a VM, we don't want a detailed modeline. I use exactly the following in my KVM virtual desktop:
$ more ~/.xprofile 

```
/usr/bin/xrandr  --output Virtual-1  --mode 1680x1050
```

I prefer not running full screen most of the time and the size works for my laptop when I'm remote. The "Virtual-1" output comes from the connection and can change depending on the connection method. I connect using a number of different tools, not just 1.

---

### Post by grxgghxrpxr on 2020-10-22
How can I access this in recovery mode or with bootable media?

---

### Post by grxgghxrpxr on 2020-10-22
I believe it was on 28 and 29. I haven't been able to access this since the issue started

---

### Post by TheFu on 2020-10-22
> **grxgghxrpxr said:**
> How can I access this in recovery mode or with bootable media?

Access what?

If you want to boot from bootable media in a virtual machine, connect the ISO file to the CDROM/DVD device, set the boot option to boot from the CD/DVD, then boot. Just like you would with a physical machine.  All VM hypervisors work the same way.  Do the same stuff you'd use on a physical setup, just in the virtual machine settings.

>  I believe it was on 28 and 29. I haven't been able to access this since the issue started 

I have no idea what this is supposed to mean.  We cannot read minds, sorry. "28 and 29" what? Lines? Reboot attempts?  After midnight?  I haven't any clue.

---

### Post by grxgghxrpxr on 2020-10-22
I believe the 2 commands I entered in the .profile Were on those 2 lines.

I don't know how to access gedit or .profile or .xprofile with recovery mode or bootable media.

---

### Post by TheFu on 2020-10-22
Use any editor you like.  That is a personal choice.  vim, nano, ted, are a few. You probably want **nano**. There must be 50 different editors, but without a GUI, the number drops to the text-only editors.

In recovery mode or using bootable media, you have to get the correct storage/partition/file system mounted somewhere, then determine the directory, then edit the file.  The file may not already exist, so you'll create it new as part of the editing.  I spent more time typing that than it would take to actually do it, once I knew the mounted location of the directory.

There are many things that Windows-trained people assume which don't apply for any other OS made. Unlearning that stuff is a challenge.

Sadly, Unix skills build on prior skills, so jumping into something is likely beyond current skills.  There's all sorts of knowledge necessary to accomplish this task that are not intuitively obvious.  Most people new to Linux should probably just do a fresh install. That's 10 minutes of time and you are done.  Then restore any files from your backups made before the problem started. If you still need to modify the ~/.xprofile, use **nano ~/.xprofile**. 

Running sudo with GUI commands can break things. Best to avoid it completely for now.

Learn basic Linux skills: [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php) 

In Unix, there isn't 1-way to accomplish things. There are usually 50, 500, 50,000 ways. Which one is best depends on things only you know.  I get that people want to know "what to type", but we can only say, "it depends on things we don't know."  If I assume the device name and get it wrong, bad things. Really bad things.  It can be frustrating for you, but it is also frustrating for us.

---

### Post by grxgghxrpxr on 2020-10-22
Thank you. I've ran nano ~/ .profile then nano ~/ .xprofile and they didn't open, but their contents weren't the same as when I was in the GUI,so I couldn't get rid of those 2 lines. Do I need to authenticate to get the full file or something?

I'm sorry for sounding really stupid, I've not been using Ubuntu for very long.

---

### Post by TheFu on 2020-10-22
It appears that you've added spaces.  
```
nano      ~/.xprofile
```
is the command (no spaces in the filename part), but it won't work unless you login to the normal install with your normal userid. I attempted to explain that above.  Unfortunately, I don't know how to explain how to get to the correct place to someone with extremely limited Linux skills in a forum. Sorry.

But if you look at that link with the book, perhaps after some reading it will become clear?

Maybe someone else can explain it?  IDK.

It is just a VM.  I'd blow it away and to a fresh install, then restore any necessary files from my last good backup. A fresh install is 10 minutes and restoring a few files shouldn't be over 30 min, tops.

---

