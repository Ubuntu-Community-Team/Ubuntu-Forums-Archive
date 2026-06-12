---
title: "Help Ubuntu, and Kubuntu won't boot"
date: 2007-04-13
forum: General Help
---

### Post by Atrio05 on 2007-04-13
:-k  ummm yeah i have a big problem none of my distro's i have installed will boot and i tryed booting a 6.06 live cd and it still frose in the boot process.

i think they are all freezing when they get to the "mounting root file system" part.

can someone please help me i really need this computer to work i have alot of important data on there!!  ](*,) 

:shock: :shock: :shock: :shock: :shock: :shock:

---

### Post by Atrio05 on 2007-04-13
someone please help this is really important!!

---

### Post by Atrio05 on 2007-04-13
come on people, some one help me!!! :mad:

---

### Post by Atrio05 on 2007-04-13
ok i am now able to boot up into knoppix so if there is anything you need me to post on here i can now post it. i really need a little advice on what i can do to fix my system. i didn't do anything special to it i just shutdown last night and went to turn it on today and bam it was freezing at the edgy loading screen along with the kubuntu loading screen and also i tryed the dapper live cd and the same thing happened to that. the only thing i've been able to boot up so far was knoppix.

:-( [COLOR="Red"]HELP!!!!!!![/COLOR] :-(

---

### Post by Atrio05 on 2007-04-13
bump!!! :D

---

### Post by daniel of sarnia on 2007-04-13
That is odd that the dapper cd would not boot, have you had this kind of trouble before.  What kind of video card is in your computer?

Did the knoppix cd boot on the first try?

---

### Post by Atrio05 on 2007-04-13
no i have never had any trouble like this before. i think my video card is an ATI Radeon 7000/VE, and yes the knoppix cd booted first try.

---

### Post by daniel of sarnia on 2007-04-13
Did you install ati's drivers or did you just use ubuntu with the free/open source drivers that it came with.

Also do you have another live ubuntu cd, all I can think of is that the ubuntu live cd you had was bad.

---

### Post by Atrio05 on 2007-04-13
no i used the free open source drivers i guess, and i'm not really concerned about getting the live cd to boot i really just want my system to boot up into ubuntu properly. i don't think the cd is bad either.

---

### Post by daniel of sarnia on 2007-04-13
You said that you think it stops when the disk is mounting, well ubuntu is set to do a disk check every 30 times it boots. It often takes a long time, are you able to reboot your computer hit the esc key when grub comes up and boot into recovery mood. If you manage that tell me what you see.

---

### Post by Atrio05 on 2007-04-13
ok i see a bunch of white text is there anything specific you want me to tell you?

---

### Post by daniel of sarnia on 2007-04-13
Yeah, just let all the text finish going by and when it's done it should either prompt you with a question (if it had a disk check error) Or it will prompted you with a root terminal something like ```
root@nameOfYourComputer:~# 
```. If the later type ```
startx
``` and tell me what you get.

---

### Post by Atrio05 on 2007-04-13
ok well then we have a problem as the last thing that printed to the screen is:

*[17179586.244000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 1*

thats the last thing on my screen there is a bunch of stuff above that about hda, hdb,hdd,hdc and basicly stuff about hard drives and cdroms and stuff.

---

### Post by Atrio05 on 2007-04-13
ok wow i feel like such a fool!! i had my jump drive plugged into the back of my computer last night and forgot about it. my computer never boots when it's plugged in as i think it's looking for a os on there and can't find it so it hangs. though i'm surprised i made it that far inti the boot process hmm.

well thanx for all the help ... well anyway thanx  umm wow i have no idea what to say except that a fell like such an idiot right now!!  ](*,)

---

### Post by daniel of sarnia on 2007-04-13
So you cannot even get to a command line? 

I googled the error and found this [https://launchpad.net/bugs/33716]("https://launchpad.net/bugs/33716") does that bug look anything like what you have? Some people on that bug post say it can happen from touchy hardware and out plugging in an odd usb device. The problem looks like it was resolved from a kernel upgrade that I think you already have, unless your horribly behind on them. To I really have not seen this before, maybe someone else here knows. If worst comes to worst, you can always back up your data with the knoppix cd. 

You might want to try checking the hardware, make sure nothing inside got bumped lose. Also check if that ubuntu cd is good. Their really is know explanation of why the ubuntu live disk could not boot and knoppix to be able to boot.

One thing I have seed before is a computer through out errors because of a somewhat faulty power supply that just one day started acting up. It would boot disks that were less cpu intensive and therefore would pull less wattage that the power supply could just barely still delivery without errors. But when trying to boot the more cpu and wattage intensive os it would lock up giving me a disk read error. 

That said, it is probably a kernel problem and a bad ubuntu cd. If it's a kernel problem I don't know what to do, but there are likely other people her that do.

---

### Post by daniel of sarnia on 2007-04-13
> **Atrio05 said:**
> ok wow i feel like such a fool!! i had my jump drive plugged into the back of my computer last night and forgot about it. my computer never boots when it's plugged in as i think it's looking for a os on there and can't find it so it hangs. though i'm surprised i made it that far inti the boot process hmm.

well thanx for all the help ... well anyway thanx  umm wow i have no idea what to say except that a fell like such an idiot right now!!  ](*,)

Ahhh that explains this [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/33716]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/33716")

---

