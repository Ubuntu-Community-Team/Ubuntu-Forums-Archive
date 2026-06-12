---
title: "HELP!  System will no longer boot"
date: 2007-01-26
forum: General Help
---

### Post by rbrugman on 2007-01-26
Hello fellow (K)Ubuntu users,
Today I encountered a very large problem - my system will no longer boot, even in rescue mode.  I was working on it today when it suddenly froze.  I used the power button to shut down and then tried to reboot.  I got the the Kubuntu blue splash screen where it loads everything, but then I got this message:

init: Unable to execute "//sbin/logd" for logd: Permission denied


That's all I get.  If I hit ctrl+alt+del I get the message that sulogin is respawning too fast.
If I try to boot into the rescue kernel it makes a bunch of weird shapes and never goes anywhere.  Is there ANY way I can fix my system?  I've spent so much time customizing it I'd hate to loose anything.

Thanks everyone!

Robert

---

### Post by llamakc on 2007-01-26
An upstart error maybe? There's a link here but I'm unable to read it:

[http://forum.ubuntu.pl/viewtopic.php?t=14524](http://forum.ubuntu.pl/viewtopic.php?t=14524)

Have you tried an alternate kernel?

---

### Post by rbrugman on 2007-01-26
The two kernels I've tried are the only two on the list.  That page has the same error, but I also cannot read it.  I'm also unfamiliar with booting from the LiveCD but I have one because I think thats how I'm going to have to fix it.

---

### Post by taurus on 2007-01-26
Boot with the LiveCD and run fsck of your harddrive to see if there is any problem with it.

Applications -> Accessories -> Terminal
```
sudo fsck -C /dev/hda1
(assuming /dev/hda1 is your Ubuntu partition.)
```

---

### Post by llamakc on 2007-01-26
This is another great reason to keep your /home/* on a separate partition, so that if the base system gets hosed from tinkering, a re-install would have you right back at the tinkering, instead of fretting about loss of data.

What was it you were last installing/working on? Are your disks large? No possibility of a filled /var/log?

---

### Post by rbrugman on 2007-01-26
/dev/hda1: clean, 178697/4702208 files, 1499038/9396009 blocks (check in 2 mounts)


I think that means it's ok.  The system is an IBM Thinkpad R51 with a 40GB drive.  The last thing I was doing was chatting on gaim and downloading a tar file off my server.  When it froze I could still hear the gaim sounds but couldn't click anything, so I powered it down.

---

### Post by llamakc on 2007-01-26
Here's what my logd looks like:

 ls -l /sbin/logd
-rwxr-xr-x 1 root root 26624 2006-10-10 05:42 /sbin/logd

---

### Post by llamakc on 2007-01-26
> **rbrugman said:**
> /dev/hda1: clean, 178697/4702208 files, 1499038/9396009 blocks (check in 2 mounts)


I think that means it's ok.  The system is an IBM Thinkpad R51 with a 40GB drive.  The last thing I was doing was chatting on gaim and downloading a tar file off my server.  When it froze I could still hear the gaim sounds but couldn't click anything, so I powered it down.

If you have the LiveCD running, open a terminal and type:

mount /dev/hda1 /mnt

df -h

and cut-n-paste the line from the output of `df -h` 

This depends on whether or not /dev/hda1 houses /

---

### Post by rbrugman on 2007-01-26
/dev/hda1    36G   5.2G   29G   16% /mnt

I know that hda1 houses /  hda5 is the swap and those are the only two that were in my fstab before.

---

### Post by taurus on 2007-01-26
```
ls -la /mnt/sbin/logd
```

---

### Post by rbrugman on 2007-01-26
-rw-----------  1 ubuntu  ubuntu  23401 2007-01-26 00:57 /mnt/sbin/logd


That would explain the permission issue?

---

### Post by taurus on 2007-01-26
```
sudo chmod 755 /mnt/sbin/logd
sudo umount /dev/hda1
```
Reboot and see what happens.

---

### Post by rbrugman on 2007-01-26
Got a much lengthier error this time.  Here it goes:

: not found :1: /*******************************************
//sbin/logd: 2: Coolmenus: not found
//sbin/logd: 3: Last: not found
: not fond: 4:
//sbin/logd: 5: v4.06: not found
: not found: 6: *******************************************
//sbin/logd: 7: /*Browsercheck: not found
//sbin/logd: 8: Syntax error: "(" unexpected

ctrl+alt+del still causes sulogin to respawn too fast

---

### Post by taurus on 2007-01-26
What if you copy /sbin/logd from the LiveCD to your harddrive, /dev/hda1?

```
sudo mount -t ext3 /dev/hda1 /mnt
sudo mv /mnt/sbin/logd /mnt/sbin/logd.bak
sudo cp /sbin/logd /mnt/sbin/logd
sudo umount /dev/hda1
```
Reboot and see what happens again.

---

### Post by rbrugman on 2007-01-26
The live cd doesn't contain logd.  When I type the third command I get:

cp: cannot start '/sbin/logd': No such file or directory

---

### Post by llamakc on 2007-01-26
Are you on Edgy?

---

### Post by rbrugman on 2007-01-26
Yeah, edgy on the laptop and using the edgy install/live cd.

---

### Post by rbrugman on 2007-01-27
Anyone else have an idea?  Is there any way to install logd from the livecd?

---

### Post by rbrugman on 2007-01-27
I've found out something interesting.  The livecd has klogd.  My server, which runs Dapper also uses klogd.  Why would my laptop not be using the same as the livecd and my server?

---

### Post by llamakc on 2007-01-27
ken@llamakc 12:57:14:~$ ls -l /sbin/klogd
-rwxr-xr-x 1 root root 22988 2006-10-06 08:46 /sbin/klogd
[1]+  Done                    conky -b
ken@llamakc 01:11:46:~$ ls -l /sbin/logd
-rwxr-xr-x 1 root root 26624 2006-10-10 05:42 /sbin/logd

I have both (on a recent Dapper reinstall from scratch).

---

### Post by rbrugman on 2007-01-27
Well my first problem was that I was using a Dapper cd instead of an Edgy one.  Whoops.  I'm now using an edgy cd and deleted both klogd and logd off my hdd partion and copied the ones off the cd.  Lets hope it boots now.

Edit:  no such luck.  Still won't start up and this time it doesn't even give me an error.  I get a bank cursor after a couple seconds.
Edit #2.  I did notice that before the recovery mode goes nuts into symbols it says something about running init-bottom scripts.  Could that have anything to do with it?

---

### Post by llamakc on 2007-01-27
Cool. Good luck. Let us know.

---

### Post by rbrugman on 2007-01-27
Nothing I've tried so far has worked, even copying the files off the live cd.  Is there any way to mount my hard drive as root and then reconfigure or reinstall all the packages used at boot?  I really would prefer not to reinstall again, but if I have to I will after pulling everything out of my home folder.  It seems to be my luck that every time I get my system fully customized with Beryl it just dies, even after not having installed anything.

If anyone knows how to rescue a system, please let me know.  I could use the help!

Robert

---

### Post by llamakc on 2007-01-27
> **rbrugman said:**
> Nothing I've tried so far has worked, even copying the files off the live cd.  Is there any way to mount my hard drive as root and then reconfigure or reinstall all the packages used at boot?  I really would prefer not to reinstall again, but if I have to I will after pulling everything out of my home folder.  It seems to be my luck that every time I get my system fully customized with Beryl it just dies, even after not having installed anything.

If anyone knows how to rescue a system, please let me know.  I could use the help!

Robert

You just said it. Move all of your /home/* files somewhere else. When you reinstall create a separate partition for /home so that these annoyances aren't so much of a deterrent in the future.

---

### Post by rbrugman on 2007-01-27
I hate to start over yet again, but I'm going to try and save myself the hassle of finding a solution to this problem.  How big of a /home partition do you recommend if my hard drive is 40GB?

---

### Post by rbrugman on 2007-01-27
Can anyone share the information on how to get my home folder mounted so I can back it up to my thumbdrive?  I'd like to try to get everything back up and running tonight, although its going to take me quite a long time to get everything as I had it.  I still wish there was a way to rescue my system.

Better yet.  Couldn't I somehow chroot to my hard drive, and reinstall upstart, the startup scripts, or the kernel or all of the above?  Something has to be possible I just dont know how to do it.

---

### Post by rbrugman on 2007-01-27
Would having /bin/bash messed up be causing my system not to work correctly?  When I try the following command with the LiveCD I get this error:

sudo chroot /mnt /bin/bash

/bin/bash: error while loading shared libraries: /lib/libncurses.so.5: invalid ELF header

Could this explain why the commands were not being executed by chance?

---

### Post by llamakc on 2007-01-27
I'd really like to know what it was you were doing before all of this started.

That said, just use the LiveCD and mount whatever partition your /home resides on. If you never made a separate partition, it will probably be the same as the the / partition.

something like:

sudo tar -cf /path/to/usbmount/oldhome.tar /mnt/hda1/home

should work, provided the paths are correct. When you're in the LiveCD what is the hard disk's designation?

---

### Post by llamakc on 2007-01-27
By the way, you may have to remount the usbstick for rw with something like:

sudo mount -o remount,rw /dev/sdaX

where /dev/sdaX represents your USB stick. This will let you write to it from the LiveCD (in case it does not by default). I had to do this tonight with KNOPPIX to save some old data.

---

### Post by rbrugman on 2007-01-27
Here's what I was doing.  I was at work, talking on AIM and downloading some mp3's in a tar file off my server at home.  I had ran apt-get update/dist-upgrade the same day to get the latest patches and things and it installed something but I can't remember what.  While chatting and downloading the file the system just froze.  I could hear the gaim sounds but the screen wouldnt change and I couldn't click anything.

I held the power button until it shut off and then turned it back on, and I got the permission denied error.


Anyway, when I mount /dev/hda1 to /mnt, home is not a directory. I can't cd to /mnt/home.  if I could see the files I could get them to my thumb drive but I don't think home is mounted or something.

---

### Post by rbrugman on 2007-01-28
I did ls -al on my /mnt/hda1.  Most of the folders are actually folders that I can access, but home is not one of them:

home -> libc-2.4.so

Why would home be linked elsewhere.  I also found out hda5 is my swap drive but this is all so confusing at this point I don't even know what to do anymore.

---

### Post by llamakc on 2007-01-28
Try mounting /dev/hda3 or /dev/hda2 and see i that is /home.

---

### Post by RayFward on 2007-02-24
I too have a spamed boot sequence  Upstart did it after a dist upgrade.
I was able to copy logd from the Boot install disk which got rid of the error cannot find logd.
The remaining error was  127 generated by init a quick look at boot messages on one of the other consoles showed unable to locate boot splash  file (Meaning of the message not the actual text).  No doubt there will be other messages.

I can't tell at this point if upstart is running the show or init is failing because the package manager removed something in favor of upstart.

Further information.
Upstart does look to have been running.  init:rc-default fails with error 127 on checking the output from init in rescue mode the failure occurs just after applying keys and font settings.
 
Regards
Ray

---

### Post by rutu on 2007-02-25
For the record I have the same error. I was having occasional crashes related to FF2.0. Not much else was running other than stock processes. The common event with the description above is restarting using the power button, perhaps hitting it twice.

---

