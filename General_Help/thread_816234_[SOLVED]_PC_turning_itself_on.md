---
title: "[SOLVED] PC turning itself on"
date: 2008-06-02
forum: General Help
---

### Post by Jeztastic on 2008-06-02
Hi there.

My PC keeps turning itself on. By which I mean, it won't stay turned off, the only way it will stay turned off is if I pull the plug out. This only happens with a new PCI wireless card in it.

Any ideas?

Thanks

---

### Post by ibuclaw on 2008-06-02
Lol, wow.
Last time that happened to me it was a 10 year old machine that had been laying dormant for 3 years. :)

As my understanding of hardware goes, when your PC is "**off**"... it **isn't really **"**off**" as there is still electricity from the mains still giving power to the motherboard and monitor (not full power, of course. Say 0.1W of energy), but never using it until you send the signal for it to boot up.

In general, self-booting of a PC is most likely caused by a serious short-circuit (that seems like its caused by your PCI card, as you mentioned above), where the signal is triggered indirectly, but triggered nonetheless.

If you have another PCI slot, try using that one instead.

Regards
Iain

---

### Post by ibuclaw on 2008-06-02
Just to double check if this is a hardware problem, though.

Save all your work and logout. Then press these key combos on your keyboard:
```

Alt+PrintScreen+R
Alt+PrintScreen+S
Alt+PrintScreen+E
Alt+PrintScreen+I
Alt+PrintScreen+U
Alt+PrintScreen+B

```
What it does is:
Take over keyboard control, writes all memory data to cache, ends all running apps, kills all remaining apps, remounts all mounted filesystems and shutdowns down your PC.

If it continues to reboot after this, then it is most definately a hardware problem.

Regards
Iain

[EDIT]
These are what we call Magic SysRq Functions.
They send signals to the kernel with immediate effect.

For more information, [read here]("http://ubuntuforums.org/showthread.php?t=617349")

---

### Post by bingoUV on 2008-06-02
It has happened to me. I say it is a BIOS bug, but motherboard manufacturer (ASUS) is not ready to accept it. 

What I had done was, in my APM settings in BIOS, selected the PC to start on a specific date and time, in a specific year. That date and time does not come everyday, but my PC started on its own almost everyday. It did this whether in suspend mode, hibernate mode or switched off. I had made the setting just as an experiment to test whether this feature works or not. Needless to say, it did not start at the selected moment in any imaginable time zone. I tested with UTC, GMT and my own time zone. I forgot to remove the setting, so faced this auto boot at random.

After disabling this automatic boot, my PC is behaving fine.

---

### Post by Jeztastic on 2008-06-03
Hi! Thanks for the replies, I am pretty sure it is a hardware problem. I will try a different PC slot, and also check the BIOS settings. So far, it is only happening with this wireless card!

---

### Post by optique on 2008-06-03
I have a win pc that turns itself on. In my case, I believe it has something to do with the wired NIC I have. 

I will have to double check, but I believe it happens when another pc on my network boots up, that pc boots up too. 

the win pc is a Tyan motherboard, I belive, but I am at work.

What would happen if the booting pc had linux on it...I don't know.   

Steve.

---

### Post by Jeztastic on 2008-06-03
I'm pretty sure it's got nothing to do with the software. It all happens way before even GRUB kicks in.

---

### Post by ChameleonDave on 2008-06-03
You can probably fix this by playing with your BIOS settings.

My motherboard (via the BIOS) is set up so that the computer switches on when I type in my password.  I could also make it switch on when I click the mouse.  Or when it receives a call via the modem, etc.

If it refuses to turn off in the BIOS, then you could try a firmware upgrade.  If that doesn't work, then your motherboard is physically damaged.

---

### Post by wpshooter on 2008-06-03
> **Jeztastic said:**
> Hi! Thanks for the replies, I am pretty sure it is a hardware problem. I will try a different PC slot, and also check the BIOS settings. So far, it is only happening with this wireless card!

Jez:

More likely than not, there are some parameters in your BIOS which allows the computer to be booted according the the status of certain hardware devices, i.e. keyboards, mouse, etc., etc.

If you can find this section just disable to booting process for your network card and you should be good to go.

P.S. - While you are at it, you might want to consider updating your BIOS to the latest version, if you have not already done so.

Good luck.

---

### Post by Jeztastic on 2008-06-03
Why would this only happen with this one card though? Others are fine. 

I am tempted to return and ask for a refund, as the seller has some crappy "return withing 7 days" rule. 

Do you think I should, or is the concensus that it's a BIOS problem?

---

### Post by Kinnza on 2008-06-03
Well im having the same problem
it only happands when the computer is at sleep mode 
i used to think its a win XP prob, cause i used to have vista, it totatly sucked, so i put winXP and i think some of the drivers werent installed correctly.
now i totaly gave up on windows and this prob happands on linux too... so im pretty sure its a hardware thingie (although it happands ALOT less)

when i used winXP/vista i had alot of probs with my wireless so i used to think that caused it... but here those probs (wireless) are pretty much gone... so taht theory goes to waste too

i also tried to update the bios and it totaly screwed up my system, i had to use system restore to remove it

---

### Post by mcduck on 2008-06-03
You'd better check the BIOS setting before you do anything else..

If the problem can be solved simply by disabling some option in BIOS it wouldn't make much sense to return the card. ;)

---

### Post by bingoUV on 2008-06-03
It could be a combination of BIOS bug and card bug. The card could be sending a particular signal to all as soon as it is powered on. The motherboard unfortunately wakes up at this signal.

Return the card and get another one if possible.

---

### Post by cariboo on 2008-06-03
Check the wake-on-lan setting in your bios, make sure it is turned off and that should clear up your problem.

JIm

---

### Post by Shazaam on 2008-06-03
Laptop? Still running Ubuntu via WUBI? Start Windows, find your card in Device Manager and check to see if "Allow this device to start/power on/off computer" (or similar) is checked. And +1 for checking your bios settings under Power Management.

---

### Post by Kinnza on 2008-06-04
ok i have nothing related to power managment in the bios
i will check the windows drivers thingie too

---

### Post by lisati on 2008-06-04
You might want to check the BIOS for a "Wake up on LAN" setting or similar. When my desktop is in "sleep" mode and I'm surfing on my laptop, this makes my desktop wake up again.

---

### Post by Kinnza on 2008-06-04
like i said there is no such option in the bios

---

### Post by wpshooter on 2008-06-04
> **Kinnza said:**
> like i said there is no such option in the bios

Are you sure that you have looked real good, sometimes these boot on device status BIOS options are hidden several layers/menus down in the BIOS settings.

Unless the computer is fairly old, it is likely that it has these type of settings.

---

### Post by Kinnza on 2008-06-04
yeah i looked pretty good
there isnt much in the bios really
i will look again

---

### Post by Jeztastic on 2008-06-05
The guy who sold it to me has emailed and said that this happened with another customer - he reckons it is a incompatibilty between the card and the motherboard, so he is sending me a equivilent card of a different make.

---

### Post by Jeztastic on 2008-06-05
> **Shazaam said:**
> Laptop? Still running Ubuntu via WUBI? Start Windows, find your card in Device Manager and check to see if "Allow this device to start/power on/off computer" (or similar) is checked. And +1 for checking your bios settings under Power Management.

Yes, but the problem is with the server, which is only running Ubuntu at the moment.

Is there an easy way to migrate from Wubi to a dual-boot without losing my settings? I would like to do that sometime.

---

### Post by ibuclaw on 2008-06-07
Most efficient way, you'll need an external hard-drive to backup the files to.

1) Copy the contents of your Home directory to the backup-drive in an isolated folder. (Visible files only, not the hidden ones).

2) Copy your apt-sources settings to the backup-drive (/etc/apt folder)

3) Store the list of installed apps on Wubi to a file
```
dpkg -l | awk '{if ($1 == "ii") print $2" "}' | tr -d "\n" >~/Desktop/packages
```
Then copy the new "packages" file on your Desktop to the backup-drive.

4) Unistall Wubi and defrag your computer (in Windows).

5) Insert Ubuntu LiveCD and reboot to run the Hard-Disk installer.

6) Once you've finished the installation, and logged into your New Ubuntu Install, restore the backed up files to their designated locations.

Note: With the /etc/apt folder, you'll need to be root.
Run```
gksu nautilus "$PWD"
``` to open up nautilus as root.

7) To reinstall you're old packages, copy the "packages" file to your Desktop and run
```
gksu apt-get install $(cat ~/Desktop/packages)
```

A reboot may be required after this, but you're computer should be more or less the same as you left your Wubi install as (minus your personal desktop configurations).


Regards
Iain

---

### Post by Jeztastic on 2008-06-07
Hey, thanks! I will try this as soon as I get the time - not one to rush. I am going to try and change Vista to XP as well. Wish me luck.

---

### Post by Jeztastic on 2008-06-09
Just as a follow up, the new card works perfectly. It may have been an incompatibility or a faulty card. If you have a compaq deskpro PIII, beware of buying a sitecom wireless g. If fact, beware anyway, as it may have been a faulty unit. I will try it in another PC soon and report back.

---

