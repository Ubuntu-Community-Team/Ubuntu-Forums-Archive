---
title: "Kubuntu login loop"
date: 2007-01-10
forum: General Help
---

### Post by wyth on 2007-01-10
I've recently put in a fresh install of Kubuntu Edgy.  Everything was working fine, I had it set up just right, very happy, and then when I tried to log in today, it'd spin a bit, and I'd get thrown back to the login screen.  I can't log in at all.

I *can* go in through recovery mode, start x as root, log out, and log back in under my name there.  But this won't do, it's in recovery mode.  

I ran apt-get clean, and had the same result.  I did a ctrl-alt-F2 at the login and tried to log in to the tty, but got a permission denied.

Now that confounds me; I could log in through recovery mode, with that user name and password, but can't through tty?  Is there a permission I need to fiddle with?

I'd like to be writing this in linux, but can't.  Hopefully, *you* can help me respond from my shmancy Kubuntu setup.

:neutral:

---

### Post by wyth on 2007-01-10
bump

---

### Post by wyth on 2007-01-10
Trying to keep this visible until I get a response.

---

### Post by kebes on 2007-01-10
What are the error messages when the login fails?

If you go Ctrl+Alt+F7 (or F8, or whichever one it is), do you see any kernel errors or x errors in the background?


Something else to try, when logged in recovery mode as root, go and delete the ICE lock files from your user directory:

cd /home/username
rm .ICEauthority*
rm .DCOPserver*
reboot


(Those files get recreated on a new succesful login, so deleting them should be safe. You can move them to tmp instead, if you prefer.)

---

### Post by wyth on 2007-01-10
Thanks Kebes.  I went ahead and did both.  There was no .DCOPserver* to rm, but I ditched the .ICEauthority*, and the login did change -- it locked up on a black screen with a mouse cursor in the middle.  

But this must have something to do with the error messages.  A ctrl-alt-F8 gets me this:

> Root filesystem is clean

There are differences between boot sector and its backup
Differences: (offset : original / backup)
	71:71/4e, 72:74/4f, 73:6f/20, 74:72/4e, 75:61/41, 76:67/4d, 77:65/45
	Not automatically fixing this.
/dev/hda2:  20198 files, 1697183/2259090 clusters
/dev/hda6: clean, 146939/665184 files, 967546/1321338 blocks (check in 3 months)


So there's something screwy with the boot sector.  I'm going to try replacing some backups I made.

Thanks again, and if you have any more ideas, I'm all virtual ears.

---

### Post by wyth on 2007-01-10
I made backups of my fstab and boot menus (out of habit) and replaced those; still the same login loop problem.  So it must be something else.

---

### Post by kebes on 2007-01-10
> **wyth said:**
> Thanks Kebes.  I went ahead and did both.  There was no .DCOPserver* to rm, but I ditched the .ICEauthority*, and the login did change -- it locked up on a black screen with a mouse cursor in the middle.  

But this must have something to do with the error messages.  A ctrl-alt-F8 gets me this:



So there's something screwy with the boot sector.  I'm going to try replacing some backups I made.

Thanks again, and if you have any more ideas, I'm all virtual ears.

If it's the booloader that's the problem, then you can try having grub reinstall itself to the master boot record. Boot into a LiveCD (might work in recovery console, too) and take a look at the file "/boot/grub/menu.lst". Make sure that it looks "normal".

You can then try reinstalling grub with the "grub-install" or "grub" commands. You can find a manual here:
[http://orgs.man.ac.uk/documentation/grub/grub_3.html](http://orgs.man.ac.uk/documentation/grub/grub_3.html)

Probably what you're going to want is:
grub-install /dev/hda

(be careful with this command... there is a difference between "hda" and "hda1" ... you probably want to install grub to the MBR of your first disk...)


This will overwrite your MBR with a new one (and presumably update the backup).

---

### Post by wyth on 2007-01-10
I was able to reinstall grub successfully, but still run into the same issue.  This has me baffled.  I wonder if I should try going in recovery mode, deleting my profile and re-creating it...

I need to take my beagles out, but am still open to suggestions, and I very much appreciate your help.

---

### Post by kebes on 2007-01-10
I'm happy to help, but unfortunatley I'm running out of ideas.

Note: Probably a reinstall would fix the problem. I know you don't want to reinstall because you had everything "just right" but note that if you make a backup of your "/home/username/" directory, you won't lose that much. Most configurations and settings (for desktop apps anyway) are stored in /home/ and so if you do a reinstall and copy your old /home/ into the new one, then all your settings will be back. (You'll still have to reinstall missing software, of course.)

That's why alot of people recommend having /home/ as a separate partition: so that they can reinstall the OS (or even switch to a whole new Linux distribution!) and the settings are still (mostly) there.



However if you're not yet willing to reinstall, then I would keep looking for errors. With grub reinstalled does the "There are differences..." error persist? Perhaps you should also look through the files stored in "/var/log/" and see if they have any hints. Maybe the syslog will list the specific events which caused the login process to fail.

Without an error message as a hint, it's hard to guess what might be going wrong.

---

### Post by Arisna on 2007-01-10
Any chance the permissions on the root filesystem or /bin got changed?  Unprivileged users need to be able to execute things in these directories for your system to work.  While in recovery mode, run the following:

```
ls -ld /
ls -ld /bin
```

The output of both should start with "drwxr-xr-x".  This means the owner (root) can do anything, while everyone else can read and execute.  If there are permission problems, I believe you can correct them by running `chmod 755 /' or `chmod 755 /bin'.  You also might want to check this for /usr/bin.

---

### Post by wyth on 2007-01-10
Well, I ended up not really getting anywhere -- literally and figuratively stuck in a loop.  I did, however, put my /home directory on a separate partition, had everything backed up, and it's only been a couple days anyway, so there's really very little to lose.  

Thanks again, fellas.

...reinstalling...

---

### Post by Finder91 on 2007-01-18
I too am having the same problem.  I installed 6.10 roughly 2 weeks ago and all went well.  I have been using daily without any issues.  A couple days ago, I started playing with Beryl.  Again, no issues.  Installed without a problem.  Out of the blue today, I get stuck in the login loop.  I really don't want to reinstall, however I am fairly inexperienced with Linux...Hoping to find a solution somehow.

Thanks

---

### Post by wyth on 2007-01-18
I know that some tweaks mess around with just how the desktop is brought up, which is where I think I ran into my problem.  Most likely, Beryl is doing some similar tweaking in order to make it work.  And most likely, if you had any updates (as was the case with me), this messed with the tweaks I had made, which I assumed were safe.  After all, I read all 12 pages on the tweaks, no nothing like a login loop was reported.  However, this is Edgy, and it's not meant to be rock-solid.  If you want a more solid Edgy, you'll most likely need to reinstall and just leave those tweaks alone for now.  Wait till Feisty Fawn and see if any standard support for Beryl comes included in the default installation.

---

### Post by kebes on 2007-01-18
> **Finder91 said:**
> I too am having the same problem.  I installed 6.10 roughly 2 weeks ago and all went well.  I have been using daily without any issues.  A couple days ago, I started playing with Beryl.  Again, no issues.  Installed without a problem.  Out of the blue today, I get stuck in the login loop.  I really don't want to reinstall, however I am fairly inexperienced with Linux...Hoping to find a solution somehow.

You can try booting into a LiveCD (or get your system to boot to a commandline at least... while stuck at the login screen try going Ctrl+Alt+F2 ... try the various F-keys until you get to a place where you can enter a commandline environment) and try exactly undoing the changes you made during your Beryl install. wyth is right: you probably made a custom modification to a few files to enable Beryl to start when the desktop environment loads. Find the guide you used to make those changes, and undo them one at a time. See if your system comes back to normal status.

---

### Post by kword on 2007-01-20
I had the same problem.  Completed a fresh install of kubuntu 6.10, completed package updates, installed some available applications through Add/Rmove Programs, installed Automatix, installed many of the available applications through Automatix, re-booted and was in the login loop described earlier.

reinstalling...

---

### Post by ESPOiG on 2007-01-20
just wondering what version of kubuntu did you just upgrade from or what ever other distro sometimes the you can be using the same username and use the same /home dir from distro to distro and then the permissions dont match or something, anywho the point of it is i had to just change my permissions for a fc6 install over a ubuntu 6.10 just by using chown

eg sudo chown -R me: ~me

the first me being my user and the second being the home directory of that user

and then everything work fine for me :D, just worth a shot

---

### Post by CadetD on 2007-02-03
I'm having the same problem (Loops back to the login screen). 
Started after replacing ATI AIW 9600 with an ATI X1950 Pro

I tried modding the xorg.conf to the point of not being able to get KDM up at all. Then booted from CD and copied the xorg.conf form the live run to my machine to get back at the same point... looping. 

I can login using the session FAILSAFE but not KDE. 
I don't think its a video driver issue as in failsafe I can launch all apps, browse web, burn CD, etc... 

So how do I fix KDE? Any ideas?

---

### Post by wyth on 2007-02-03
Well, what I had to do was just re-install without adding any nice tweaks.  Not pleasant, but once I did, I haven't had any problems.  Now using edgy eft without any problems.

---

### Post by kebes on 2007-02-03
> **CadetD said:**
> Started after replacing ATI AIW 9600 with an ATI X1950 Pro

Since you've changed your video card, it's probably best to rebuild xorg.conf from scratch. Boot into recovery mode, and on a commandline run: "xorgconfig" (if that doesn't work, try "Xorg -configure" or "xorgcfg").

After building a new xorg.conf, you can then reinstall the ATI driver (or probably just update xorg.conf to use it, since it may already be installed...).

Edit: More info here:
[http://wiki.x.org/wiki/ConfigurationHelp](http://wiki.x.org/wiki/ConfigurationHelp)

---

### Post by prion on 2007-02-05
I just encountered this problem running Kubuntu 6.10 on a HP Pavilion notebook.  It was caused by a software update sometime in the past 10 days (my computer's been on for a while).  None of the solutions in this post solved my problem.  When I reinstalled Kubuntu and updated my system it reappeared.  I hope this helps someone diagnose and solve this issue.

---

