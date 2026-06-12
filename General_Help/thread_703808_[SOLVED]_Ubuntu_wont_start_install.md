---
title: "[SOLVED] Ubuntu wont start install"
date: 2008-02-21
forum: General Help
---

### Post by JimBuntu on 2008-02-21
I just built a new computer with abit an9 32x board and amd 64x2 5000+ and nvidia 8600gt oc card. Started her up, put the Ubuntu 64 disk in, and  it looked like it was starting. Then it went to the screen that says Ubuntu in the center with the start/install option. I press enter for the start/install and it shows a little loading kernal bar go to 100% then switches to a screen that says kernal alive or something, then my screen shows the "no signal" message and shuts off. I know people have been having problems with the nvidia drivers but has anyone figured this one out yet??

Also, how do i boot in recovery mode so that I can mess with the xorg? 

Please remember this is a fresh install on brand new hardware. What do i do???

Is it the 64 bit???

---

### Post by socceroos on 2008-02-21
Hmm, it does sound like a graphics problem.

Does your computer keep processing (like its continuing to load the ubuntu installer) when your screen says 'no signal'?

Also, do you recon you could get a more acurate reading of what the installer says just before your screen goes blank?

---

### Post by JimBuntu on 2008-02-22
Just before the screen goes blank, it says "kernel alive". And under that it says "kernel direct mapping tables" followed by a number. Just at that point it looks like its about to change to a different screen and then fades to black very quickly and then the screen says "no signal" and turns off.  I can hear my computer still on but not sure if it is still working like its trying to load anything. My best guess would be that maybe just as it goes blank it's calling for the graphics card to work and doesnt have the correct drivers. I am a total newb so that is completely a guess. I want to get this fixed as simple as possible. Ive read posts about disabling the splash screen, starting in recovery mode, starting in command line... Which one is the right one? And, I dont know how to do any of those things, so first off how do I start in command line mode, and when I do what do I type to get to set up xorg???

Sorry for the long post but Ive read and read and read, and no one post seems to be able to cure this problem. I know that there is a way to use the 64bit system with the 8600gt graphics card, there has got to be thousands of people doing so, so someone please post the correct way or lead me to the right post. 

Thank you all for your help...

---

### Post by u-foka on 2008-02-22
Do you try to use the AMD64 version, right?

What happens with the i386 cd?
If i't works, you may use it, there is only at maximum 10% difference with apps optimized well to amd64.

You can also try to go to advanced options at the boot menu, and remove the splash and quiet options, then you can see everything happening, and can found the problem.

If the problem stil not solved, please tell us, what's inside your computer ;)
And you can try to install a command line system with the alternate installation disc and the you can find what was wrong.

---

### Post by JimBuntu on 2008-02-22
I'm guessing the i386 is the 32 bit version?? I have not tried that one yet, but will. That is a good point about the 10% percent of programs that are optimized for 64 bit, is that right??? I always thought that 64 bit made everything better for some reason.

Anyways, you said that I could go to advanced at the boot menu and remove splash and quiet options, what exactly does that do, and how do I do that? 

Also, being that I am very new at this stuff, If I do remove splash and quiet options am I going to know what to do next? Or, am I going to look at the screen like a dear in headlights??

My system is an Abit An9 32x SLI , running AMD 5000+ Black version, and one BFG 8600GT OC.

---

### Post by u-foka on 2008-02-22
Well the one thing why people may need a 64 bit os, when they have more than 4gb memory what is impossible to use on 32 bit... I read test's where some apps runs slower on 64 bit, and they sad, maybe because the bigger memory adresses... btw, I tryed my core2 in 64 bit and I can't feel any difference, so I decided to don's suck with 64 bit, untill I really need that...

How I see your vga is an nvidia based one? then I think you don't need to worry about graphics, because nvidia makes one of the best supported cards for linux...

But I have problems too with usplash (the graphical loadin splash of ubuntu) on some lcd monitors... and when I disabled it, it solved my all problems...

So if it isn't work on 32bit you can disable usplash by pressing F6 at the boot screen, and delete "splash" from the appearing text field... And how I sad before, you can remove "quiet" too to have a detailed kernel log...

---

### Post by JimBuntu on 2008-02-22
THis may seem like a stupid question but what "boot screen" are you talking about? Are you talking about the Ubuntu Screen that has all the options on it? When I press F6 a line of wording comes up at the bottom saying:

Boot Options t=casper initrd=/casper/initrd.gz quiet splash

Do I delete the word splash or both "quiet splash"??

---

### Post by JimBuntu on 2008-02-22
just deleted the one word "splash" and hit install, then a screen came up saying that kernel alive thing at the bottom of the page, and Loading, please wait... at the top. Looks like its loading something cause its still on that page a few minutes later.

---

### Post by PmDematagoda on 2008-02-22
Delete the words "quiet" and "splash" then see where the Ubuntu Live CD stops loading and post it here.

---

### Post by JimBuntu on 2008-02-22
Just deleted the word splash and its definitely not loading anything. Its just hangin on the screen that says "Loading, please wait... and a cursor flashing under those words.

I'll try deleting both word and repost.

---

### Post by JimBuntu on 2008-02-22
Just deleted both words and hit install. The next screen showed a whole bunch of text. The bottom text its showing is:

[ 65.439346] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0
.60.
[ 65.564106] Floppy drive(s): fd0 is 1.44M


Those are the bottom two lines of text that it is hanging on. Also, I do not have a 3.5 inch floppy drive in my computer. Just a dvd/cd rom... I dont know if that makes any difference.

---

### Post by PmDematagoda on 2008-02-22
You may have better luck in installing Ubuntu using the Alternate CD, it can be found [here]("http://releases.ubuntu.com/7.10/").

The Alternate CD is the text-based installer for Ubuntu and would have better success. One thing though, after you install Ubuntu using the Alternate CD you would have to setup the X-Server manually but that is rather easy:).

---

### Post by u-foka on 2008-02-22
Well that not helps us to many :S

Joust one thing, if you enable the floppy in bios, it's does not care about it's really exists or not...

And have you made a try with a 32 bit cdrom?

---

### Post by JimBuntu on 2008-02-22
ok, just switched discs to the 32 bit version, deleted the words "quiet" and "splash" from F6 text at the boot screen, and I got a screen with a bunch of text  and the bottom couple say some stuff like:

[ 0.500000] ..MP-BIOS bug: 8254 timer not connected to IO-APIC
[ 0.500000] ..trying to set up timer (IRQ0) through the 8259A ... failed.
[ 0.500000] ..trying to set up timer as Virtual Wire IRQ... failed.
[ 0.500000] ..trying to set up timer as ExtINT IRQ... failed :(. 
[ 0.536000] ..Kernel panic - not syncing: IO-APIC + timer doesn't work! Boot w
ith apic=debug and send a report. Then try booting with the 'noapic' option

and a cursor is flashing repeatedly.

What is 'noapic' and how do I boot without it?

---

### Post by u-foka on 2008-02-22
Well let's do what your kernel sad :)

If you want to report that bug, and hope to be fixed sooner, you can enter "apic=debug" where you deleted the splash and quiet before, and then post the detailed log here: [https://bugs.launchpad.net/ubuntu](https://bugs.launchpad.net/ubuntu)

If you don't want to spend your time for that, or after you sent the report, you can try to enter "noapic" (but still remove splash and quiet to see what happening) and maybe you have some luck and can use your computer with ubuntu...

---

### Post by JimBuntu on 2008-02-22
Great News!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!

So, I deleted the words quite and splash, and my system was giving me the message listed above about the error with IO-APIC. It said to input 'noapic' and try to boot again. SO, I replaced the "quiet splash" with "noapic" and there it went loading everything. I did see it hang up on something listed as fd0 cdrom error or something but it kept on going and loaded everything and started up. My screen did show the great orange color and then said "no signal" and for a second there i thought it was screwed again, but i just moved the mouse and the orange came back up and right now I am looking at a beautiful brown Ubuntu screen. 

A Big thank you for the help. It is greatly appreciated!!!!!!!!!!!!!!!!!!!!11:guitar:

---

### Post by JimBuntu on 2008-02-22
Up and running! 

Ok, so now with much thought, here is the verdict. I first started off with a brand spanking new build. Abit an9 32x sli, AMD athlon 64x2 Black edition 5000+, BfG 8600GT OC 512mb, Seagate 320G sata hard drive, OCZ 2gig, ANTEC 650 watt trio. 

Put it all together. Stuck in the Ubuntu 7.10 64bit, and it did not work. It got up to the Ubuntu Splash and as soon as i clicked start/install, the screen went black. Then I read through a bunch of posts about similar problems. Found that by using the regular 32bit version disk I got a different error. With that disk I got to the splash screen and click install and it would try to load but then told me there was an IO-APIC error. The error screen told me to try booting with 'noapic'. SO, I restarted the computer, went back to the splash screen and hit F6. I deleted the last to words in that command line which were 'quiet splash' and replaced them with 'noapic'. Clicked install and boom, it worked. 

I dont think that deleting the 'quiet splash' was essential, but it let me see what the hell was going on during boot up. Also, I'd like to point out that it was difficult at first trying to figure out exactly which letters were being deleted in that command line since it ran off of my screen and there was no way for me to see it. However, with some careful counting I was able to get it right.

PROBLEMS: So, I still had a few problems to deal with. One was the screen resolution was automatically set way to low and everything was zoomed in really big. Another was after I updated everything including the nVidia drivers I had to restart. So, I restarted and boom, there was the exact same ERROR saying 'problem with the IO-APIC. So, I restarted and hit escape during the 4 seconds it gave me before grub load. That took me to a screen where I would edit the command line for the linux kernel (top one on list). Hit enter on that top one and followed the directions by pressing 'e' to edit and added 'noapic' after the words 'quiet splash', hit enter and then pressed 'b' for boot. It loaded up and everything worked. 

At this point I need to add, I have the infamous nvidia 8600gt that everyone says doesnt work, and yes it works. Not only did it work, but Ubuntu automatically told me to download the selected 3d nvidia drivers. 

CONCLUSION: Although there are still a few issues I have to deal with like figuring out how to permanently disable APIC, and a few other things, everything is up and running. All sound, and graphics work. The main thing to note here is that at first glance I thought just like everyone else that this entire issue was with the graphics card when in fact it was not. The main issue was the APIC. If anyone knows anything about this APIC and how to fix or deal with it please post...

Thank you to the Ubuntu Community.

---

### Post by u-foka on 2008-02-23
Hy!

To disable apic permanent, you need to edit /boot/grub/menu.lst open it with your favorite editor and find the line "#defoptions = "... and enter the kernel parameters you like to use, AND LEAVE IT COMMENTED OUT, because this part of the file not for grub iself, it tells debian's update-grub command the defaults for the real grub lines... When you saved the file, you need to run "sudo update-grub" in a terminal to apply your changes, and then you're done... If you reboot no need to "hack" grub every time :)

---

### Post by JimBuntu on 2008-02-24
Thanks man, great help. My comp is up and running perfectly...

---

