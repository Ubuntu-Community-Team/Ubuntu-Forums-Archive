---
title: "Cannot unmount USB hard disk in Ubuntu 7.04"
date: 2007-04-04
forum: General Help
---

### Post by function151 on 2007-04-04
When trying to remove an external USB hard disk, an error reading "Cannot eject volume" and a message stating "data needs to be written to the device (...) before it can be removed" are produced. 

The drive does appear to be unmounted for a second before the error appears, then it's re-mounted.

This only occurs when attempting to unmount the disk through Nautilus (right click -> "Eject" on the desktop, "Unmount" or "Unmount Volume" in the file browser). However, using "sudo umount  /dev/sdb1" works without error, as does "unmount" in GParted.

Disk permissions have me as owner (uid 1000) with root as group. File access is "---" for all fields. Owner folder access is set to "create and delete files". The remaining folder access fields are set to "none". I have not been able to change these permissions under in any way, even as root. 

The following are the applicable contents of my mtab:
/dev/sdb1 /media/disk vfat rw,nosuid,nodev,shortname=mixed,uid=1000,utf8,umask=077 0 0

This has become increasingly annoying, if anybody has an idea or solution I'd greatly appreciate it.

---

### Post by vikasrawal on 2007-04-04
This would normally happen because there is some process using the disk in question. You could use [COLOR="SeaGreen"]ps x | grep /media/disk[/COLOR] and use [COLOR="SeaGreen"]lsof /media/disk[/COLOR] to check the processes that are accessing the disk. If possible, run them as root because there may be some system processes accessing the disk. Once you know which processes are accessing the disk, you can kill them and then umount.

V.

---

### Post by MeneK on 2007-04-05
I have the same problem (not being able to unmount an USB drive in Feisty). Some of the last week updates changed something, since it was working perfectly until then.

---

### Post by dngpng on 2007-04-05
I confirm this, and I tried the two commands vikasrawal mentioned but there is no output i.e. no process using the disk

---

### Post by nilsja on 2007-04-06
i confirm the status of dngpng. external 250 gb harddisk via usb. 
> nils@schlepptop:~$ ps x | grep /media/Elements
16150 pts/0    R+     0:00 grep /media/Elements
nils@schlepptop:~$ lsof /media/Elements
nils@schlepptop:~$ 

---

### Post by rondackcpu on 2007-04-06
I, too, am having this problem with one of the several USB flash sticks I have.  Only the SANDISK256M gets "stuck" and won't eject.  The others work normally.  I can unmount it with "sudo" and get no error messages.  I believe, as above, that something happened in the recent upgrades to 7.04 Beta.

---

### Post by chalumeau on 2007-04-06
I confirm the last post since two days updates, my 2 USB stick are ok, but I **(USER)** cann't umount my 2 USB HDD, only **ROOT** can by sudo umout /media/XXX

---

### Post by mulno on 2007-04-06
I have a similar problem with a "Traveller" digicam. If i try to eject it, I'm getting a popup window telling me "Cannot eject volume". The device is unmounted though and there is no attempt to remount it, if I uncheck the options in the preferences dialog.

Funny thing : I had a problem mounting the device some time ago using KDE and Breezy. This was among other things the reason why I switched back to Gnome. Now the device is perfectly handled with KDE but not with Gnome.

I Liked to see a tutorial on how to edit the HAL config files but didn't find one on the web.

---

### Post by nilsja on 2007-04-06
in the console **eject sdb1** works fine in my case. but the nautilus context menu links still don't work...

---

### Post by fsf@rula on 2007-04-08
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/103790](https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/103790) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This is surely not because of the volume being used, as the volume does get unmounted, but then it gets remounted right away. Please check launchpad [_bug #103790_]("https://bugs.launchpad.net/ubuntu/+source/util-linux/+bug/103790").
My guess is that this is a HAL issue, but it might also be udev or kernel.

---

### Post by nilsja on 2007-04-11
see the attachment

---

### Post by trav5 on 2007-04-12
nilsja same problem here[ATTACH]29552[/ATTACH]

But my usb stick works fine.

---

### Post by mulno on 2007-04-16
For me the following works:
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/99538/comments/6](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/99538/comments/6)

---

### Post by cookfromfrozen on 2007-04-20
Same problem here with 250GB external HDD.  Don't have the problem with any other USB mass storage devices, only the external HDD.

The workaround works but still doesn't seem as "clean" as it did in Edgy; for example I don't hear the USB drive "click" anymore which I assume is the HDD heads parking.

---

### Post by b0ng0 on 2007-04-21
I have the same problem with my external hdd. I can eject using sudo eject but that's the only way and it's lame :p.

---

### Post by mdurham on 2007-04-21
Try editing the file /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi and for usb devices set requires_eject to false, and see if that makes any difference.

---

### Post by reacocard on 2007-04-21
> **mdurham said:**
> Try editing the file /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi and for usb devices set requires_eject to false, and see if that makes any difference.

Or better yet, just move the file:
```
sudo mv /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi /usr/share/hal/fdi/policy/10osvendor/storage-policy.fdi.bak
```

That command fixed it for me. I now have an unmount option instead of eject, and it works exactly as expected.

---

### Post by b0ng0 on 2007-04-21
I tried that option and although it does indeed allow you to unmount the drive, with my external hdd it does not power down, it just keeps running so I do not think that it has been safely removed. When I sudo eject it, it powers down like it does in Windows. 

So although that may be a solution ot USB stick problems, i'm not sure it's the safest option for external hard drives.

---

### Post by ingo on 2007-04-21
Hi,

I cannot access any usb devices at all! I tried both bug solutions mentioned above but neither worked :)

---

### Post by reacocard on 2007-04-21
> **b0ng0 said:**
> I tried that option and although it does indeed allow you to unmount the drive, with my external hdd it does not power down, it just keeps running so I do not think that it has been safely removed. When I sudo eject it, it powers down like it does in Windows. 

So although that may be a solution ot USB stick problems, i'm not sure it's the safest option for external hard drives.

It works fine for my usb hard drive.

---

### Post by b0ng0 on 2007-04-22
What I mean is that I don't hear the hdd "click" as someone mentioned above which is the heads coming to rest (which means it has been properly d/c). Seems weird since I had no problems in edgy.

---

### Post by cookfromfrozen on 2007-04-22
> **b0ng0 said:**
> I tried that option and although it does indeed allow you to unmount the drive, with my external hdd it does not power down, it just keeps running so I do not think that it has been safely removed. When I sudo eject it, it powers down like it does in Windows. 
That is exactly what I'm seeing too.  What drive have you got?  I've got a 250 GB Western Digital My Book and in Edgy, when I right click and Eject, the drive unmounts and I hear a "click" from the drive and it powers down.

In Feisty I get the "Cannot eject volume", but when I do the fdi file workaround, it unmounts, but the drive does not "click" and it stays powered on.  I don't feel "safe" leaving it like that, it doesn't seem to have powered down fully so I don't know if it has really unmounted properly or not.

I've tried restoring the fdi file from Edgy, but it still doesn't make the drive power off like it did in Edgy.  I can't really risk moving to Feisty until this is fixed because I have a lot of important stuff on my external HDD and I can't risk losing it. :(

This is where some more discussion is happening, it would be really helpful if you could comment there too as then we have another person to confirm they are having the prob as well

[https://bugs.launchpad.net/ubuntu/+bug/99538](https://bugs.launchpad.net/ubuntu/+bug/99538)

---

### Post by b0ng0 on 2007-04-22
Yeh I have the exact same drive as you, but I don't think it's a specific problem with the WD HDD, probably just the way is disconnects from the computer. I'll have a look at that link.

Just fyi, I think that you can turn the drive off safely just by pushing the power button on the front, if it's in use it won't let you turn it off that way so technically you could still move to Feisty, you'd just have to turn it off that way (or sudo eject it which seems to work fine).

---

### Post by reacocard on 2007-04-22
Oh that's what you mean. I also have a MyBook (160GB), and yeah it doesn't power down on unmount, but I've never had any trouble with that. After it's unmounted you can just unplug it from the computer and it'll turn off just fine. It does unmount fully, it just doesn't get the signal to turn off.

---

### Post by cookfromfrozen on 2007-04-22
Yeah, come to think of it, as long as the device doesn't show up in the list from the mount command, the caches should have been flushed and there should not be any chance of data loss.

I just tried it and you're right, when you press the power button it makes the "click".

It would be nice to see it work the way it did in Edgy though.

---

### Post by eumetaxas on 2007-04-23
hello guys!
i've just moved to feisty 7.04
i have an external WD HDD 250GB with ALL my valuable files on. i have exact the same problem as the others. i cannot unmount the drive and i cannot take the risk. to feel sure i need to hear the 'click' of the power off button. i don't know if i am overreacting but i switch to windows to unplug the drive. on edgy everything worked fine and the same must be on feisty too!
thanks for support!!

---

### Post by SonicSteve on 2007-04-23
I'm having this same issue. I never had it with Dapper or Edgy. My drives are generic 3.5" laptop usb drives. One has a Toshiba drive the other an IBM travelstar.

I tried this work around but no luck. 
[https://bugs.launchpad.net/ubuntu/+source/hal/+bug/99538/comments/6](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/99538/comments/6) 
it says to do this.
Can you guys please temporarily move away /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi, then reboot and check if it works then? If so, then bug 63090 would be the root cause. Thanks in advance!

Hopefully this gets fixed soon. I don't like corrupting data.:(

---

### Post by vanadium on 2007-04-23
Whant would be the consequence of moving that particular file? For me, it works, but why was the file there in the first place and what are the risks of "inactivating" it?

---

### Post by b0ng0 on 2007-04-23
All moving this file does is change the Eject option to Unmount Volume when you right click (a la Edgy style). This seems to work if you're having trouble, but as I've previously said, for external HDDs (mine anyway) it does not 'properly' disconnect the drive as say, "sudo eject sdc1" would.

---

### Post by reacocard on 2007-04-23
> **eumetaxas said:**
> hello guys!
i've just moved to feisty 7.04
i have an external WD HDD 250GB with ALL my valuable files on. i have exact the same problem as the others. i cannot unmount the drive and i cannot take the risk. to feel sure i need to hear the 'click' of the power off button. i don't know if i am overreacting but i switch to windows to unplug the drive. on edgy everything worked fine and the same must be on feisty too!
thanks for support!!

If you do (replacing /dev/sdb1 with your drive's partition)
```
sudo eject /dev/sdb1
```

from the terminal, it powers off properly. However, 
```
sudo eject /dev/sdb  #(ejecting the device, not partition)
```

does not work properly, but instead produces the same behavior as the current 'Eject' right-click option. I think this is the root of the problem: HAL is doing 'eject /dev/sdb' (or equivalent), instead of 'eject /dev/sdb1', as it should.

---

### Post by in_flu_ence on 2007-04-24
> **reacocard said:**
> If you do (replacing /dev/sdb1 with your drive's partition)
```
sudo eject /dev/sdb1
```

from the terminal, it powers off properly. However, 
```
sudo eject /dev/sdb  #(ejecting the device, not partition)
```

does not work properly, but instead produces the same behavior as the current 'Eject' right-click option. I think this is the root of the problem: HAL is doing 'eject /dev/sdb' (or equivalent), instead of 'eject /dev/sdb1', as it should.

I tested what you mean and it only works for /dev/sdb1. /dev/sdb doesn't eject the usb drive properly.

---

### Post by in_flu_ence on 2007-04-24
Has anyone tried to change the /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi

where ```
<match key="info.category" string="storage">
      <match key="storage.bus" string="usb">
        <merge key="storage.requires_eject" type="bool">true</merge>
``` from true to false.

It seems that I can unmount the drive but not sure if it will create the 'click' effect.

---

### Post by b0ng0 on 2007-04-24
Thanks for the information, i'll give it a try and let you know.

EDIT: Just tried changing this and it has the same effect as moving the file (the one you said to edit). Stops the HDD talking to the computer but does not power it off. :(

---

### Post by reacocard on 2007-04-24
> **in_flu_ence said:**
> I tested what you mean and it only works for /dev/sdb1. /dev/sdb doesn't eject the usb drive properly.

Reread my post, that's exactly what I said it does. Or rather, doesn't do. ;)

> **in_flu_ence said:**
> Has anyone tried to change the /usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi

where ```
<match key="info.category" string="storage">
      <match key="storage.bus" string="usb">
        <merge key="storage.requires_eject" type="bool">true</merge>
``` from true to false.

It seems that I can unmount the drive but not sure if it will create the 'click' effect.

> **b0ng0 said:**
> Thanks for the information, i'll give it a try and let you know.

EDIT: Just tried changing this and it has the same effect as moving the file (the one you said to edit). Stops the HDD talking to the computer but does not power it off. :(

Yep, I tried that too. Same results.

---

### Post by in_flu_ence on 2007-04-24
I was trying to confirm that what you get is what i get which => not any one's fault but rather a bug to be fixed:P

---

### Post by ramjet_1953 on 2007-04-25
Follow this link for a fix:

[http://ubuntuforums.org/showthread.php?t=418688&highlight=USB+HDD](http://ubuntuforums.org/showthread.php?t=418688&highlight=USB+HDD)

Regards,
Roger :cool:

---

### Post by b0ng0 on 2007-04-25
Thanks for the reply Rog but that only appears to be the solution for USB memory. The main problem we are having is with USB HDD's where the drives do not power down when Ejected (they previously did in Edgy).

---

### Post by cookfromfrozen on 2007-04-25
> **in_flu_ence said:**
> I tested what you mean and it only works for /dev/sdb1. /dev/sdb doesn't eject the usb drive properly.

I tested that here and it's true, but it's also true for my in Edgy too, whereas the Gnome ejection problem seems to have been introduced in Feisty.

---

### Post by 23meg on 2007-04-25
> **b0ng0 said:**
> Thanks for the reply Rog but that only appears to be the solution for USB memory. The main problem we are having is with USB HDD's where the drives do not power down when Ejected (they previously did in Edgy).

Firewire drives are affected too.

---

### Post by in_flu_ence on 2007-04-25
i m not very sure about the launchpad system. How do one request a bug fix in such case?

Think maybe there should be an update soon:P

---

### Post by b0ng0 on 2007-04-25
I know you can post bugs there but I've no idea if anyone has  even looked at this since there's been no reply -_-

---

### Post by catchmeifyoutry on 2007-04-25
> **eumetaxas said:**
> hello guys!
i've just moved to feisty 7.04
i have an external WD HDD 250GB with ALL my valuable files on. i have exact the same problem as the others. i cannot unmount the drive and i cannot take the risk. to feel sure i need to hear the 'click' of the power off button. i don't know if i am overreacting but i switch to windows to unplug the drive. on edgy everything worked fine and the same must be on feisty too!
thanks for support!!

Hi, I have a WD My Book HDD that I connect to my laptop (Ubuntu Feisty) over firewire (USB works too).
To unmount it, open a terminal and type
```
sudo umount /media/My\ Book
```
If I try to eject it using the desktop icon menu, it reconnects immediately, but when using this command the drive seems to unmount properly.

Btw, after reading some other comments here I tried
```
sudo eject /media/My\ Book
```
and that works too. Any reason to prefer eject over umount?

---

### Post by b0ng0 on 2007-04-25
Well from my experience, using the unmount volume command does not cause the drive to "click" (i'm sure you know what i mean) and thus is not fully disconnected - whether or not this is a risk I have no idea. 

However in my experience, using the Eject command causes the drive to power down properly when run, whereas the unmount command simply unmounts the device but you can still see that the drive is running after it has been unmounted.

Hope that makes sense.

---

### Post by reacocard on 2007-04-25
> **b0ng0 said:**
> Well from my experience, using the unmount volume command does not cause the drive to "click" (i'm sure you know what i mean) and thus is not fully disconnected - whether or not this is a risk I have no idea. 

However in my experience, using the Eject command causes the drive to power down properly when run, whereas the unmount command simply unmounts the device but you can still see that the drive is running after it has been unmounted.

Hope that makes sense.

Under edgy I was running XFCE (and later, custom Xsession), so the GUI only had unmount, not eject. I used my external HDD for 4 months that way, and it doesn't seem to have had any bad effects whatsoever. Eject is still nice though, just for the audible feedback.

---

### Post by cmmike1 on 2007-04-25
I have the same problem but i found out that i can connect it via firewire which i was previously unable to do in edgy. I would like to see and update fix the USB error though.

---

### Post by catchmeifyoutry on 2007-04-25
> **cmmike1 said:**
> I have the same problem but i found out that i can connect it via firewire which i was previously unable to do in edgy. I would like to see and update fix the USB error though.

Firewire has the same problem in my experience, and others have reported this too. Does using firewire make a difference on your external HD? :confused:

> **b0ng0 said:**
> 
However in my experience, using the Eject command causes the drive to power down properly when run, whereas the unmount command simply unmounts the device but you can still see that the drive is running after it has been unmounted.
> **reacocard said:**
> Under edgy I was running XFCE (and later, custom Xsession), so the GUI only had unmount, not eject. I used my external HDD for 4 months that way, and it doesn't seem to have had any bad effects whatsoever. Eject is still nice though, just for the audible feedback.

I'm still kind of new(b) to Ubuntu, so thanks for the tips.
I'll use my ears next time. :)

---

### Post by f3ua on 2007-04-26
Same problem with 80 GB maxtor usb disk. Never had before update.
I hope ubuntu staff fix it quickly.

---

### Post by vanadium on 2007-04-26
To give some insight: 

"unmount" does disconnect the device from the file system

"eject" does physically disconnect the device. To do that, it first must also unmount, i.e. disconnect from the file system. For example, ejecting a CD rom will open the tray.

For example: "sudo unmount /media/cdrom" will unmount  the CD rom from the file system
"sudo mount /dev/cdrom /media/cdrom" will connect it. The gnome desktop moonitors this: the icon accordingly disappears/appears again.

"sudo eject /dev/cdrom" or "sudo eject /media/cdrom" (1st version refer to device, 2nd to mount point) both unmounts and ejects the CD rom.

Bottom line here is that there is no risk for data loss removing a drive after it has been unmounted. Eject does something more, which is very visible for CD roms (it truly ejects it for you), perhaps for USB hard disks, it makes the disk park its head (the "click") but I don suppose it powers the drive down, and for USB sticks, eject probably doesn't do anything more than an unmount does.

I suspect that a drive will automatically park its head after it has not been written to, and I suspect that upon shutting down the drive, heads are also parked. So there shouldn't be any risk of data loss or damaging the drive.

Anyway, this very visible bug will probably be fixed quite soon.

---

### Post by fsf@rula on 2007-04-26
Well, I have tried the storage method HAL configuration policy file from fedora,suse and from the HAL git tree, all to no avail, not only does it not work with the hal in ubuntu, but it messes up storage so bad that my external hdd wouldn't even mount (automatically).
I have no idea how to edit the file or how to debug hal, so I will not try. I also tried the file from edgy, which worked better, the unmount operation gave me three boxes saying it wasn't able to unmont before unmounting and ejecting the drive (stange, eh).
I hope this bug gets fixed pretty soon, as this is really an important one, also, it has been around for at least 3 weeks if not more, so I don't really know hwy it wasn't fixed in beta allready
Also, here is the bug URL, if anyone has _useful_ comments (A FIX WOULD BE GREAT), please check it out: [https://bugs.launchpad.net/ubuntu/+source/hal/+bug/63090](https://bugs.launchpad.net/ubuntu/+source/hal/+bug/63090) .
Cheers!

--edit
okay, I forgot to reboot after putting the policy files (99-storage-policy-fixed-drives.fdi and 20-storage-methods.fdi ) from the suse package into /usr/share/hal/fdi/policy/10osvendor/ worked for me, I now can unmount(eject) my drive fine, the workaround goes as follows:
download [http://librarian.launchpad.net/7411241/20-storage-methods.fdi](http://librarian.launchpad.net/7411241/20-storage-methods.fdi) from launchpad, and put them in /usr/share/hal/fdi/policy/10osvendor/ ,
chown -R root /usr/share/hal/fdi/policy/10osvendor/ and then reboot
now try it, if it works, post here or on launchpad.

--edit yes, it works without the 99-storage-policy-fixed-drives.fdi file

---

### Post by cookfromfrozen on 2007-04-26
Just noticed that LUKS-encrypted volumes like my USB flash drive are somewhat borked too.  They mount once but unmount them and they won't mount again.  It either does nothing after you type the passphrase or says "already set up".  Seems related to this issue.

I don't know what happened with the gnome automounter between Edgy and Feisty but it sure got screwed up pretty good.

---

### Post by catfishy on 2007-04-27
Hi!  Glad to see the work-around for unmounting problems but is there going to be a fix anytime soon, a replacement hal or something?  The un/mounting is fine for me now but not for the millions who will use the 7.04 disc, right?  Also, I came across someone having a problem with a USB external hdd just turning off, not even unmounting.  This happened to me tonight; I left it sitting for a while and it wasn't just sleeping, it was OFF.  Strange!  Thanks for any info friends!

(more description:  when I came back to the machine, an hour later, the drive was still mounted but the actual ext. hdd was powered down/off.  I tried to see if exploring the drive would revive it but then it just hung-up.  I had nothing to do but hold down the power button, yikes!)

---

### Post by cmmike1 on 2007-04-27
when i right click on my firewire drive and click eject it ejects and i can then shut it off. I haven't noticed any problems with it losing information or anything of the sort. Bottom line is that the usb hard drive problem needs to be fixed somehow.

---

### Post by Cyb3rD0n Architectus on 2007-04-27
Hi, I cannot remove my LaCIE 200GB USB disk either, but when I look at my disks properties, I see that the owner is the root all of a sudden. Before the upgrade I was perfectly certain that I (the main user account) was the owner of the disk (view screenshot).

Maybe this might help, as all other possible solutions fail. I even logged in as root and changed the ownership back to the main user account, but it won't budge... :confused:

---

### Post by fsf@rula on 2007-04-28
can you please try with the workaround described in [http://ubuntuforums.org/showpost.php?p=2539063&postcount=49](http://ubuntuforums.org/showpost.php?p=2539063&postcount=49) ?
This bug is going to get fixed sooner if we work together, this is why linux is great, it's somewhat doit yourself :)
of course you can just wait for an update...but this workaround works perfectly for me, so...

---

### Post by reacocard on 2007-04-28
> **fsf@rula said:**
> can you please try with the workaround described in [http://ubuntuforums.org/showpost.php?p=2539063&postcount=49](http://ubuntuforums.org/showpost.php?p=2539063&postcount=49) ?
This bug is going to get fixed sooner if we work together, this is why linux is great, it's somewhat doit yourself :)
of course you can just wait for an update...but this workaround works perfectly for me, so...

Sure thing. I'll report back soon.

EDIT: No luck. It behaves exactly as before.

---

### Post by daimac on 2007-04-28
I also get " Cannot Eject Volume " for my  WD My Book 250 gig External Hard drive . This seems to be a widespread problem with 7.04 as it was working fine in 6.10 . Hope the team have a fix for it soon.

---

### Post by in_flu_ence on 2007-04-28
Seems like there is a pmount update via update manager. Is that the answer to our bug?

---

### Post by reacocard on 2007-04-28
> **in_flu_ence said:**
> Seems like there is a pmount update via update manager. Is that the answer to our bug?

I doubt it, as by default feisty doesn't have pmount installed. (Kubuntu feisty does, but not Ubuntu or Xubuntu)

---

### Post by b0ng0 on 2007-04-28
Just a quick reminder to those who are posting:

If you cannot remove your external HDD, this is a common bug. You can either rename 
/usr/share/hal/fdi/policy/10osvendor/10-storage-policy.fdi to 10-storage-policy.fdi.bak and this will change the Eject option to Unmount Volume which should work (but imo it's not really a proper solution).

Or you can just open up the terminal and type "sudo eject [name of your drive e.g. sdc1]". This is the method i'm using at the moment and it works, it's just a hassle.

---

### Post by in_flu_ence on 2007-04-28
> **reacocard said:**
> I doubt it, as by default feisty doesn't have pmount installed. (Kubuntu feisty does, but not Ubuntu or Xubuntu)

That's fairly strange. I got the update on my ubuntu laptop but not my Kubuntu Desktop
hmm.

---

### Post by hewhocutsdown on 2007-05-02
I have 4 external hard drives, of varying sizes, including a 1TB MyBook, and all exhibit the exact same behaviour. None of them will properly unmount or eject from nautilus.

This was working perfectly on 2 machines running edgy. I did a clean install of feisty on 1 machine, did a dist-upgrade on the other and now neither work; it is an issue introduced with feisty.

The only way I have found where I can guarantee my data is not corrupted is literally shutting down the entire system in order to remove the hard drive. This is unacceptable, but I have not found how to fix this and it seems many more are in this position as well.

I don't mind tinkering with settings files under some circumstances, but this is something that needs to be corrected by default. This is not behaviour that users, particularly those less familiar with the command prompt need to go through.

As a disclaimer: overall I am incredibly appreciative of the fine work everyone has done on feisty. This one issue has been grating on me for several weeks, so I apologize if I come off as ungrateful; I very much am.

---

### Post by kilou on 2007-05-03
> **fsf@rula said:**
> 

--edit
okay, I forgot to reboot after putting the policy files (99-storage-policy-fixed-drives.fdi and 20-storage-methods.fdi ) from the suse package into /usr/share/hal/fdi/policy/10osvendor/ worked for me, I now can unmount(eject) my drive fine, the workaround goes as follows:
download [http://librarian.launchpad.net/7411241/20-storage-methods.fdi](http://librarian.launchpad.net/7411241/20-storage-methods.fdi) from launchpad, and put them in /usr/share/hal/fdi/policy/10osvendor/ ,
chown -R root /usr/share/hal/fdi/policy/10osvendor/ and then reboot
now try it, if it works, post here or on launchpad.

--edit yes, it works without the 99-storage-policy-fixed-drives.fdi file

I tried that but it didn't work for me. Also with the new fdi file my /windows filesystem was show on the desktop as if it was in /media....

Unrelated to the fdi file but now for some reason even when I do sudo eject /dev/sdb my external USB disk is not unmounted. I don't get any error message but the icons on the desktop disappear briefly and immediately reappear.....weird! Before, the eject command did work but not anymore...

---

### Post by trav5 on 2007-05-12
I just did some updates ( hal ) and its fixed:guitar:

---

### Post by Frostmourne on 2007-05-12
I updated as well but Eject still brings the drive back up.

---

### Post by reacocard on 2007-05-12
The updates gave me 'unmount' instead, which works but doesn't power off the drive as it's supposed to.

---

### Post by cookfromfrozen on 2007-05-22
Haven't been around for a while.

Was this fixed, or will it sink away into obscurity never getting fixed like 80% of the other bugs do? ;)

---

### Post by reacocard on 2007-05-22
> **cookfromfrozen said:**
> Haven't been around for a while.

Was this fixed, or will it sink away into obscurity never getting fixed like 80% of the other bugs do? ;)

Fixed here. Not completely, but it does let it unmount properly now, so it works.

---

### Post by kilou on 2007-05-23
The update unmounts the drive or partition but doesn't eject it (power it off). With my USB devices I'm still using eject command in the terminal because it's the only way to power off a USB device properly. Moreover my USB harddisk has many partitions on it. I don't want to right click all mounted partitions and unmount them one oat a time. I believe the behaviour of Edgy was much better since right clicking on a single partition would eject the whole disk (unmount all partitions and power off the disk)! It would be nice to have another fix or workaround to do this. Well typing eject in the terminal is no big deal but Ubuntu is supposed to be GUI for those things....

---

### Post by Sionide on 2007-05-24
Go into Software Sources in the Admin menu - tick unsupported updates on the Updates tab and apt-get update and apt-get upgrade ... Should be updates for HAL - this fixes this issue for me, amongst others..

---

### Post by kilou on 2007-05-25
I already did that. I have the new HAL version (0.5.9). But this did put a "unmount" command in the menu in stead of the usual "eject" when you right-click a USB device. Unmount works but it's not a good solution for me because it doesn't power down the USB disk and I have to unmount each separate partition on the disk. So basically this update didn't solve anything for me. I'm still using eject from the terminal.

---

