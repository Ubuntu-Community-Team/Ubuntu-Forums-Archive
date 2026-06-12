---
title: "Major Ooopsie -- can't log in"
date: 2023-07-16
forum: General Help
---

### Post by bill24 on 2023-07-16
I have used Ubuntu a fair bit in the past, on several different computers.  About 6 years ago I went through a bunch of life changes, moved, etc.  I dug out my Ubuntu machine, turned it on and see:

"Please unlock disk sda_crypt"

I have no idea what any login information I used back then, I have no idea how to get past that initial request for login credentials.

Anyone??

---

### Post by Rubi1200 on 2023-07-16
More experienced users will no doubt provide you with more information on this subject. But, what I do know is that if you used full disk encryption there is no way you can unlock it without the passphrase.

Did you write it down somewhere perhaps, can you try guessing the password based on passwords you know you used in the past?

Sorry I can't offer more than this.

---

### Post by ian-weisser on 2023-07-17
> **bill24 said:**
> "Please unlock disk sda_crypt"

That's not user login. That's asking for your encryption key. Very different.

The purpose of a login is to securely identify you to the system so you can interact with it.

The purpose of encryption is to deny all access (including non-interactive read access) to everybody in the universe who does not have the correct key.

There is no backdoor or bypass or "admin restore". Without the correct key, everything encrypted is gone.

---

### Post by bill24 on 2023-07-17
OK, this sounds terminal for the OS on the computer as is.  I did download the latest Ubuntu install version on a different PC and can write a DVD to install from.  Any suggestions how I might install the new software on the PC?  There must be some way.

---

### Post by ian-weisser on 2023-07-17
You simply boot the install media. Follow the prompts. The installer will happily destroy the encrypted system by overwriting it with a new, fresh system.

---

### Post by bill24 on 2023-07-20
That's what I thought.  How hard can that be.  I downloaded the most recent ISO, 4.55 GB and tried to write it to a DVD.  I was told that the file was too large to write to a 4.7 GB capacity DVD.  Two different PCs, two different disk writers and I got the same message.  OK, I can deal with that, I'd write the ISO to a thumb drive.  Two different empty 30GB thumb drives using two different PCs and I got the same message, the files was too large to write to the thumb drive.  Sometimes I just don't understand computers.

I tricked the thumb drive by opening the ISO and copying files 4 at a time to the thumb drive.  I moved all files, and checked to make sure I had all 4.55 GB and figured it should work.

I am trying to install Ubuntu on two different computers, one an older basic Lenovo and one a micro.  I figured it would be easier with the Lenovo so I booted that up (Mint Linux), mounted the thumb drive and figured that I would go to the "install" folder and click on something to start the process.  The install folder was empty.  Is that suppose to be empty?  I have downloaded the suggested ISO on two different PCs and I check, all the install folders are empty.

I then worked with the micro, the one that insists on using the special secret key I don't have.  I can open the terminal screen and did some research, presuming that if I had the appropriate script I could get it to unlock and allow a new version of Ubuntu to be loaded in.  I quickly learned that I don't have a clue what script to use and even if I did, I'm not sure that the ISO I have will work.

Are all flavors of Ubuntu with empty install folders??  Are any versions of Ubuntu easier to install than others?  Assuming I could get an installable ISO on a thumb drive could someone suggest the appropriate script to allow me to install Ubuntu on the micro via the terminal screen.

Anyone??

---

### Post by ian-weisser on 2023-07-20
> **bill24 said:**
> I can deal with that, I'd write the ISO to a thumb drive.  Two different empty 30GB thumb drives using two different PCs and I got the same message, the files was too large to write to the thumb drive.

Yes, it is too large...if you are trying to copy the file. Folks trying to copy the file are trying to take a shortcut.

> **bill24 said:**
>  I tricked the thumb drive by opening the ISO and copying files 4 at a time to the thumb drive.  I moved all files, and checked to make sure I had all 4.55 GB and figured it should work.

Another common shortcut that doesn't work.

Follow the instructions and make the LiveUSB properly. Then it works.

---

### Post by bill24 on 2023-07-23
I have created a bootable USB as per Ubuntu instructions, I plugged this into my micro computer, and launched.  I get nothing new, the same old "please use the magic key" to unlock the system.  Pushing any number of keys while attempting to reboot yields nothing.  I did get to GRUB via CONTROL-ALT-DELETE but nothing there seems to help, I am not fluent in Linux Terminal commands.

Is there some direct way of wiping the hard drive from the GRUB terminal window?  A totally fresh start would be nice.

I attempted to send this note yesterday, but something didn't work and I can't find it this AM.  If you did, sorry for the repeat.

---

### Post by Rubi1200 on 2023-07-23
I know this sounds a bit simple but did you change BIOS boot order to boot from this USB you created?

---

### Post by bill24 on 2023-07-24
That was the firt thing I tried, as per Ubuntu install suggestions.  I have held  ESC, F1 through F12 keys while starting this micro, then I held the ESC simultaneously with F1 through F12.  I've never seen the BIOS screen.  Is there any way to get to the BIOS screen from GRUB?

---

### Post by Rubi1200 on 2023-07-24
I'm not sure how much more help I can be here.

I have asked another forum member to take a look when he comes online so please be patient.

---

### Post by dragonfly41 on 2023-07-24
Try installing rEFInd alongside Grub.

---

### Post by bill24 on 2023-07-24
While I been able to get to the GRUB screen, nothing I type in there seems to have any impact.  I have been on line trying to learn a bit about GRUB and have attempted to launch things, but GRUB pretty much ignores them.  Having said that:

Where do I find rEFlnd and how do I install it "along side" GRUB?

---

### Post by oldfred on 2023-07-24
What brand, model system?
Can you download manual for system and review correct keys to get into UEFI/BIOS?
If in UEFI, you have set fast boot on, then you may not have time to press a key. It assumes no system change & immediately boots previous configuration.
You can often "cold" boot, or fully  power down, unplug & remove battery if laptop, hold power switch for 10 sec or so to drain any remaining power. My Dell manual calls it flea power which I have never heard before.
Then when powering up you have just a few seconds to press the correct key to get into UEFI, often f2 for system and f12 for boot menu, but check manual as various vendors use different keys. 

Microsoft listed some of the keys by vendor.
[https://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx](https://social.technet.microsoft.com/wiki/contents/articles/12911.tips-for-configuring-your-bios-settings-to-work-with-windows-to-go.aspx)

---

### Post by dragonfly41 on 2023-07-25
> **bill24 said:**
> 

Where do I find rEFlnd and how do I install it "along side" GRUB?

See example pulled from advanced search .. see top right of this forum page under eyeglass

[https://ubuntuforums.org/showthread.php?t=2486791&highlight=rEFInd](https://ubuntuforums.org/showthread.php?t=2486791&highlight=rEFInd)

Read OldFred's posts.

Or you can go to the horse's mouth
[http://www.rodsbooks.com/refind/](http://www.rodsbooks.com/refind/)


I have a Dell with multiple OS in dual (triple) boot options.
Since I also use Windows 10 I installed rEFInd in my Windows device.  But equally I can install rEFind in any partitions containing Ubuntu installation. So you can have multiple rEFInd installations or one.


In my current Ubuntu I launch Gparted to inspect my several devices.
I have three devices. the main device (an SSD replacing original HDD which came with Dell/OEM Windows 10)
/dev/sda1   Windows and Ubuntu
/dev/sda2    Ubuntu (current)
/dev/sda3    Data plus more space
Each device has boot, FAT, 500 MiB.


No Ubuntu in third device but because from LiveUSB + Gparted I always preconfigure new devices with boot 500 MiB space I can add Ubuntu later in third device.


So basically rEFInd can be installed in any of the three boot sessions.
I leave you to read how to install.
Your BIOS boot options (F2 at first sign of Dell logo) dictates which of the several devices are booted first.
So we have a tree of options.
First BIOS at bootup to select the installed boot sessions.
Second when rEFInd is chosen a GUI presents where you have yet further options. The configuration of this GUI is defined in refind.conf.


One problem I must admit I found with rEFInd GUI is that when I switched to Bluetooth Logitech keyboard (MX Keys) and mouse, of course Bluetooth does not kick in at the rEFIND GUI point. So I have to retain my old hard click keyboard next to me expressly for navigating rEFInd choices .. when I need to (such as switching to boot Windows. Usually I don't need to toggle the options and just wait a few seconds for autostart. After that I switch to Logitech keyboard remembering to use Bluetooth options 1, 2, 3 for Windows, Android, Ubuntu options.


Other than this annoyance (when I need to navigate the GUI choices) I always use rEFind GUI.

---

### Post by bill24 on 2023-07-26
Golly, lots of serious suggestions.  First off, please realize that I feel very much like a fish outta water, I'm about as far from computer geekdom as  you can get in a technical environment, I'm a glue chemist with an interest in digital stuff.  Please note that the micro computer I am dealing with is something I picked up from Amazon ~4 or so years ago.  It did not come with a manual nor an OS.  It came with a basic set on instructions of how to load either Windows or Linux.  I had a useable Ubuntu USB and installed that.  It worked like a champ until a bunch of life stuff happened and exploring Linux was a low priority.  Getting settled in again, I dug this system out, turned it on and was asked for a "key" I'd never heard of.

Exploring this brand I find that it is unique to Amazon.  They bragged about tech support, there isn't any save for this link I just found and have not yet explored:

  [SIZE=2][FONT=Times New Roman, Times, serif][https://www.amazon.com/stores/Vnopn/FAQ/page/83A1389C-2B3D-4CA6-95BC-3299F19A2CEC](https://www.amazon.com/stores/Vnopn/FAQ/page/83A1389C-2B3D-4CA6-95BC-3299F19A2CEC)

I will be going through the above information you folks were kind enough to offer and see what I can glean from it.

Bill[/FONT][/SIZE]

---

### Post by dragonfly41 on 2023-07-28
Let me share some experiments I play with using the latest thinking on AI assisted searching (not Google).

First do a bit of searching on your product. Capture key words, phrases (sans whoopsie) , ke sources / urls to search in*_ context._*

Start by loading url [https://phind.com](https://phind.com) into your browser.

Then craft in a separate note pad your precise questiion (AI / ChatGPT will be puzzled by "whoopsie" terms).

Now AI assistant questions if you have rights (password). I answered "yes" but the real answer is probably "no".


After all this, based on your stated profile,  you might consider buying a Raspberry Pi for experimenting.

I have a similar problem trying to bring to life a CanoScan LiDE 600F bought decades ago.

I learned by telcon (not AI) that it is a rare retro beast able to scan books and 35 mm slides.

So I plan now to build a Virtual Machine on Ubuntu with (I'm advised by Canon) Windows 7 (64bit) just to link to the scanner.

Improvisation.

_____________________________________________

ADDENDUM

After I tidied up the output format here are the questions I posed. I feel that this dialogue can be improved. I'm learning by experimenting. For example I targeted this forum in another experiment and focussed on key contributors. The subject was backup and recovery,


See Settings in phind.com

Your question to Phind.com:



**Explain to an amateur developer how to integrate with Ubuntu an external Mini PC purchased from Amazon some years ago.**
**Key words follow:**
**"Amazon"**
**"Vnopm&#8221;**
**&#8220;Amazon K6-F12 j4125 LAN Mini PC&#8221;**
**&#8220;K970-F12 N3700 N&#8221;**
**&#8220;K410-F12 J4125 4&#8221;**
[B]&#8220;K8-F12 Intel N3700 4x LAN&#8221;

[/B]
**Key sites follow:**
**[https://www.amazon.com/Fanless-Gigabit-Firewall-Appliance-Computer/dp/B09J4H9ZXY?ref_=ast_sto_dp](https://www.amazon.com/Fanless-Gigabit-Firewall-Appliance-Computer/dp/B09J4H9ZXY?ref_=ast_sto_dp)**
[B][https://www.amazon.com/stores/Vnopn/FAQ/page/83A1389C-2B3D-4CA6-95BC-3299F19A2CE](https://www.amazon.com/stores/Vnopn/FAQ/page/83A1389C-2B3D-4CA6-95BC-3299F19A2CE) 

Explain cause of this message "Please unlock disk sda_crypt".[/B]
**Explain further how to recover files from the Mini PC and then install Ubuntu.**

---

