---
title: "Nvidia driver issue caused system to become unbootable...next steps?"
date: 2020-05-12
forum: General Help
---

### Post by goemonburo on 2020-05-12
This is not my first Linux rodeo but alas, Nvidia drivers have again bested me and I need some help.  I have an older Dell Studio XPS 8100 and installed an Nvidia GeForce GT 1030 card, which required newer Nvidia 440 drivers.  I used "ubuntu-drivers devices" to confirm that was what was needed, and then "ubuntu-drivers autoinstall" to install them.  Things seemed to go well and then the system just hung.  Eventually, after getting a cup of coffee and then going off to the store, I downed a stiff one and turned off the computer.  

When it turned on again, instead of a dark blue security screen for the entering of the decryption password, I saw a light blue screen with "Lubuntu 18.04LTS" in very old, unaliased lettering.  Like DOS used to look.  Four dots that progressively indicated "loading" but it boots only to a "BusyBox v1.27.2 built in shell" and the "initramfs" prompt.

BUT MY KEYBOARD WON'T WORK.  

In the past I've typed "exit" and gotten somewhere or run fsck if needed...no errors are showing, but the keyboard doesn't work.

Am I best off running Ubuntu from a boot disk or boot usb?  If so, how do I go about repairing what's been effed up?  

Thank you so much.  I really appreciate any advance help -- I am using someone else's computer so it's hard to do extended searching (and libraries are closed due to Covid!).  If you know what I should do to reclaim my system please take a moment and share your expertise.  THANK YOU in advance.

---

### Post by CelticWarrior on 2020-05-12
First of all try disabling Secure Boot.

---

### Post by goemonburo on 2020-05-12
Thanks, this computer is a desktop and I don't believe it ever had that.  I don't think that's what's wrong here.  Any other thoughts?

---

### Post by dragonfly41 on 2020-05-12
What does this command yield ..

[FONT=monospace][COLOR=#000000]sudo mokutil --sb-state

ah! you can't type this command.

[then any tips here]("https://askubuntu.com/questions/1033767/keyboard-not-working-after-update-to-18-04")?
[/COLOR]
[/FONT]

---

### Post by goemonburo on 2020-05-12
Right now I'm using a boot USB.  Yeah.  The problem is (well, the immediate problem!) is that when I get to the prompt, I can't use the keyboard at all.  :-(

---

### Post by CatKiller on 2020-05-12
> **goemonburo said:**
> Am I best off running Ubuntu from a boot disk or boot usb?

Yes, you are. No boot and no keyboard makes fixing things tricky. From the live USB you'll have keyboard and Internet. Makes fixing things *much* easier.

For fiddling with files you can just mount the partition with your installation on and fiddle away. For *running commands* you'll want to mount the partition then *chroot* (**ch**ange **r**oot) to wherever you mounted it to: that will run commands as if whichever mount point was the root directory, exactly as if you'd booted to a command-line interface but with a working keyboard.

---

### Post by goemonburo on 2020-05-12
Can you give me a little more hints as to WHAT I should fiddle with?  :-)  I'm not sure if I need to just get the Nvidia drivers successfully installed or if there's more going wrong.  Any help would be hugely appreciated...

---

### Post by CatKiller on 2020-05-12
> **goemonburo said:**
> Can you give me a little more hints as to WHAT I should fiddle with?  :-) 

Nope :P

I've steered *well* clear of Optimus.

> I'm not sure if I need to just get the Nvidia drivers successfully installed or if there's more going wrong.  Any help would be hugely appreciated...

It's certainly a likely candidate. Purging all the nvidia stuff and adding *nomodeset* to your boot options *might* get your machine booting again, albeit at low-resolution and with no acceleration. Then you'd be able to try installing it again.

Or it might be something else.

Black screens or boots stalled with an error message are one thing - it gives you something to go on - but dumping to BusyBox is the **I have literally no idea what to do now** response from the boot process. Could be a messed up kernel module, could be a missing hard drive, but whatever it is it's caused the boot process to simply throw its hands in the air and give up.

Oh, just spotted that you were using drive encryption. I don't have any experience of that, either.

---

### Post by goemonburo on 2020-05-12
Well, that's yes, a bit concerning.

But let's say the issue is with the nvidia driver.  Say, it didn't complete, or got interrupted mid-install, or maybe isn't compatible with my old system.  Is there a chance I could try reinstalling the old driver and restoring the system at that point?

A thread I was looking at said something about editing /etc/gdm3/custom.conf and uncommenting #WaylandEnable=false  Might that work here?  If so, how would I access the drive if I'm running a USB live version?

---

### Post by CatKiller on 2020-05-12
In reverse order:

> **goemonburo said:**
> If so, how would I access the drive if I'm running a USB live version?

The same sort of mount command that you'd normally use, of which there are many examples all over, followed by a chroot to wherever you mounted it to, will let you run commands as if you'd booted the system normally. ```
sudo mkdir /mnt/some-place
sudo mount /dev/some-device /mnt/some-place
sudo chroot /mnt/some-place
```

If you're just playing with files you'd only need to do the middle one. It's possible that you'll need to do some kind of unlocking thing for your encrypted filesystem before you can mount it, but I don't know anything about that.

> A thread I was looking at said something about editing  /etc/gdm3/custom.conf and uncommenting #WaylandEnable=false  Might that  work here?  

No. That's for if you can't start a normal session. Wayland on Nvidia is... problematic... because reasons, and it used not to work at all. Despite it not working at the time, Gnome used to default to a Wayland session even on Nvidia. That edit tells it not to do that. Your system is broken long before it gets to the display manager stage.

> But let's say the issue is with the nvidia driver.  Say, it didn't  complete, or got interrupted mid-install, or maybe isn't compatible with  my old system.  Is there a chance I could try reinstalling the old  driver and restoring the system at that point?

Sure. Like I said, in a chroot you can run any command as if you'd booted normally. That includes package management things or grub-configuration things that you can't do just by fiddling with files.

You were there when you did the update, and you know about the hardware and software that you've got, and you've got the machine in front of you. You're much better placed than we are to work out what's up with it.

It's also worth remembering that you can backup any files that you want to keep from a live session, too, in case you can't figure out what's wrong. Assuming you can decrypt it.

---

### Post by goemonburo on 2020-05-12
The problem with Linux is that it's necessary to know exactly what to type and do or one can truly mess things up.  Sorry if this is too vague -- I would be more than happy to provide more tech specs if they will help, just let me know what would be useful.  As I mentioned above, it's a Dell Studio XPS 8100 running Lubuntu 18.04LTS.  It has 16GB of ram, a 1TB hard disk...not sure what else is useful in regards to the graphics driver/booting issue.  

So, anyway...the above "sudo mkdir..." is very helpful.  Thank you, @catkiller!  

I get an error message trying to "sudo chroot /mnt/mydrive" saying failed to run /bin/bash, no file or directory.  I see a bunch of solutions to this but in various ways -- am I truly missing /bin/bash?  Is there some other issue?

Also, my drive has 3 partitions:  sda1, sda2, and sda5.  I mounted sda1 in the "mydrive" and it appears to be the boot, with the various linux images on it.  Is this where I'd be needing to go to reinstall the graphics drivers?

And the process, if I'm understanding it right, would be to mount the (correct) partition, then run apt-get install or ubuntu-drivers autoinstall or some such, hopefully getting it to properly install this time?  

I am still at the point of hopefully NOT needing to back up...hoping it is just a boot/graphics issue, not something that will require a new system.  

Would it be worth trying to reinstall the old graphics card just for kicks and see if it will boot with that?

Again, sorry if this is all too vague and I do (totally) understand that I'm the one with the system (and problem, #facepalm) but if there are any other suggestions that will help get this back to a functioning state that would be fantastic.  I feel like the issue of "graphics drivers failed, how to restore a bootable machine" can't be too unusual.

---

### Post by CatKiller on 2020-05-13
Bear in mind that I generally type responses on my phone, and I don't have any direct experience of the situation that you're in. Vague higher level pointers of approaches that could conceivably work if people find out how to do it, and if my instincts aren't totally wrong, are generally what I can offer, and sometimes that's helpful :) 

> **goemonburo said:**
> Also, my drive has 3 partitions:  sda1, sda2, and sda5.  I mounted sda1 in the "mydrive" and it appears to be the boot, with the various linux images on it.  Is this where I'd be needing to go to reinstall the graphics drivers?

I would guess that sda1 would be a /boot partition or EFI System Partition, and that sda2 would be the one you're after. There's no harm in mounting them all and having a poke around. The / partition of your install will be the one that has things like /etc and /usr in. If you've set up a separate /home partition sda5 could be that, or it could be a swap partition, or you might have done something different with the partitions. 

> And the process, if I'm understanding it right, would be to mount the (correct) partition, then run apt-get install or ubuntu-drivers autoinstall or some such, hopefully getting it to properly install this time?   

Yep, that's the plan. Get your packages ship-shape and see what happens then. 

The encryption could still be the issue rather than the graphics. The graphics driver *does* have a kernel module that needs to be loaded at the start and included in the initramfs, so it's definitely feasible that it's all screwed up in some fashion. However, you would *also* get dumped to BusyBox if the boot process can't find the next stage of the bootloader (an inaccurate fstab can do this) which *could* happen if the bootloader can't unlock the partition that holds the next stage. Or it could be something else. 

> I am still at the point of hopefully NOT needing to back up...hoping it is just a boot/graphics issue, not something that will require a new system.   

The thing is, a reinstall takes about 20 minutes. All the time you're learning stuff and it's interesting it's OK that it's broken. We've all been there. Other times having a broken computer is boring or really inconvenient, so being back up and running really quickly is what you need, and you can work out why it broke later. The *nuke it from orbit* call varies from individual to individual, and from day to day. 

> Would it be worth trying to reinstall the old graphics card just for kicks and see if it will boot with that? 

It probably won't help, but it also probably won't hurt. It's another thing to cross off the troubleshooting checklist. 

> I feel like the issue of "graphics drivers failed, how to restore a bootable machine" can't be too unusual.

It does crop up now and then, but it normally presents differently. Low resolution and things not working properly, or a black screen that doesn't do anything, are things that you'd normally see with a failed nvidia install. Your issue seems to be at a more fundamental level, although it may turn out to be an easy fix once we discover what the actual problem is. Poking it to see what doesn't look right is the best we've got to go on at the moment, and knowing what "looks right" actually looks like comes after quite a lot of poking :)

---

### Post by goemonburo on 2020-05-13
@catkiller, yes, that makes sense -- being on the phone makes it hard to type exact line-for-line instructions.  

I've had a similar (though always different!) issue with graphics cards nearly every time I've upgraded, so I am (fingers crossed) pretty sure that I just need to get things fixed rather than reinstall.  I've been doing the full disk encryption for years and it's always been possible to reinstall and retweak and get the system back to shape again.

Not having a keyboard is certainly frustrating though!  

But back to the steps needed to have a workable bootable system.

I have no problems getting to the live CD.

From there, I have been able to mount /dev/sda1

Chroot hasn't worked, but I woke up this morning thinking maybe it's just because I should run "/bin/bash/chroot" instead of "chroot"?  Does that seem likely?

From there, would I maybe want to reinstall grub?  

(I am able, though, to get to grub by hitting F12...so I'm also thinking it's not grub.)

But if I hit F12, is there a way perhaps to force use of the Nouveau driver for a one-time boot?  Because the card WORKED FINE earlier, using my old card's Nvidia 360 drivers.  It was only when the process of upgrading to Nvidia 440 drivers failed (the system just hung) that this occurred.  So I know that the card CAN work (even if not fully!) on my system.  And if I can tell the computer to use different drivers instead of the messed up version that's included there, maybe that will fix things?

My biggest problem is that I know what I did and what happened and what the effects are...but not the commands and tools to diagnose and fix.  Just writing this out, I feel like maybe that "run using nouveau" option by editing the grub install might be worth a try.  

Thank you for any additional help you can offer -- I appreciate it!  And again, yes, being on a phone makes things a bit more challenging!  Thank you!  :-)

---

### Post by goemonburo on 2020-05-13
So interestingly, I was able to get the partition successfully mounted (had to use luks crypto stuff, but it worked fine).  Did some chrooting and then tried a few things.  Alas, no dice thus far.  I may end up backing up the drive and reinstalling fresh.  

Oh, I put the old card in to see if that would magically repair things and it didn't.  Really doubted it would, but worth a shot.  

Back in a bit after I continue puttering...  ;-)

---

### Post by CatKiller on 2020-05-13
> **goemonburo said:**
> From there, I have been able to mount /dev/sda1 

It's probably not sda1 that you want. After you've changed the location of root you still need an execution environment for the terminal to hand over to: an actual / will have that, but some other partition won't. 

> From there, would I maybe want to reinstall grub?   

Probably not. If Grub were missing it would be the UEFI that couldn't get to the next stage of the boot process, and it would complain about "no Operating System found" or similar. 

> But if I hit F12, is there a way perhaps to force use of the Nouveau driver for a one-time boot?   

Maybe. There is a recovery mode that will not try to load any graphics stuff. 

> Because the card WORKED FINE earlier, using my old card's Nvidia 360 drivers.  It was only when the process of upgrading to Nvidia 440 drivers failed (the system just hung) that this occurred.  

OK, now we're getting somewhere. First off, the nvidia drivers often trip themselves up when going from one branch to another: the presence of one branch stops the other from installing properly. Purging the old branch before you install the new branch stops that happening. I have no idea if the automated driver tool is sophisticated enough to do that, since I've never used it. Second thing is that the package manager may have been waiting for input somewhere, which you'd have been able to enter if you were doing it from the command line but, again, the automated tool might not be sophisticated enough to allow that. But by interrupting it it's not going to be in a good state. 

The good news is that package management is one of the things that works perfectly fine in a chroot. So run one of the "sort yourself out, package manager" commands (something like *apt install -f* or *dpkg --configure -a*), then probably purge all the nvidia stuff, then install the 440 branch. Or the 360 branch if you prefer, but definitely only one of them.

---

### Post by goemonburo on 2020-05-13
Hi @catkiller, just checking in and in the meantime I've been getting somewhere -- happily chrooting, so (as you mentioned) in the worst case scenario I could just backup the files and reinstall.  BUT I feel like I'm not too far away from getting this working.  However, an odd thing has cropped up:

I am unable to use the network within the chroot.  

On the same machine, I have no problem running Firefox and can access any pages I want.  But in the terminal and on the chroot, if I try to ping Google I get no response, and when I try to add or update via apt, it's not finding any of the repositories.  

So that's the current hurdle.  I have tried changing the /etc/hosts file to 8.8.8.8 but that didn't work (entirely possible that I didn't do it correctly).  I've been restarting the network with "sudo service network-manager restart" and it seems to restart...but somehow, all my ppas are inaccessible.

---

### Post by goemonburo on 2020-05-13
So at the command line, if I try to ping "google.com" I get "unreachable."  But if I ping 8.8.8.8 it works fine.  So there's some weird thing happening with the DNS resolving now.  I think once that's fixed, I can manually install the right Nvidia driver and try rebooting.

Also, I may have used the wrong file.  Other posts say it should be /etc/resolv.conf that's edited, not /etc/hosts...

---

### Post by goemonburo on 2020-05-13
Additional info:  when I say "the command line" I am using the terminal into which I've chrooted.  If I use a fresh terminal that's just the prompt of the Live USB, then I don't have this issue...I can ping with proper DNS resolution.  But (am I wrong?) I was under the impression that to run apt-get and so on the proper volume, I need to be doing it on that terminal window.  

Thank you (again!) for sticking with this and helping me.

---

### Post by goemonburo on 2020-05-13
Nevermind!  I got the network part working.  Now off trying the nvidia driver reinstall....

---

### Post by goemonburo on 2020-05-13
So I added the graphics-drivers/ppa and then added nvidia-driver-440 and it chugged and churned and seemed to go well except that at the very end I'm getting this:

(after the "processing triggers" lines...)
update-initramfs: Generatng /boot/initrd.img-4.15.0.-99-generic
cryptsetup: WARNING: invalid line in /etc/crypttab for myvolume -
W: initramfs-tools configuration sets RESUME=UUID=(hexnumber-here)
W: but no matching swap device is available.

Could this be causing the whole problem?  It does say "Warning" but not "Error."  So....?

I am going to try rebooting and will be back with an update.  Thank you!

---

### Post by CatKiller on 2020-05-13
> **goemonburo said:**
> update-initramfs: Generatng /boot/initrd.img-4.15.0.-99-generic
cryptsetup: WARNING: invalid line in /etc/crypttab for myvolume -
W: initramfs-tools configuration sets RESUME=UUID=(hexnumber-here)
W: but no matching swap device is available.

Could this be causing the whole problem?  It does say "Warning" but not "Error."  So....?

It definitely could be: it checks if there's a resume image, in case you hibernated rather than shut down, but if it can't find where it's supposed to be looking, that could definitely cause it to throw a wobbler.

The hex number is the UUID of your swap partition. You might be able to set it to the right thing, or you might be able to tell it not to look. I'm not sure exactly where that's set.

---

### Post by goemonburo on 2020-05-13
Alas, a reboot and I am in exactly the same place.  Grrrr.  I will do some digging and see if I can figure out that part of it.  I would have done whatever swap defaults Lubuntu sets one up with.  The "myvolume" though is the name that I used for the chroot and mount stuff...would it be better if I changed "myvolume" to something actual?  (And how would I figure out what that is?)

---

### Post by CatKiller on 2020-05-13
The UUID is set at partition creation and isn't affected by boot order and the like, like the sdx identifiers are, so they're handy. The swap one does seem less fixed than the other types - resizing a swap partition seems to destroy it and create a new one, for example. You can see what the UUIDs are with **blkid**.

---

### Post by goemonburo on 2020-05-13
So I found a thread with something similar and am trying to use update-initramfs -u -k all to redo things.  It seems that renaming my "resume" file in /etc/initramfs-tools/conf.d has gotten rid of one of the errors thrown.  I don't know if this will cause other things to fail but my hope is to get these kernel images to rejigger without the errors.

Then the UUID stuff is over my head.  I am trying now to get rid of the "invalid line in /etc/crypttab for myvolume" which sort of makes sense since "myvolume" is a different thing than the original drive, no?  

In there, I have "sda5_crypt UUID= (long number) none luks,discard
cryptswap1 UUID= (other long number) /dev/urandom swap, offset=1024, cipher=aes-xts-plain64"

When I do blkid, I get a UUID for /dev/sda5 that is different from what was in the RESUME file.  Could that be the reason for that swap error?  

Should I edit something so that the UUID is correct?

Just kind of dog paddling in the dark at this point.  :-)

---

### Post by CatKiller on 2020-05-13
> **goemonburo said:**
> In there, I have "sda5_crypt UUID= (long number) none luks,discard
cryptswap1 UUID= (other long number) /dev/urandom swap, offset=1024, cipher=aes-xts-plain64"

When I do blkid, I get a UUID for /dev/sda5 that is different from what was in the RESUME file.  Could that be the reason for that swap error?  

Should I edit something so that the UUID is correct?

The *sda5* that you see now that you've booted from a thumb drive may well not be called *sda5* when you're booting normally. The numbers change, depending on what else is plugged in and how quickly a given drive perks up to be counted. That's why UUIDs exist instead. So don't just change that value to whatever's sda5 *now*, change it - only if it needs changing - to whatever partition it's supposed to be referring to. Given that you have two entries, one for / and one for the swap seems logical, but you know which partitions they are. And there's no reason either of them should necessarily be sda5.

Bearing in mind I have no experience with encrypted drives, of course.

(UUID is Universally Unique Identifier, if that helps understand it)

---

### Post by goemonburo on 2020-05-13
So I have made a little progress...just a little.  I am now able to use the keyboard and reinstalled grub...but all it's doing is leaving me at a grub shell with a "Minimal BASH-like line editing is supporte..." note at the top.

It's clearly not finding any kernel images to offer.  And possibly wiped anything that was already there.

But the good news is that at least I can type stuff at this shell.  #facepalm

There seem to have been issues with /etc/crypttab and /etc/fstab -- causing issues when I ran update-initramfs.  Finally managed to fix that enough that the errors stopped showing up, but when I eventually rebooted...didn't get too far.

Any suggestions what to do from here?  I am guessing I need to create a Linux image and tell Grub about it.  Does that sound right?  And if so, how would I do that?  

Thanks so much.

---

### Post by CatKiller on 2020-05-14
I would say that at this point it's definitely time to throw in the towel.

---

### Post by goemonburo on 2020-05-14
Thanks for your time.  I will sleuth on the options for backing up my files.  While I was able to mount and decrypt the sda5 volume, I haven't yet gotten to where I can access my home dir (as that is also password protected and encrypted).  So it's not as simple to just back up and copy things.  

But I'll figure it out.  Thanks for the suggestions thus far.  Stay healthy!

---

