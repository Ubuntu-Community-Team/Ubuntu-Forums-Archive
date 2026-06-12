---
title: "trouble restoring desktop after flipping circuit breaker"
date: 2023-12-28
forum: General Help
---

### Post by jdchurchill on 2023-12-28
hi all
this morning i flipped the circuit breaker for my pc and on the restart it would only show a giant display of the upper right ish corner where the clock. so i've been tinkering away for a couple hours now i think i reinstalled lightdm and can get to a login screen - the problem is i put in the passwd and it goes to a black screen displaying
a single line of 
/dev/sba6:clean etc
for less than a second and then bounces back to the login screen
if i open a terminal using ctrl+alt+F1 i can login and sudo startx
it gets to a desktop but i cant see the left edge or the top 
running 16.04.7 LTS
please help tyia

---

### Post by ajgreeny on 2023-12-28
A few comments I must make before trying to solve your problem.

If you are not using the ESM system, you should update from 16.04 to a newer supported version. I would recommend 22.04 at the moment, supported until 2027. As you're using the 7th point release maybe you have enabled ESM already.

If that's the case you should boot to a live Ubuntu system, eg from a USB, and from that run ```
sudo e2fsck /dev/sdx#
``` on the root partition, where ***sdx#*** is the real device shortcut

---

### Post by jdchurchill on 2023-12-28
not using esm, and not sure how to enable it - i looked into it and it seemed like it cost money
tried to upgrade to 18.04 and it told me i had to update everything before i could upgrade, but apt-get update just shows the esm link again

---

### Post by ajgreeny on 2023-12-28
In that case you really must clean install a supported version as I suggested earlier; it is very unsafe for all of us who are online for you to keep using an unsupported version.

Backup all your personal files and then install a new version and finally restore your personal files.

---

### Post by jdchurchill on 2023-12-28
i cant backup any files though and i would hate to lose the files that are there

---

### Post by Rubi1200 on 2023-12-28
> **jdchurchill said:**
> i cant backup any files though and i would hate to lose the files that are there

Use a liveUSB with any recent version of Ubuntu to boot the computer. Choose to try not install and then recover/copy/save your files before following ajgreeny's advice.

---

### Post by #&amp;thj^% on 2023-12-28
> **Rubi1200 said:**
> Use a liveUSB with any recent version of Ubuntu to boot the computer. Choose to try not install and then recover/copy/save your files 
+1 just need a drive big enough to copy over to.

---

### Post by jdchurchill on 2023-12-28
thank you all for helping me i had to order a usb flaash drive should be here tmrw so i will likely continue to update this thread but thank you again

---

### Post by ActionParsnip on 2023-12-28
> **jdchurchill said:**
> i cant backup any files though and i would hate to lose the files that are there

Do you not have a backup? If you'd "hate to lose.those.files" you'd have a second copy somewhere... Right? If not then why not?

---

### Post by ajgreeny on 2023-12-29
> **ActionParsnip said:**
> Do you not have a backup? If you'd "hate to lose.those.files" you'd have a second copy somewhere... Right? If not then why not?
+1000!
It's only when you lose files that you realise how stupid you've been if they are not already backed up!!

And I speak from personal experience, even though it was about 18 years ago!

---

### Post by dragonfly41 on 2023-12-29
In a spectrum of risks I put this down to human failure. There is a principle of n+1 redundancy which should be learned.

---

### Post by jdchurchill on 2024-01-02
i have followed the directions for making a usb flash drive with ubuntu 22.04 iso image, but i can't figure out how to get it to boot from the flash drive. i got into BIOS but usb is not an option in the boot loader sequence

---

### Post by dragonfly41 on 2024-01-02
I assume that you have a working Ubuntu OS which you can use to create a LiveUSB. I'm not sure if you have a stable older US. Or even Windows but using Rufus instead of mkusb.

I have just gone through this process myself today.

Follow the instructions for mkusb and you should be good to go. Then when finished go to your BIOS at startup (F2 ?) to locate your new LiveUSB and place that at top of BIOS boot order.

Remember that mkusb uses dd and destroys content of target partition you select so since you have no backup take great care in choosing target installation. In my case my active (older) SSD's are in an external docking bay and I can power off to eliminate risk of installing into wrong partition of new SSD to hold fresh 22.04.

---

### Post by jdchurchill on 2024-01-02
i have been using another machine to interact here and create the flash drive - it's windows thus the rufus. i am almost completely sure i made the flash drive correctly. when i plug it into the machine i'm using to interact here it reads as ubuntu 22.04 etc, and when i plug the usb flash drive into the broken machine it lights up. but when i go into BIOS and try to toggle options in boot order i can't change anything. 

also i do want to recover some files before installing 22.04 but i am at a loss as to how to do anything at this point. i was thinking of taking out the cd/dvd drive so that is not an option in the boot loader cuz it's basicly useless and i don't think works - i can't get it to open. oof i flick one damn circuit breaker and then this whole debacle . . .

---

### Post by dragonfly41 on 2024-01-02
If you have Windows then one idea is to use Rufus to create **persistent storage** perhaps adding an NTFS format persistent partition in addition to the main Ubuntu ext4 partition. Then .. when you manage to get "Try Ubuntu" mode .. you should be able to see files in your old Ubuntu and copy to your Rufus Live USB persistent NTFS partition. Or you could create a Dropbox account to gradually pull out and backup important data. No doubt this is a long and tortuous exercise until you can get into another mode.  Try commands such as efibootmgr and inxi to inspect.  You can in BIOS add new boot opti ons and you might not have selected your flash boot to add to options.  I did start with Rufus since I have windows 10 on a    separate SSD but encountered some difficulty and switched to mkusb.  There is another option to  create a Ubuntu partition in your Windows HDD (as I do) but I would not go down that path just yet. 

Regarding the circuit breaker event just one event can cause failure.  This is why n+1 thinking is so important.

P.S. Another ploy I have used is to install R-Linux in Windows which allows Ubuntu files to be viewed inside Windows and captured.

And another card to play is using testdisk in Windows to recover files from external Ubuntu in an emergency. But again hold this in reserve since your issue is at the boot options stage. At that point in Boot options look for **add boot option**.

Final "get me out of gaol" card is to install rEFInd in your LiveUSB.

---

### Post by jdchurchill on 2024-01-02
i'm feeling a bit overwhelmed and done with this for today. thank you dragonfly for your replies, but i am super confused. to be clear i do have windows on the broken machine although it is xp and doesn't always boot when i select it against the ubuntu options. sometimes the machine just whirs for a bit and then beeps and nothing happens. i have resolved to sleep on this problem and take apart the machine when i'm caffeinated tmrw and hopefully resolve this.

---

### Post by MAFoElffen on 2024-01-03
Lets start from step one. How old is it? What brand and model of computer is it, that you cannot boot from USB? About 15 years old or so?

---

### Post by jdchurchill on 2024-01-03
i think i built the computer in 2011. it's amd athalon quadcore but i can't remember any other specifics off the top of my head. i have booted from usb before to get the linux os on there way back when. and when i've had problems troubleshooting and just reinstalled the ubuntu in 2019 - so i'm pretty sure i'm just missing something. i'm about to open up the case and dig around in there for a bit and remove the cd/dvd drive that doesn't seem to work and clean it up a bit.

---

### Post by jdchurchill on 2024-01-03
so i cleaned up the inside of the box and it's an msi motherboard. disconnected the dvd drive and powered it up - got into BIOS and don't know what i did cuz in advanced BIOS i selected boot 1 showing SATA etc disabled so i just hit some arrow keys and next thing i know boot1 and boot2 turned to usb etc so wtf save and exit and come to the screen to select ubuntu or recovery or the old windows xp which is sized correctly so i again wtf hit the top selection ubuntu and i get to the login screen again. tried the pw and it bounced me back to the login screen but this time ctrl alt f1 just went to the ubuntu logo with the dots underneath so i ctrl alt t and now i'm looking at a list of things the bottom of which has 
[*'s going back and forth] A start job is running for Hold until boot process finishes up (displays a timer counting up) 
- it's currently at 14min / no limit
so other than just waiting or pushing the power button/turning off the power source i don't know what to do.
so i have chosen to wait and see what happens - the usb drive is not blinking but it did light up red when the machine wasnt even turned on yet - don't know if that's of any significance

---

### Post by jdchurchill on 2024-01-04
i let the machine run for about 8h and nothing happened. so i turned off the power source and unplugged everything, and powered back on and bios was boot 1 usb boot 2 sata . . . exit and i got to the place where it's install or try ubuntu so i go into try and it looks the way i think it's supposed to do i do the 
[COLOR=#000000][FONT=&amp]sudo e2fsck /dev/sdx# 
to try and recover files? well i tried that in a terminal that was ubuntu@ubuntu and it came back command not found[/FONT][/COLOR]

---

### Post by MAFoElffen on 2024-01-04
Do
```

apt list e2fsprogs --installed

```
If it is not installed, then install it.

---

### Post by jdchurchill on 2024-01-05
when i do 
apt list e2fsprogs --installed 
Listing. . . Done
e2fsprogs/jammy-security,jammy-updates,now 1.46.5-2ubuntu1.1 amd64 [installed,automatic]
N: There is 1 additional version. Please use the '-a' switch to see it

---

### Post by jdchurchill on 2024-01-05
using the try ubuntu form from the usb flash drive on the desktop i am able to see the files i wanna keep but the desktop will not acknowledge another usb drive to move the files.

---

### Post by #&amp;thj^% on 2024-01-05
> **jdchurchill said:**
> using the try ubuntu form from the usb flash drive on the desktop i am able to see the files i wanna keep but the desktop will not acknowledge another usb drive to move the files.
How is the back-up USB drive formatted?

---

### Post by jdchurchill on 2024-01-05
**** it i used dropbox to move some files and i'm just gonna put the new ubuntu on there i'm tired of trying to deal with this

---

### Post by jdchurchill on 2024-01-05
the usb drive i was trying to move files to format? i don't know factory default i reckon

---

### Post by #&amp;thj^% on 2024-01-05
> **jdchurchill said:**
> the usb drive i was trying to move files to format? i don't know factory default i reckon

If it's factory UN-touched it's probably fat32 and that has problems transferring anything larger then 4gigs.
Gparted tool to convert to ext4 would be better.

---

