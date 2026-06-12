---
title: "what to do if you chmod/chown root recursively"
date: 2018-09-14
forum: General Help
---

### Post by nickajshelden on 2018-09-14
This is a very high-level guide, but I've seen multiple people do this over the years, and I don't think I've ever seen someone attempt to actually fix it. Well, I just made the mistake myself 2 days ago, and so I figured I'd actually fix it and write it up.
I notice that below in my instructions, I never tell you to use sudo. well, almost everything here has to be done as root, so log in as root when you can.  if you made it as far as needing to use this manual, then you already know why running things as root is dangerous.  Keep that in mind. Oh, and I claim no responsibility if you make things worse by doing this.  if you need further help, do comment, and I can maybe provide more specifice (like what I actually typed into the terminal).

Scenario:
                You ran chown or chmod on all files recursively from root.
Problem:
                Now only one user has control and all permissions are messed up.
Solution 1:
                Get a root shell as quick as possible (don&#8217;t reboot) and copy your home folder to another place and reinstall. You did back it up, right? And you put all your data in your home folder, preferably on another drive&#8230;.right?
                                Pros: fast and simple
                                Cons: You lose all system-level settings, any programs that were installed, any data you forgot to move.
Solution 2:
                You set the permissions on every file in the system.
                                Pros: system can be recovered exactly how it was before, and you learn a bunch of stuff about the linux/gnu environment you didn&#8217;t want to know.
                                Cons: this took me 30 hours (time, not attention), and I knew for the most part what I needed to do&#8230;
 
 
How to Solution 2:
                Please read this all the way though before attempting this.
First, you will need a root shell.  You probably already have one because you made a root-level mistake. If you did it as su/root, easy.  If you did it as sudo, things may be a bit more difficult. Hopefully recovery works for you if nothing else does.  If you aren&#8217;t able to access root (likely the sudoers file is broken at this point), then switch virtual terminal (ctrl+alt+F#) and log in as root (you know your root password, right?
First things to do BEFORE you reboot: copy your home folder off somewhere (hopefully USB still works until you reboot&#8230;.it may not afterwards. Then fix the permissions of the sudoers file. &#8220;chown root:root /etc/sudoers&#8221; Hopefully now sudo will work.
The longer you can go without rebooting, the better.  When you reboot, you will likely only be able to go to single user mode (recovery), and networking will most likely not work.
Now the real first steps of the solution:
                Let&#8217;s start with everything is owned by root.  Maybe you chowned everything as another user, so switch EVERYTHING to root. If it&#8217;s already root, you probably are fine. Home should belong to user 1000 (primary human user).  Remember this term, as I will likely use it a lot. &#8220;chown 1000:1000 /home &#8211;R&#8221; Open another terminal and check that you can sudo. If not, you could have trouble later on, but just try to log in as root on everything.
                Now we have a root user and a 1000 user. Theoretically you can log in as either. Most of the files are owned by root.  That should be fine for now.  The problem is some more files need to be owned by 1000, and then some need to be owned by other entities, notably &#8220;daemon&#8221;
                If you have internet at this step, try the following code:
for pkg in `dpkg --get-selections | awk '{print $1}' | egrep -v '(dpkg|apt|mysql|mythtv)'` ; do apt-get -y --allow-remove-essential install --reinstall $pkg ; done
                This can be placed in a sh script file, but you will likely want to explicitly say &#8220;\#\!/bin/bash&#8221; at the beginning. Also, most people use the --force-yes option, but this is depreciated, so I use the --allow-remove-essential option, which here get's the job done as we need.
                That code will reinstall every debian package on the system that it can find in the sources.  It will fail on everything that you installed manually.  This will take a very long time (my computer ran for about 16 hours).  It should pause half a dozen times or so at least to ask questions, so do check on your computer periodically. After that, most everything should be set correctly. Also, if you can live without them, here are some packages I&#8217;d recommend PURGING until your computer is fixed: mysql* (take it all, and if you have blender installed, this will remove it, dunno why), anything to do with vmware or virtualbox, apache*,chrome-remote-desktop.  Thing is, these create their own users and have complex setups.  It&#8217;s just so much simpler to deal with these on a healthy system.
                Once you have reinstalled everything, you should be very close to done.  Several programs may complain about not finding files. Now worries, run them from the terminal and change the permissions on the files as necessary.  Be aware that some programs make their own &#8220;users&#8221; and the files need to be owned by them, such as &#8220;mysql.&#8221; If you have any website or virtualization, this will be very likely.  Oh, and blender. What&#8217;s up, blender?
                Another category that will fail will be kernel modules, services, and daemons.  They will all fail for just about the same reason, but expressed different way.  To find out what failed, reboot and run &#8220;journalctl -b0 _PID=1 | grep Failed&#8221;
Kernel modules are the trickiest.  They likely cannot be just reinstalled.  Try to run each one (try in /etc/) and find what files the permissions are not set right for. You will need to &#8220;update-initramfs&#8221; at least once.
Services can be purged and reinstalled. Some of them need to still have separate files adjusted like kernels (I&#8217;m looking at you, Logical Volume manager and device mapper...which also brings us to daemons).
Daemons. Ah, this one took me a while to figure out (but not as long as it took me to figure out Nvidia). Daemons can usually be found in /etc/system.d/system and they need to have the right permissions on any links to /dev/null. Basically, find any file in there that is a link to null and remove it.  To check what a file is run &#8220;file /etc/system.d/&#8230;&#8230;../file_name&#8221; and if it says &#8220;&#8230; symbolic link to /dev/null&#8221; just delete it and run &#8220;systemctl daemon-reload&#8221; why? Well, glad you asked. Daemons can be in a few states.  We are all familiar with enabled and disabled, but they can be in other states, including masked.  Masked is like an aggressive way to disable it, by putting an appropriately-named link to null in the folder.  That way, the system will not even try to enable it, and it will fail, without much other warning&#8230;not good for us.  However, given the right conditions, the system will gladly unmask it (systemctl unmask daemon_name_or_service_name)&#8230;but it doesn&#8217;t have permissions.  You see, these links are supposed to owned by daemon:daemon&#8230;.but right now, the masking files exist, and are owned by root.  So delete the files and reload the daemons.
At this point, likely everything is mostly fixed.  Do run &#8220;dpkg &#8211;configure &#8211;a&#8221; to double check, and an update/upgrade is likely a good idea. Oh, and a backup.
Now, a note about nvidia.  Linus Torvalds gave them the finger a while back, and I heartily agree with that.  If you are running nvidia graphics, uninstall nvidia* LAST THING BEFORE FIRST REBOOT.  Don&#8217;t worry, Ubuntu will reinstall the proprietary drivers in due time given a good network connection after everything else is fixed. Oh, and if you have done any configurations, just delete them or save them off and delete them. The graphics are just gonna be hell if you had them optimized like I did, but now don&#8217;t have the right permissions for nvidia to run.
 
Random advice:
                You may like to keep your configuration of everything, but remember that it will probably be more work to set the permissions of each file right individually rather than just purge and reinstall and reconfigure most of them.  I&#8217;m looking at you, chrome-remote-desktop.
                Pulseaudio can cause trouble.  You can live with a silent computer, but just be aware that pulseaudio likes things just-so&#8230;.purge and reinstall.
                Chmod 0755 is your friend. This is quite useful for mysql and the services. Chmod +x or chmod +t are also frequently used.
                Keep an eye on networking, and try to use Ethernet.  You may have to rebuild the configuration for your Ethernet manually.  Just look for available devices (ifconfig &#8211;a) and duplicate the configuration for the loopback device, but with the name of your Ethernet controller. Hint: /etc/network/interfaces You will probably run into this after your first reboot.  And the service will probably not work.  Fix networking.service sooner rather than later. Also, ifyou do duplicate the entry in the interfaces file, undo that change after you have fixed the computer. Also, you may run into issues with the lock file (just delete it) once you are up and running. Then restart the network-manager service...otherwise the wired connection will be labeled as "unmanaged"
                First thing to do in recovery mode: mount &#8211; remount,rw /

---

### Post by oldfred on 2018-09-14
Best to have backups.

You can do a "dirty" install, or install without reformatting. That will still overwrite any system configuration files (most in /etc) that you may have changed like grub settings, network settings, fstab etc. It will also change installed apps to defaults, so you have to reinstall apps. Your data in /home should be ok. If still in system, you can export list of installed apps to make it easy to reinstall. I make that part of my standard backup.

       Over install without formatting to reuse same home data. "Dirty Install"
System settings or anything in / may be overwritten with defaults. Good backups still important
[https://help.ubuntu.com/community/UbuntuReinstallation](https://help.ubuntu.com/community/UbuntuReinstallation)
[http://ubuntuforums.org/showthread.php?t=1941872](http://ubuntuforums.org/showthread.php?t=1941872)

---

### Post by TheFu on 2018-09-14
>  it will probably be more work to set the permissions of each file right individually rather than just purge and reinstall and reconfigure most of them. 
Agreed.

Making backups isn't just about the data files.  It must include owner, group, permissions, links and any ACLs as well.  If you don't want to backup the files, you can still make a backup of the permissions using** find -ls** , but that just captures the data. It isn't in a format that is easily used programmatically.

---

### Post by nickajshelden on 2018-09-14
Oldfred, yep backups are the way, and I have them.  Some folks don't and really want to recover their system.  This guide is for those poor souls.

---

### Post by nickajshelden on 2018-09-14
> **TheFu said:**
> Agreed.

Making backups isn't just about the data files.  It must include owner, group, permissions, links and any ACLs as well.  If you don't want to backup the files, you can still make a backup of the permissions using** find -ls** , but that just captures the data. It isn't in a format that is easily used programmatically.

I typically backup using Terabyte Inc. Image4Linux.  That is a bit-for-bit image. it has everything.

---

