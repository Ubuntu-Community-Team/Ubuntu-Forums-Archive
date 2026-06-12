---
title: "[SOLVED] How to totally disable suspend/hibernation?"
date: 2008-05-31
forum: General Help
---

### Post by Triple_X on 2008-05-31
Hello all.

I have tried numerous advice on how to disable my system from hibernating.
Please see my post here: [http://ubuntuforums.org/showthread.php?t=813975]("http://ubuntuforums.org/showthread.php?t=813975")

Any ideas would be appreciated!

Thank you.

---

### Post by eldragon on 2008-05-31
what makes your system hibernate in the first place?

ive got my computer up 24/7, doesnt suspend / hibernate unless i tell it to.

---

### Post by Triple_X on 2008-05-31
> **eldragon said:**
> what makes your system hibernate in the first place?

ive got my computer up 24/7, doesnt suspend / hibernate unless i tell it to.

That is a great question, unfortunately I am unable to answer it.
I have all hibernation and suspend options turned off (that I am aware of). And of course, this only happens on Ubuntu (it does not happen in Windows).

---

### Post by ladr0n on 2008-05-31
Could you give us a little more information about the problem?  How often does your system suspend or hibernate?  Does it do this after a specific period of time, or just randomly?  Tell us anything you think might be related to the problem.

---

### Post by Triple_X on 2008-05-31
> **ladr0n said:**
> Could you give us a little more information about the problem?  How often does your system suspend or hibernate?  Does it do this after a specific period of time, or just randomly?  Tell us anything you think might be related to the problem.


It happens approximately 15 or 20 mins from the last I touch the system. It is a timed instance happening, just like hibernate was turned on somewhere else. Each and every time.

---

### Post by eldragon on 2008-06-01
check bios settings for power saving features. that could be it.

---

### Post by sdennie on 2008-06-01
If it's not a BIOS issue, it may be as simple as hitting Alt-F2, typing gconf-editor and then going to /apps/gnome-power-manager/general and unchecking can_hibernate.  I've not tried this but, that should tell the whole gnome power management system that your machine isn't able to hibernate.  If not, something around that area in gconf-editor might help you.

---

### Post by Triple_X on 2008-06-01
Thanks for both of your replies.

1. I have already looked into the BIOS settings, and disabled power management.
2. From my previous post, someone had me go into gconf-editor aqnd uncheck those settings.

:(

Any other ideas out there please?

Thanks again.

---

### Post by bingoUV on 2008-06-01
I am not sure what exactly Ubuntu uses for suspend/hibernate, but in Add/Remove Programs, search for something like pm-utils, or power-manager etc. Try removing it. If it removes extra packages as a dependency, make sure they are not necessary packages or post the names of those packages here so someone here can advise. 

This will remove the ability to suspend/hibernate totally.

---

### Post by sdennie on 2008-06-01
Removing pm-utils will remove a bunch of stuff that you may not want to remove.  If the problem is with pm-utils, a VERY dirty hack (DO NOT DO THIS!) would be to make pm-is-supported not executable (which will make pm-utils stuff stop working):

```

sudo chmod -x `which pm-is-supported`

```

I tried this in a VM and, afterwards, I wasn't able to suspend or hibernate the VM.

---

### Post by Triple_X on 2008-06-01
> **vor said:**
> Removing pm-utils will remove a bunch of stuff that you may not want to remove.  If the problem is with pm-utils, a VERY dirty hack (DO NOT DO THIS!) would be to make pm-is-supported not executable (which will make pm-utils stuff stop working):

```

sudo chmod -x `which pm-is-supported`

```

I tried this in a VM and, afterwards, I wasn't able to suspend or hibernate the VM.


Ok, so you do not want me to do that, correct? :)
Any other ideas? I am pretty stumped and annoyed right now. I have to shut my system completely off when I am going to walk away for 15 minutes....quite a pain. haha

---

### Post by sdennie on 2008-06-01
The "DO NOT DO THIS!" part was in jest actually.  I was hoping that someone else would see this thread and post a more elegant solution but apparently they haven't.  Using the sudo chmod command I posted might work and, is easily reversible by running the same command with "+x" instead of "-x".

---

### Post by Triple_X on 2008-06-01
> **vor said:**
> The "DO NOT DO THIS!" part was in jest actually.  I was hoping that someone else would see this thread and post a more elegant solution but apparently they haven't.  Using the sudo chmod command I posted might work and, is easily reversible by running the same command with "+x" instead of "-x".

gotcha..and thanks.
I just tried this, and will report back my findings!

---

### Post by Triple_X on 2008-06-01
no go on that one either.

any other ideas? =D

---

### Post by BlueSkyNIS on 2008-06-01
> **eldragon said:**
> check bios settings for power saving features. that could be it.

Double check that!

Also, maybe something in your PC is dying? 
Could you post your PC configuration, just out of a curiosity? 

This is a very strange problem :confused: I'm also confused why none of the given answers didn't work for you...?

---

### Post by Triple_X on 2008-06-01
> **BlueSkyNIS said:**
> Double check that!

Also, maybe something in your PC is dying? 
Could you post your PC configuration, just out of a curiosity? 

This is a very strange problem :confused: I'm also confused why none of the given answers didn't work for you...?


Sure, I will double-check the BIOS.
Also, what configuration do you need? Do you need me to run a command of some sort, or just type out my basics?

I am running Hardy (latest with all updates) on a Dell Optiplex GX630.
P4D 3.2GhZ, 4GB RAM, ATI Radeon x1950PRO 256MB, 80GB HDD.
/ = 10GB
/home = 65GB
/swap = 5GB

---

### Post by sdennie on 2008-06-01
That really does sound like a BIOS problem if even horrible software hacks aren't working.  As far as I know, changing pm-is-supported to not be executable should prevent any software means of suspend/hibernate.

---

### Post by Triple_X on 2008-06-01
> **vor said:**
> That really does sound like a BIOS problem if even horrible software hacks aren't working.  As far as I know, changing pm-is-supported to not be executable should prevent any software means of suspend/hibernate.

I checked and double-checked...and nothing is in the BIOS to make this happen. Only thing I can do, is change from S3 to S1, which I tried and get the same results.
My machine did not hibernate ever (had it turned off in Power Options) under Windows XP....since the switch to Ubuntu about 2 weeks ago, it has done it since. So it is indeed an OS issue.

---

### Post by roachk71 on 2008-06-01
You may have to edit /etc/default/acpi-support, editing the following lines (as root, using **gksu gedit /etc/default/acpi-support** or **kdesu kate /etc/default/acpi-support**):
```
ACPI_SLEEP=false
```and
```
ACPI_HIBERNATE=false
```After a reboot, these should completely disable hibernation and suspend. Alternatively, they could be simply commented out with a pound sign (#).

---

### Post by sdennie on 2008-06-01
That's a perfectly reasonable reply roachk71, but, I don't think those settings do anything in Hardy.  At the moment, Hardy power savings stuff is absolutely allover the place.

---

### Post by werries on 2008-06-01
um. has anyone suggested the simple simple solution of going to System > Preferences > Power management and checking the AC and Battery power tabs? (assuming laptop). setting as never put to sleep.

---

### Post by sdennie on 2008-06-02
werries: That's far too easy of a solution.  All good replies must come in the form of doing cryptic and potentially system damaging things.  ;)

---

### Post by werries on 2008-06-02
ahahahaha. aren't you supposed to start with simple solutions first? or is that just forbidden in linux editing? =P
although, cryptic and potentially system damaging is so much more fun.

---

### Post by sdennie on 2008-06-02
Hehe.  Simple is always good but, it sounds like the OP has done his homework and has tried every reasonable solution.  At the moment I'm thinking that doing a chmod -w on the /proc devices that allow for suspend/hibernate might fix the problem but, 1) I don't know if that's possible. 2) I don't remember the device names 3) I have no idea why that would be needed.

---

### Post by Triple_X on 2008-06-02
> **vor said:**
> Hehe.  Simple is always good but, it sounds like the OP has done his homework and has tried every reasonable solution.  At the moment I'm thinking that doing a chmod -w on the /proc devices that allow for suspend/hibernate might fix the problem but, 1) I don't know if that's possible. 2) I don't remember the device names 3) I have no idea why that would be needed.


Yes, you are correct...I had already disabled that one (Power management under System Preferences). That was the first thing I tried before posting on here.

Thanks all for the replies. Hoping for some more activity on things to try, help please!


Thanks.

---

### Post by bingoUV on 2008-06-02
vor, what worst could happen if you chmod -x /usr/sbin/pm-hibernate as well as /usr/sbin/pm-suspend? In my limited imagination, a crash at the worst. As we use a well-journalled filesystem data loss would be minimal. What am I missing?

EDIT : This will make us aware in a short time that whether Ubuntu is requesting the hardware to go into sleep, or is the hardware/firmware/BIOS is going to sleep on its own free will.

---

### Post by Pjotr123 on 2008-06-02
Disable hibernate/suspend easily and safely:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 4)

Greetz, Pjotr.

---

### Post by Triple_X on 2008-06-02
> **bingoUV said:**
> vor, what worst could happen if you chmod -x /usr/sbin/pm-hibernate as well as /usr/sbin/pm-suspend? In my limited imagination, a crash at the worst. As we use a well-journalled filesystem data loss would be minimal. What am I missing?

EDIT : This will make us aware in a short time that whether Ubuntu is requesting the hardware to go into sleep, or is the hardware/firmware/BIOS is going to sleep on its own free will.

I am certainly up for giving this a try...pretty desperate right now. I will try this when I get home this afternoon from work, and will report back!

Thanks.

---

### Post by Triple_X on 2008-06-02
> **Pjotr123 said:**
> Disable hibernate/suspend easily and safely:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 4)

Greetz, Pjotr.

Hi and thanks for the reply.
I have already completed this with no luck. :-(

---

### Post by sdennie on 2008-06-02
> **bingoUV said:**
> vor, what worst could happen if you chmod -x /usr/sbin/pm-hibernate as well as /usr/sbin/pm-suspend? In my limited imagination, a crash at the worst. As we use a well-journalled filesystem data loss would be minimal. What am I missing?

EDIT : This will make us aware in a short time that whether Ubuntu is requesting the hardware to go into sleep, or is the hardware/firmware/BIOS is going to sleep on its own free will.

In this case, no harm at all in trying this.  It's trivial to revert and I can't think of any reason why it would cause any sorts of crashes.

---

### Post by eldragon on 2008-06-03
how about homer's bird that drinks water solution?

just leave it hitting the spacebar! :D

cant thing of any solution, sorry :(

---

### Post by Triple_X on 2008-06-03
> **vor said:**
> In this case, no harm at all in trying this.  It's trivial to revert and I can't think of any reason why it would cause any sorts of crashes.

the chmod of those options did not work either. :-(



and lol @ the bird....if I had one, I would use it right about now!

---

### Post by sdennie on 2008-06-03
> **eldragon said:**
> how about homer's bird that drinks water solution?

just leave it hitting the spacebar! :D

cant thing of any solution, sorry :(

That's actually not as absurd as it sounds if the system is thinking it's idle when it's not.  Just generating random key events could fix the problem.  Maybe a script that does some acpi_fakekey every few minutes would do the trick.

---

### Post by eldragon on 2008-06-03
> **vor said:**
> That's actually not as absurd as it sounds if the system is thinking it's idle when it's not.  Just generating random key events could fix the problem.  Maybe a script that does some acpi_fakekey every few minutes would do the trick.

mhhh, a virtual bird :D

how about a cronjob writing to /dev/null? every 5 minutes? would that be enough?

---

### Post by sdennie on 2008-06-03
> **eldragon said:**
> mhhh, a virtual bird :D

how about a cronjob writing to /dev/null? every 5 minutes? would that be enough?

Probably not.  You'd have to generate the events in such a way that the BIOS thought they were user generated.  I *think* acpi_fakekey can do that.

---

### Post by bingoUV on 2008-06-03
Cool, so we know that Ubuntu did not send a request to the hardware to sleep, but it did so on its own free will. Since it only happens when you are in ubuntu and not in windows, something in Ubuntu kernel is disliked by your hardware. Could be something other than kernel, but more hopes on kernel.

Since we don't know the exact problem, attempts to solution will look like hit and trial.

To try different kernels without compiling, you have the following options : 
1. Downgrade kernel, to maybe multiple different previous versions.
2. Use kernel shipped with Ubuntu server edition (I hear it is differently compiled than the desktop versions)
3. Maybe debian's kernel debs will install on Ubuntu without trouble.

Installing additional kernel debs should be possible, and then you should get the choice in grub about which one to boot.

Does this happen when you are booted to the live CD of Ubuntu? If yes, try live CDs of other distributions (knoppix, suse, fedora come to mind). These also provide differently configured kernels so they could solve the problem. If they do, we will have to compare options used to compile those kernels and see what can be done in Ubuntu to mimic that behaviour.

Command line options to linux kernel might also help. But others might suggest these better than me.

---

### Post by spiderbatdad on 2008-06-03
Agree kernel boot paramters may be the solution.```
dmesg > dmesg.txt
```look through the file that writes in home directory for suggestions from the kernel, like: 'apic disabled by BIOS, try using lapic.'

---

### Post by Triple_X on 2008-06-03
Thanks for the replies!

I am certainly up for the "fakekey" scenario, whatever stops my machine from doing this when I walk away. The shutting down and booting up each time I come to my computer is starting to suck. 
Since I am indeed a newb to Linux, is there some tutorial on this fakekey option? Like what commands, etc to make?

As far as the Kernel option, I am down for that as well. I have seen numerous posts about using different Kernels, but they are above and beyond me. Can someone recommend a simple Kernel compiling instruction/tutorial? And I am I correct to assume, doing so will not affect my current system (layout, sound settings, etc)? I am VERY happy with my system and the setup, everything else is working flawlessly (from USB devices, network, my .WINE setup, sound, mic, etc.) aside from this hibernate/suspend issue.


Attached is the .txt of dmesg > dmesg.txt



Thanks a lot everyone!

---

### Post by eldragon on 2008-06-03
to use the acpi_fake key do the following
type
```

crontab -e

```
this will open your cron table with nano.

add the following line
```

5 * * * * /usr/bin/acpi_fakekey

```
hit ctrl-X and Y to save
from what i read, that should do the trick, there is not much documentation about fakekey.

good luck

---

### Post by Triple_X on 2008-06-03
> **eldragon said:**
> to use the acpi_fake key do the following
type
```

crontab -e

```
this will open your cron table with nano.

add the following line
```

5 * * * * /usr/bin/acpi_fakekey

```
hit ctrl-X and Y to save
from what i read, that should do the trick, there is not much documentation about fakekey.

good luck

Thanks for the recommendation. I tried this, and the cron job was a no go. System still shut down after non-use. :-(

---

### Post by bingoUV on 2008-06-03
> **Triple_X said:**
> 
As far as the Kernel option, I am down for that as well. I have seen numerous posts about using different Kernels, but they are above and beyond me. Can someone recommend a simple Kernel compiling instruction/tutorial? And I am I correct to assume, doing so will not affect my current system (layout, sound settings, etc)? I am VERY happy with my system and the setup, everything else is working flawlessly (from USB devices, network, my .WINE setup, sound, mic, etc.) aside from this hibernate/suspend issue.


You should not have to recompile the kernel to try some kernels. Just getting kernel debs from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) should do. Software installer might let you downgrade the kernel, not sure how to do this in Ubuntu.

Do you have the same problem in Ubuntu liveCD?

---

### Post by Triple_X on 2008-06-03
> **bingoUV said:**
> You should not have to recompile the kernel to try some kernels. Just getting kernel debs from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) should do. Software installer might let you downgrade the kernel, not sure how to do this in Ubuntu.

Do you have the same problem in Ubuntu liveCD?

Not sure yet, will try the Live CD out in a few first, and let ya know!

---

### Post by Dr.Ninethousand on 2008-06-03
Triple_X, this is off-topic, but I noticed you have 4GB RAM and 5GB swap..  with that much ram, you certainly don't need so much swap, or any swap at all for that matter..  (although I would still keep about 128 - 512MB for swap)


:popcorn:

---

### Post by Triple_X on 2008-06-03
> **Dr.Ninethousand said:**
> Triple_X, this is off-topic, but I noticed you have 4GB RAM and 5GB swap..  with that much ram, you certainly don't need so much swap, or any swap at all for that matter..  (although I would still keep about 128 - 512MB for swap)


:popcorn:

Oh really? I had ready that you need double swap of the amount of RAM. If this is the case, I certainly would love to regain that space....but that will be another thread I am sure. :-)

Now onto the current issue, I utilized my Live CD (the same CD used to install my current system) and left it up over an hour without it suspending or hibernating. I did not remove anything, or make any system changes except for moving the slider over to NEVER under Power Management.
So I guess this means it is a kernel issue?

---

### Post by bingoUV on 2008-06-03
Live CD most likely uses the same kernel as the installed version. So, the only difference would be kernel parameters. Someone here should be able to tell which parameters a live CD boots up with.

So you need not install different kernels from all over the world.

EDIT : wait! You must have updated the system after installation. The live CD will have the old version of kernel. You must try downgrading the kernel to the live CD version. Following should downgrade it.
```

sudo apt-get install linux-generic=2.6.24.16.18 linux-image-generic=2.6.24.16.18 linux-restricted-modules-generic=2.6.24.16.18

```

You can undo this by simple apt-get update.

---

### Post by Triple_X on 2008-06-03
> **bingoUV said:**
> Live CD most likely uses the same kernel as the installed version. So, the only difference would be kernel parameters. Someone here should be able to tell which parameters a live CD boots up with.

So you need not install different kernels from all over the world.

Gotcha, thanks a bunch.

I do have an interesting update.
My screensaver was set to come on after 10 minutes of inactivity. After the screen saver was on for 5 minutes, the system will hibernate/suspend.
I just set my screensaver down to 2 minutes. Sure enough, within 5 minutes after the screensaver my system hibernates.
So basicaly, it is not a hibernation based on a specific system time of inactivity, but 5 minutes after the screensaver is engaged.

So what kind of hibernation/suspend triggers related to the screensaver are there? What am I missing?

Thanks.

---

### Post by bingoUV on 2008-06-03
cool. Can't you disable the damned screensaver? Somewhere in System, Appearance etc?

---

### Post by Triple_X on 2008-06-03
> **bingoUV said:**
> cool. Can't you disable the damned screensaver? Somewhere in System, Appearance etc?

Nope, I looked...only able to set it up to 2 hours..lol

Unless there is some file somewhere to change? Not sure.

---

### Post by BlueSkyNIS on 2008-06-03
[QUOTE="Triple_X"]Nope, I looked...only able to set it up to 2 hours..lol

Unless there is some file somewhere to change? Not sure. [/QUOTE]

Have you tried unchecking "Activate screensaver when computer is idle" option?

---

### Post by Triple_X on 2008-06-03
> **BlueSkyNIS said:**
> Have you tried unchecking "Activate screensaver when computer is idle" option?

Actually yes...but...my system received an update since my last post (Kernel .18?) along with some other updates (ATI driver, headers, etc.). Since the update, my hibernate/suspend works! Well, my system is still set to NOT hibernate/suspend...but it does after so long, but it comes out of it when I move the mouse/keyboard now!

Thanks to all for your attempted help, it was much appreciated!

---

### Post by sdennie on 2008-06-03
I'm really happy that you managed to fix your problem however, I admit that I'm a little disappointed that the fix was as mundane as, "update-manager".  It would have been more entertaining if some of the insane things people have posted had actually worked.  ;)

---

### Post by Arthur Archnix on 2008-06-05
I tried to chime in a few times, but all the database work and I kept forgetting. Anyway, I don't know about all the fakeroot stuff, but what I'd do is just reboot into recovery mode. Walk away... see if it goes to standby. If you're still interested.

---

### Post by Triple_X on 2008-06-05
> **Arthur Archnix said:**
> I tried to chime in a few times, but all the database work and I kept forgetting. Anyway, I don't know about all the fakeroot stuff, but what I'd do is just reboot into recovery mode. Walk away... see if it goes to standby. If you're still interested.


Hi, and thanks for the info.
I really should un-mark this as solved, because it worked ONCE. Since then, my system has been shutting down. I was so disappointed and fed-up, I stopped posting about it..haha
On that note, how do I get the gnome power management options to reappear once removed from SYSTEM>PREFERENCES>SESSIONS?

And yes, I will definitely try the recovery mode, and see what it does.

EDIT: Went ahead and un-marked as solved. :-(




Thanks.

---

### Post by Triple_X on 2008-06-06
Tried recovery mode, still same results. :-(


Any other ideas?

---

### Post by Arthur Archnix on 2008-06-06
Yeah... you can rule out X and gnome. Sounds like kernel trouble. Try booting into recovery mode, but with various boot options, stuff like noapic, no lapic, irqpoll. 

Go here [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) and try the various kernel options. If you find one that works, you're home free.

There's quite a few there, to save time I'd skip the oldboot and ht ones until very last. Not likely to help.

---

### Post by Triple_X on 2008-06-06
> **Arthur Archnix said:**
> Yeah... you can rule out X and gnome. Sounds like kernel trouble. Try booting into recovery mode, but with various boot options, stuff like noapic, no lapic, irqpoll. 

Go here [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) and try the various kernel options. If you find one that works, you're home free.


Thank ya, will check that out.

---

### Post by Triple_X on 2008-06-06
> **Arthur Archnix said:**
> Yeah... you can rule out X and gnome. Sounds like kernel trouble. Try booting into recovery mode, but with various boot options, stuff like noapic, no lapic, irqpoll. 

Go here [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions) and try the various kernel options. If you find one that works, you're home free.

There's quite a few there, to save time I'd skip the oldboot and ht ones until very last. Not likely to help.


You sir are the man!
The noapm command did not do the trick, but added the noapic and it works like a charm! yay!

Thank you very much.

---

### Post by Arthur Archnix on 2008-06-06
Awesome. Enjoy your new 24 hour a day machine. :)

---

### Post by sdennie on 2008-06-06
Enjoy indeed.  I'm very glad you were able to get this fixed.

---

### Post by Triple_X on 2008-06-06
> **vor said:**
> Enjoy indeed.  I'm very glad you were able to get this fixed.

Yes, thanks a bunch to both of you.
Just installed my new 8800GTS 640MB video card without a hitch as well (aside from stupid Dell case limitations)!

---

### Post by menelaosbgr on 2012-02-25
Hey all,

Just wanted to share my own experience and the dirty evil hack I found to deal with it.
If anyone else needs a temporary solution I think it may work for them.

I set up ubuntu 10.04 on an IBM thinkcenter A50...(OK, that's what I had).

Anyway, I would come back to the lab every morning and find the computer in something like sleep but it would not wake up at all. As I had installed a raid array and had a share this was not good....it made all my work worthless.

I disabled everything in the bios, disabled acpi in the kernel options, disabled sleep in the power options within Ubuntu to no avail after losing a few days troubleshooting.
I even tried poking the monitor off and on and various such options.

At that point the following options were available that I knew of:
1) Install another linux distro (e.g. ubuntu server)
2) Install another OS e.g. Free NAS
3) if 1 and 2 failed build another pc using another motherboard.
4) Try updating the kernel...

However, being in a jam due to time pressure for other tasks I decided to try adding a cron script to write to a file every few minutes. Surprisingly the server is still up after 2 days and has stopped sleeping.

I suspect reading from a file every 20 minutes, or writing to dev/null may also stop the idle state.

Just my 2 cents about this very frustrating problem and a dirty hack which worked.
"Taking any old pc and calling it a server doesn't make it so" :).

Menelaos

---

### Post by overdrank on 2012-02-25
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

