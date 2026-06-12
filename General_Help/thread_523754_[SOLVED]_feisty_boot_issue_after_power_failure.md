---
title: "[SOLVED] feisty boot issue after power failure"
date: 2007-08-12
forum: General Help
---

### Post by jonathanmc on 2007-08-12
I've had feisty running fine for a while but I recently had a power outage while it was running.

Now it will not finish a normal boot and I am trying to work out why. With the default boot through grub selected it gets most of the way through the ubuntu splash screen with the progress bar 3 1/2 boxes from the end but then dosen't go any further even if left for an hour or so.

It boots into recovery mode or Win xp okay so I don't think it has damaged the hardware or boot drives. I've also seen it complete a scheduled fsck when booting into recovery.

I am still fairly new to linux and am not sure which log or startup scripts to look at.

I've looked at
[http://ubuntuforums.org/showthread.php?t=49925](http://ubuntuforums.org/showthread.php?t=49925)
[http://ubuntuforums.org/showthread.php?t=478225&highlight=bootlogd](http://ubuntuforums.org/showthread.php?t=478225&highlight=bootlogd) 

But I am currently feeling confused as to what next. 

My pc should be a fairly standard feisty install upgraded from edgy. With mythtv frontend/backend including mysql also running.

As the the myth backend would I guess be one of the few services/daemons running attached to active data files at the time of the outage. I am wondering whether removing this from startup somewhere will help?

I've tried ctrl f1 to see more than splash/progress bar but have not yet got it to to get away from the splash progress bar and show actual boot progress.

I've also tried removing quiet in grub
based on [https://answers.launchpad.net/ubuntu/+question/7197](https://answers.launchpad.net/ubuntu/+question/7197)
- you may edit the grub menu when you see it at the first beggining of a
  system startup process.
   Pressing 'e' will bring you into the edit mode of grub.
   select the line you want to edit with the <Up> and <Dn>Keys (The up and
    down arrow keys)
   press 'e' once more to edit the selected line.
   you may delete the options 'quiet' and / or 'splash' with the delete keys
   press <Esc> to leave the edit mode and
   press <b> to boot

With no difference so I must be doing something wrong.

Any help would be appreciated.

Thanks
jon

---

### Post by darksidedude on 2007-08-12
this happens a lot to me ( when I used freespire even more common) IMO you might have to re-write grub there is a cd for doing that, I think its called (super grub?) or something like that

---

### Post by jonathanmc on 2007-08-12
being new at this I am probably missing something, but given I can boot into recovery based on the grub menu.lst entry below, 
title		Ubuntu, kernel 2.6.20-16-generic
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0cc67fbf-9321-4e79-8113-5e120891a009 ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd2,0)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=0cc67fbf-9321-4e79-8113-5e120891a009 ro single
initrd		/boot/initrd.img-2.6.20-16-generic

but can't complete the boot of Ubuntu, kernel 2.6.20-16-generic, why do you think reinstalling Grub will help?

note choosing a normal (non recovery) older kernel version seems to stop at the same place.

I would have thought that for things to progress this far grub is working fine. ie it is a least getting past the mbr load from hdd
past the second boot loader stage
then it loads the kernel based on the configs above
This is based on what I read here
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch07_:_The_Linux_Boot_Process#The_Linux_Boot_Sequence](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch07_:_The_Linux_Boot_Process#The_Linux_Boot_Sequence)

Can  somone tell me what Im missing given darksidedude's suggested fix?

I'm still trying to find a way to work out what is the last succesful/1st unsuccessful process that's started

With the introduction of upstart I'm not sure the rest of that link above is as useful. ie from /sbin/init
perhaps someone could point me to a feisty doc that's equivalent to the above link as I haven't been able to find one yet.

Also does edgy/feisty have anything equivalent to chkconfig
[http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch07_:_The_Linux_Boot_Process#Using_chkconfig_to_Start_Daemons_at_Each_runlevel](http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch07_:_The_Linux_Boot_Process#Using_chkconfig_to_Start_Daemons_at_Each_runlevel)

Note: I'm not a fedora person it's just what google gave me to various searches

---

### Post by jonathanmc on 2007-08-13
Ok if I push Alt F1 it goes through various checks, then gets to a command line logon prompt and no further

However the seems to be no response to the keyboard at this point, (it worked at the grub menu and for Alt F1)

Can anyone give me any pointers as to which log to look at for this point in the boot process?

---

### Post by jonathanmc on 2007-08-13
Ok I managed to change the options in grub (removing quiet from the 1st and 3rd lines) and attempted to boot what was the normal or default boot process the last line shown is starting syslog.

I'm not sure what to try next.

Is it possible the syslog could be corrupt in some way and stop the daemon from starting?

---

### Post by jonathanmc on 2007-08-13
Ok 

> syslog from the recovery boot option has fixed it

So yes syslog can be corrupt and stop the daemon and therefore the system from booting normally
:)

---

