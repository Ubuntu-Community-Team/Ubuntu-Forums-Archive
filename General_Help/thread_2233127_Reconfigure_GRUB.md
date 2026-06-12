---
title: "Reconfigure GRUB"
date: 2014-07-06
forum: General Help
---

### Post by Mike_Walsh on 2014-07-06
Evening, all.

Now, then; I've got a wee problem with GRUB.

Since I started with Linux a couple of months ago, I've tried many different combinations of distros, both singly installed, and also in dual-boot config.

I started with Ubuntu, and I keep coming back to it.

My last dual-boot config was Ubuntu & Mint, but I decided to try and resize the partitions, made a complete hash of it, and re-installed Ubuntu by itself. This was about 4 days ago.

I've always liked Zorin's OS 8, but decided it wasn't suitable as a primary O/S, due to a couple of problems that wouldn't go away; I wanted something a bit more stable, which Ubuntu 14.04 is. Anyway, I've decided to re-install Zorin alongside Ubuntu as a secondary O/S in a smaller partition (about 30 Gb), so that I can have a play about with it.

Hence to my problem! With the last dual-boot, I always got GRUB appearing immediately after the system screen, as you should, so I could choose which O/S I wanted. Having installed Zorin, I appear to have lost GRUB. Ubuntu is still all there, in the main partition...but I just can't access it. Zorin appears to have decided it doesn't want to share centre stage, and wants the limelight all to itself... :confused:

Anybody have any suggestions as to how I can reconfigure (or recover) GRUB, so that I can choose between the two O/Ss again? 

A slightly perplexed Mike.

ps I was going to attach the two GRUB .cfg files, so y'all could have a look through them, and let me know what might need changing...but I can't figure out how to convert them to text files, so that they can be scrolled through; another thing I need to get the hang of!:p

---

### Post by Bashing-om on 2014-07-06
Mike_Walsh; Hey,

What we can do is boot up the liveDVD(USB) of ubuntu 14.04 and see where ubuntu is installed to:
```

sudo fdisk -lu
sudo parted -l

```
And once known for sure, (RE-)install - from the liveDVD - ubuntu's grub as that boot manager, and later pick up the Zorin OS to chainload it to ubunt's boot menu.
---------------
Off topic: Attachments ->
If you hit the big red button top left of the post, many additional tools - on the tool bars - are available, in this instance the "paper clip" icon to attach a file. In the event the file is too large, there is 'pastebinit' and post the resulting URL.
-----------------------

[INDENT][INDENT]ain't nothing but a thing[/INDENT][/INDENT]

---

### Post by Mike_Walsh on 2014-07-06
Hallo there.

Well, that's easy enough to tell....if this is what you need to know:-

Ubuntu is installed to /dev/sda1.

Zorin is installed INSIDE extended partition /dev/sda2, at /dev/sda5.

Is that what we need to know? I obtained that from gparted, but I've also run the terminal commands. What exactly is required for installing the bootloader from the live CD, and, um, how do I then go about it? I'm venturing DEEP into unknown territory here, as I'm still fairly new to Linux..!

Regards,

Mike.

---

### Post by jp734 on 2014-07-06
Before doing anything with the partition or grub, try rebooting, and as it boots keep hitting the shift key. I remember doing this some time ago and it let me choose which distro to use.

---

### Post by Bashing-om on 2014-07-06
Mike_Walsh; OK,

See jp734's last. It is worthy of conideration.

To (RE-)install grub:
Taking your word for it, that ubuntu is in fact installed to sda1:
In your process of learning, the terminal is your closest friend - not to be feared !

Boot the liveDVD -> terminal
Terminal commands:
```

sudo mount /dev/sda1 /mnt
sudo grub-install --boot-directory=/mnt /dev/sda
sudo umount /mnt

```
done with the liveDVD;

Reboot into the install.
Now to pick up the Zorin install:
terminal command:
```

sudo grub-install --recheck /dev/sda
sudo update-grub

```
Re-boot once more and now I expect you will have a ubuntu grub boot menu containing the choice to boot Zorin.

[INDENT][INDENT]ain't no step for a stepper
[/INDENT][/INDENT]

---

### Post by NM5TF on 2014-07-06
Hi Mike...

you could also try using ***Boot Repair***....I have found this to be invaluable for my adventures in Linux...

go here:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

tommy

---

### Post by Mike_Walsh on 2014-07-06
Thanks, everybody.

jp734; I thought I'd give your suggestion a try first because it was the easiest! (Nothing ventured, nothing gained...)

I didn't really expect it was going to be that easy....no luck. Tried it 3 or 4 times, too..! No worries; that's the whole point of these forums; lots of folk, lots of different ways to fix the same problem. What works for one won't necessarily work for somebody else; such is life. It was definitely worth a shot..!

Bashing-om; it's too late for me to try your suggestion tonight (it's 1.30 am over here, give or take a few); I'm knackered - had a long ol' day - so tomorrow, I'll give your suggestion a try IF NM5TF's idea about using Boot-Repair doesn't pan out. I'm not frightened of the terminal, but I'm pretty inexperienced with it, and I've already read some horror stories about how ONE single mis-spelling can cause chaos; understandably, I'm a little bit wary of it still! (I REALLY don't want to do yet ANOTHER re-install; I've done too many over the last few weeks...)

NM5TF; ditto as for Bashing-om. Will give your idea a shot tomorrow, when I manage to get back on  here. I don't MIND using Zorin while I get this sorted; I wouldn't have re-installed it if I didn't like it. It's just annoying having an entire O/S sitting there on the hard-drive.....and I can't access it 'cos the boot-loader's decided to play 'silly buggers'!

Will report back tomorrow, and let y'all know how I've got on.

Cheers!

Mike.

---

### Post by Mike_Walsh on 2014-07-06
Hi, all.

Dog-tired; but can't sleep! SO.....

Have installed 'Boot Repair' to USB flashdrive with UNetbootin.

Restarted, booted from the flashdrive, and waited for 'Boot Repair' to come up. (is it based on the LXDE desktop from Lubuntu? It looks AWFULLY familiar...)

Waited while it settled down, clicked on the 'Recommended Repair' button, let it go through its arsenal, noted down the pastebin URL (just in case!).....and shut it down.

Rebooted, and *holds breath*.....wonder of wonders, GRUB2's back, and everything's all right with the world again; yay!!

NM5TF, that's a NEAT piece of kit, alright. Ubuntu boots, Zorin boots. GRUB2's behaving itself like nothing happened..! That's DEFINITELY going in my toolkit...for sure.

Thanks for that, Tommy! And thanks to everybody else for your advice...all much appreciated. I'll sleep soundly now!!

Cheers.

Mike.

ps Bashing-om; I suspect this thing probably does, automatically, more or less what you suggested! I know I said I was wary of using the terminal, but I've been using Linux for long enough now to at least recognise some of the script terminology, and I see where your suggestions were going. I know, I know, I'll never get the hang of the terminal if I don't actually use it... (!!)

---

### Post by yancek on 2014-07-06
> Having installed Zorin, I appear to have lost GRUB. 

You didn't lose Grub, you just have the Zorin Grub.  Zorin is derived from Ubuntu and also uses Grub2.  If I understood your initial post correctly, you installed Zorin and were able to boot it but did not have an entry in the Grub menu for Ubuntu.  That would be unusual but I guess it happens.  You could have booted Zorin, run:  sudo os-prober and the sudo update-grub and should then have had an entry for Ubuntu.  If you did and wanted the Ubuntu Grub for some reason, you could then have booted Ubuntu and run:  sudo grub-install /dev/sda.

---

### Post by Bucky Ball on 2014-07-07
> **yancek said:**
> You didn't lose Grub, you just have the Zorin Grub.

My thoughts exactly. 

Please mark thread as 'Solved' to help others by using Thread Tools at top right. Post new threads for any further issues.

And yes, Boot Repair rocks. ;)

---

