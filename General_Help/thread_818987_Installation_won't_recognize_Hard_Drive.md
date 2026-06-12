---
title: "Installation won't recognize Hard Drive"
date: 2008-06-04
forum: General Help
---

### Post by Avenger1432 on 2008-06-04
Ok,  so I just bought a geforce 8800 gt and a 500 gig hard drive and i installed and ran windows perfectly... then i tried to install ubuntu and it doesnt even detect my HD... in gparted or partition editor or anywhere within Ubuntu.

I tried Ubuntu 8.04 and 7.10...   7.10 didnt even get anywhere... the first time it tried to boot into liveCD and my computer started yelling at me (crazy beeping) so i shut it down and tried again and it said that it had to run in low graphics mode and didnt even go anywhere.  8.04 went in perfectly to LiveCD mode... but it just doesnt see a HD at all... 

Again, I feel like I am in the twilight zone...  HELP.. it is suppose to be Windows that has problems not Ubuntu!!

 Can anyone help??    pleeeeeassse



my computer specs are..

Abit Ip35 series motherboard
Intel Core 2 Duo 2.66 ghz E6750
2 gigs ddr2 memory
Geforce 8800 GT
500 gig Western Digital HD SATA
Memorex Lightscribe cd/dvd multi recorder
Nexus fan controllers (dont know if thats necessary, dont think so)

---

### Post by spiderbatdad on 2008-06-04
is it possible for you to boot into the live cd (in low graphics) and run```
cd Desktop
dmesg > dmesg.txt
```Right click that file and select 'create an archive."
Upload that archive here?

I'm assuming you have jumper settings correct on your new HD

---

### Post by cariboo on 2008-06-04
You have to set your bios setting to AHCI. here is a link on how to do it.

[http://forum.abit-usa.com/showthread.php?t=133222](http://forum.abit-usa.com/showthread.php?t=133222)

JIm

---

### Post by Avenger1432 on 2008-06-04
ok here it is..    and my jumper settings should be correct considering i can run vista perfectly on the HD.

---

### Post by Avenger1432 on 2008-06-05
Jim,  sry but how does that affect my SATA HD?? It is not an IDE HD.. or maybe it does.. but doesnt seem to make sense, since the only thing IDE is my DVD drive.

---

### Post by spiderbatdad on 2008-06-05
Interesting output message here...for google or launchpad perhaps:
> [  323.813342] program gparted is using a deprecated SCSI ioctl, please convert it to SG_IO

The other other suggestion I see from the kernel is:
> irq 20: nobody cared (try booting with the "irqpoll" option)
but I don't think that is related to the HD problem. I can't tell what interrupt is failing.

I suppose it's worth a shot. Also local apic is handling all events, so there are a couple of options I would try...If I were me.

Press F6 at the boot options screen of the live cd, and delete the end of the kernel line, where it says --quiet splash...or anything else after "ro."
Replace --quiet splash with irqpoll.

so you have: ro irqpoll

and boot. If the installation fails, repeat. This time try:

ro nolapic irqpoll

If that fails try:

ro noapic nolapic

Good Luck.
I think the low graphics problem cannot be solved until installation has succeeded and you install the restricted hardware driver.

---

### Post by Avenger1432 on 2008-06-05
the low graphics problem only occurs in 7.10...   sry didnt explain that very well. I will try what you suggested tho and hopefully that works.

Jim, I can't do the AHCI thing cuz when i download the storage drivers it says my computer doesnt meet minimum requirements...

---

### Post by Avenger1432 on 2008-06-05
yes, it worked...  the first line. I can now see the Hard Drive and installing right now.

Thankyou so much!!  I will update later if something goes wrong... thankyou again.

---

### Post by cariboo on 2008-06-05
When you connect sata drives and don't change the access to AHCI the drive is running in a sort of emulation mode.

Jim

---

### Post by Avenger1432 on 2008-06-05
ya but i replaced two  120 gig SATA HD's for one 500 gig...  my 2 120 gigs were working perfectly for both OS's vista and ubuntu.  Anyways still installing ubuntu and going to bed while it finishes...  

Thanks so much again...

---

### Post by kernalsanders123 on 2008-06-05
Hello all, I seem to have a similar, if not the very same, problem with the Hardy LiveCD:

[http://ubuntuforums.org/showthread.php?t=816500](http://ubuntuforums.org/showthread.php?t=816500)

But anyway, to sum it up, the CD boots fine for me, no graphics problems, except it won't recognize either of my SATA hard drives.

I have tried spiderbatdad's suggestions, but they didn't seem to work for me. However, it might be I'm doing something wrong. Just for clarification, spiderbatdad states:

> 
Press F6 at the boot options screen of the live cd, and delete the end of the kernel line, where it says --quiet splash...or anything else after "ro."
Replace --quiet splash with irqpoll.

However, when I'm under the LiveCDs boot menu, "ro" isn't among the boot options, so I tried deleting the end, which consisted of "quiet splash --" and replacing it with the 3 options that were suggested, however, all attempts failed.

So, my question is, am I doing it wrong, or might the source of my problem be something else?

Thanks in advance!

---

### Post by kernalsanders123 on 2008-06-18
bump?

---

