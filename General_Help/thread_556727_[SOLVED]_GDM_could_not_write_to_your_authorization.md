---
title: "[SOLVED] GDM could not write to your authorization file. This could mean that you are"
date: 2007-09-21
forum: General Help
---

### Post by mahasmb on 2007-09-21
> GDM could not write to your authorization file. This could mean that you are out of disk space or that your home directory could not be opened for writing. In any case, it is not possible to log in. Please contact your system administrator.

That is the horrible message I got when I tried to login yesterday.

I deleted upto a gigabyte in files, but df-h still said I was using 100% of my disk space even if it said my partition was composed of 79 GB, but only 75 GB of used space.

I then deleted more than 8 GB of space through my Windows XP partition ... and after rebooting, Windows read my Linux partition as a RAW partition. And it didn't solve my problem either.

Not until I ran ```
 rm -r /root/.Trash/*
``` did df -h start giving reasonable results (Size = 79 GB, Used = 55 GB, Avail = 20 GB,.. )

Now when I try to login in, I get this error:

> 
Your session only lasted less than 10 seconds. If you have not logged out yourself, this could mean that there is some installation problem or that you may be out of diskspace. Try logging in with one of the failsafe sessions to see if you can fix this problem.

View details (~/.xsession-errors file)



 log in ~/.xsession-errors :

> 
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "maha"
/etc/gdm/Xsession: Beginning session setup...
bash: /usr/share/reconstructor/scripts/boot-scripts-exec.sh: No such file or directory
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  2: IOR file '/tmp/gconfd-maha/lock/ior' not opened successfully, no gconfd located: No such file or directory)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  2: IOR file '/tmp/gconfd-maha/lock/ior' not opened successfully, no gconfd located: No such file or directory)
Cannot remove file /tmp/gconf-test-locking-file-TK7UYT: No such file or directory
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  2: IOR file '/tmp/gconfd-maha/lock/ior' not opened successfully, no gconfd located: No such file or directory)
GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://www.gnome.org/projects/gconf/](http://www.gnome.org/projects/gconf/) for information. (Details -  2: IOR file '/tmp/gconfd-maha/lock/ior' not opened successfully, no gconfd located: No such file or directory)

** ERROR **: Cannot find a safe socket path in '/tmp'
aborting...




Also, could it be possible that I have a corrupted hard drive?

---

### Post by Sef on 2007-09-21
> Also, could it be possible that I have a corrupted hard drive?

I would say that you removed your GDM.   

See if you can the screen type these two commands:

1) sudo aptitude update

2) sudo aptitude install ubuntu-desktop

---

### Post by mahasmb on 2007-09-21
I can't.

I connect to the internet using Wireless Assistant. I can't use Wireless Assistant without Gnome working.

---

### Post by dcstar on 2007-09-21
> **mahasmb said:**
> I can't.

I connect to the internet using Wireless Assistant. I can't use Wireless Assistant without Gnome working.

Manually create a new user account (using the text login if you have to), and you should be able to log into that.

Once in there, you can up the permissions on the new account to admin level, or just copy any missing files/directories from the new account to your original account (to replace any essential missing things that you may have inadvertently deleted) and then change the user permissions so the new account owns them.

It would be probably better to copy all of the files from your original home directory to a safe location, then delete and recreate that original account so all missing items are recreated, then copy the saved files back in.

---

### Post by mahasmb on 2007-09-22
I made a new user account with

> 
useradd user
passwd user



but I can't log onto it.

How would I add my Feisty installation DVD to my repos using the command line in order to re-install GDM??

---

### Post by dcstar on 2007-09-22
> **mahasmb said:**
> 
..........
How would I add my Feisty installation DVD to my repos using the command line in order to re-install GDM??

```
sudo nano /etc/apt/sources.list
```
and add in something like:

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Beta i386 (20070322.1)]/ feisty main restricted

(That is my install CD name - I don't know the name of your one)

---

### Post by mahasmb on 2007-09-22
Thanks.

So, I tried re-installing ubuntu-desktop from my install DVD's but it's still not working. Is there any other way?

---

### Post by nvteighen on 2007-09-22
Maybe you have lost permission of your .ICEAuthority file or home folder.

Do this:

1. When GDM appears or whatever it remains of it, press Ctrl+Alt+F1 and login.

2. Type:
```

chmod u+r -R *

```

3. To logout, type:
```

exit

```

4. Press Ctrl+Alt+F7. It should bring you GDM back; try to login.

---

### Post by mahasmb on 2007-09-23
Whenever I restart the Ubuntu, it always says

> /dev/hdc2 contains a file system with errors, check forced.

And then it says the following:

> 
/dev/hdc2: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY
                        (i.e., without -a or -p options)
fsck died with exit status 4

* An automatic file system check (fsck) of the root filesystem failed. A manual fsck must be performed, then the system restarted. The fsck should be performed in maintenance mode with the root filesystem mounted in read-only mode.
* The root filesystem is currently mounted in read-only mode.


This is followed by more mumbo-jumbo I'd rather not type out myself.

What's wrong this time?

I seem to be having one problem afer another and am more more than fed up at this point.

EDIT:

When I type: fsck /dev/hdc2

I get 

> 
Pass 3: Checking directory connectivity
Unconnected directory inode 1671905 (/tmp/???)
Connect to /lost+found<y>?


Please, please, please, what can I do?

---

### Post by petroskhan on 2007-09-24
I just started getting this problem today myself.  I am curious about something.  You said that you deleted some stuff through your Windows partition...how did you Windows to recognize the Ubuntu partition?  When I log into my Windows partition, it won't recognize the other half of my hard drive at all.  How do I get it to see the other partition?

---

### Post by nabaashraf on 2007-09-24
Hello all (I need help)
we are using a ldap server version 3 in debian sarge server
and knoppix client .all user profile (home folder) are stored in a single server and  home directory automatically mounted using nfs and autofs and it working fine without any problems.Now we updated our client pc operating system into kubuntu and retained old ldap server and home folder mounted using /etc/fstab.after some time ldap server process (slapd) consumes 99.9% cpu and server crashed with a kernel panic error
Please info any information regarding this problem

---

### Post by mahasmb on 2007-09-24
Hi, please create a new thread for your problem. It is completely unrelated to mine.

---

### Post by mahasmb on 2007-09-24
> **petroskhan said:**
> I just started getting this problem today myself.  I am curious about something.  You said that you deleted some stuff through your Windows partition...how did you Windows to recognize the Ubuntu partition?  When I log into my Windows partition, it won't recognize the other half of my hard drive at all.  How do I get it to see the other partition?

I downloaded a little program that allows Windows to see Ext2/Ext3 file systems: You can download it here

[http://www.fs-driver.org/download.html](http://www.fs-driver.org/download.html)

Edit: If you're having the same problem, do you have any idea what caused it? I've no clue.

---

### Post by mahasmb on 2007-09-24
I've tried

> 

sudo dpkg-reconfigure gdm
sudo dpkg-reconfigure xserver-xorg
sudo dpkg-reconfigure -phigh xserver-xorg

but they all give responses similar to the following:

> 
The program 'dpkg-reconfigure' is currently not installed. You can install it by typing: apt-get install debconf
bash: dpkg-reconfigure: command not found.
 But that's useless especially considering I don't have internet setup.

I've also tried 

> sudo /etc/init.d/gdm restart

but it also gives me an error message.

As per someone else's suggestions, I've also deleted the two folders under /tmp . I'm thinking that may have been a mistake though.

Any other suggestions out there? Any words of insight? Any help whatsoever?

---

### Post by petroskhan on 2007-09-24
I have NO idea what caused it, but I can tell what was going on when it did happen.

I had started to make a DVD, using ManDVD, which returned some errors, so I tried to close the program, right after I had tried to start Rythmbox, which would not start, again for no reason I could figure out.  At this time, my wife asked me to check some pictures from her camera's SD card.  When I inserted the card, the system did nothing, when it would usually pop up the folder for me to view.  I had noticed in the past that ManDVD was sort of pig when it came to system resources, so I thought maybe it was just bogging things down.  I tried again to close it, but no luck.  At this point, I even tried Ctrl-Alt-Bkspc, but even that didn't work, so I held down the power button till the system shut off.  Once back on, I had the GDM problem.  Don't know if all this babbling will help solve the problem, but maybe some one will get an idea of how to solve it...I hope.  Please?  I really to get back to Ubuntu.  'Specially since all my music and a few movies are over there.  Oh, and Windows blows.  I miss my Buntu, some one please help!!

---

### Post by petroskhan on 2007-09-24
Update.

I just used the program above, to access my Ubuntu partition from windows.  It showed me that I had 0 bytes free on the Linux drive, so I deleted the files in the directory where I was working, and recovered 2.5 GB of drive space.  On restart, the system said that the drive had some errors, and a check was being forced.  After the check, I was able to log into my Ubuntu side without trouble.  I wonder if somehow forcing the system to check would have solved my problem before, but everything seems fine now.  I am installing some updates, and will restart the system a couple of times to make sure everything is ok.  More on this story as it develops.

By the way, thanks a LOT for the help.  I do appreciate it.

---

### Post by mahasmb on 2007-09-25
That's awesome.

It's too bad my problem wasn't that easy to solve...

Question:

For the Alternate Install CD of Feisty Fawn, what does the "Rescue a broken system" choice do?

Edit:

[B]
NEVERMIND! I DON'T KNOW EXACTLY HOW IT WAS FIXED, BUT I WAS FINALLY ABLE TO BOOT INTO GNOME! HOORAY!
[/B]

What a horrid few days. Breaking my system without knowing how, but apparently a simple "fsck -y" even after the system's forced fsck check of it's own after booting into the recovery mode of Ubuntu solved it.

---

### Post by t-timmy on 2007-10-16
> **nvteighen said:**
> Maybe you have lost permission of your .ICEAuthority file or home folder.

Do this:

1. When GDM appears or whatever it remains of it, press Ctrl+Alt+F1 and login.

2. Type:
```

chmod u+r -R *

```

3. To logout, type:
```

exit

```

4. Press Ctrl+Alt+F7. It should bring you GDM back; try to login.

I encountered the same message as the starter of this thread has, and used the Ctrl-Alt-1 trick to log on into console.
The problem was that the Ubuntu partition got completely full. Since there was no warning about that, I never noticed. I used the console to free up some space.
I am completely new to Ubuntu, so I don't know where I should suggest this, but my suggestion is to alert the user when the disk becomes so full, or at least save some room to enable logons!
Most home users won't know how to use console...

Thanks and sorry if this was the wrong place to post this (I wanted to use Launchpad's bug reporting, but this isn't really a bug, is it?).

---

### Post by bl8n8r on 2007-11-27
I ran into the same problem today.  the perms on /tmp somehow got changed to 0755.  Setting them to 1777 remedied the login issue.

---

