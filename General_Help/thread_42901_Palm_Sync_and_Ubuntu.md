---
title: "Palm Sync and Ubuntu"
date: 2005-06-19
forum: General Help
---

### Post by purple_ghost on 2005-06-19
I have a:

Gateway 2000
Model: P5-166 MMD PENTIUM

Ship Date: 7/14/1997

144 Megabytes RAM

Intel 586 166-MHz PCI Motherboard With Integrated Video [Part #MBDSAC086AAWW]

Hard Drive  2.1 Gigabyte Hard Drive  IDE ST32122A

Mitsumi 12X/16X IDE CD-ROM Without Bezel [Part #5500408]

Panasonic 1.44MB Floppy Drive [Part #5500465]

104 Windows 95 Keyboard [Part #7000573]

Telepath for Windows with X2 Technology (Rabbit) [Part #6000639]

Ensoniq Audio PCI Wavetable Sound Card [Part #6000566]

BIOS  4L3TT0X0.15A.0007.P07

I had this Gateway 2000 Computer successfully running Windows 95B OSR2. 

I also have a Micron computer with a 300 Megahertz Celeron, 96 MB RAM, 4.0 Gigabyte Hard Drive, Windows 95B and is my internet connection.   

Using Ubuntu on the Gateway 2000.
Error Message:  ACPI unable to locate RSDP
Using the Micron to internet research this, I used BIOS and turned the CPU fan to 'always on', as opposed to 'sometimes on.'

  My reading implies that the message does not apply to the Gateway 2000.  I do not know whether Windows 95 ever had anything to do with the fan either.

Did I do the right thing in setting the BIOS to fan always on?

I intend to use this computer to Hot-Sync to a Palm Zire 21.  

I have used the Gateway 2000 with a Simply Mepis 3.3.1 (KDE) to sync to my Palm and place an ebook on it, backup files from Palm.   Then I used a friends Windows 2000 and the Palm Desktop program to install a Keyboard driver (for a Stowaway Portable keyboard, also the program Wordsmith.   The next time I tried to sync my Palm via the Simply Mepis KDE Palm program.   The Palm crashed hard.  I had to do a Hard Reset to get my Palm to respond again.   Simply Mepis KDE restored most of the information on the Palm.   It did not restore any programs.  Not the fundamental Palm Reader,  or Wordsmith, or the Keyboard.   I am aware that there is a Linux version of Wordsmith which is supposed to work with Red Hat.   

I am guessing that Palm programs (on the Palm itself) which are configured to work with Windows will always be a problem for Linux.  Does anyone have any experience with the subject of Palms and Ubuntu.  Yes, I am aware there is some rigamarole which I need to additional do to get my Palm to Sync with Ubuntu.   I have not tried that.  I am guessing that even after I do those things.  My programs will not stay installed or back up, or restore.    

I think I might try to install Wine on the Gateway 2000, Ubuntu 5.04 to further install the original Windows based Palm Desktop programs (which do the Windows based Hotsync.) 

I might try to install KDE onto Ubuntu in order to use its Palm Pilot program.  At least their program was installed ready to run, unlike the Gnome version.

  Before I spend a lot of time trying to install and try all of these things.  Has anyone else any experience using Palm Syncs with Ubuntu?    Which is the option that will work with Ubuntu and the Palm Sync?

---

### Post by rider343 on 2005-06-19
My Palm work fine, I use usb port...

---

### Post by dwanders on 2005-06-21
I have a Palm Zire 21. And have had very little success in sync. It was also a bit hard to try and find the commands to interact with the Palm (IMO). I am currently downloading the latest version of Ubuntu and plan on rebuilding my computer with the latest release and trying again. I will let you know my results in the end if you want.

---

### Post by purple_ghost on 2005-06-21
Thanks to both of you for replying.

Rider343:  Please a little detail.  Which version of Ubuntu?  Which Palm do you Sync with?  Did you do anything else from freshly installed Ubuntu to get it to work?     Have you loaded programs onto your Palm?  Even the Palm Reader provided by Palm?


dwanders:  FYI.  I think I am using the latest version of Ubuntu.  In my email I referred to rigamarole.   What I was referring to ---  If you search this forum for Palm.  About three pages in, I found some others who had this same difficulty synching between Ubuntu and a Palm.   They have some kind of thing to 'type in' which they say facilitates Synching.   However.  As I am new to Linux, I am not sure where I am supposed to be entering things.   For me is a bigger issue.  I do not sorta want to synch with my ebook files and standard Palm addressbook, To Do lists, Memo.  

   I want to install programs onto my Palm.   Kpilot would install ebooks, back up the basic Palm stuff.  Kpilot would not install programs onto the Palm.

  Personally.  I do not want to spend many hours more trying to get Linux programs to work.  As nearly i can tell.  The Palm program for Gnome is an orphan.  The program does not have full time programmers trying to make it work.  (Still, Thanks to you Linux guys who gave up your time trying to get Palm Gnome to where it is though.   I am sure it is not a little thing to try to get applications like this to work.)   I suspect that part of my problem must be that my older hardware does not handle USB ports like the newer hardware.  Meaning (I am hypothesizing) whomever tested the Palm program did it on a later model hardware (computer), where the Ubbuntu 5.04 Gnome Palm program worked exactly as it was installed on Ubuntu 5.04.   

  I saw a note somewhere that part of the deal with Synching to a Palm with Linux is that every time you Synch:   Linux reads the entire Palm.  As it ends, Linux will rewrite everything back onto the Palm.  My hunch is;  So if Linux does not install programs.  It will clobber the Palm.   Windows does not work this way.

   The Windows based Palm desktop programs work easily, intuitively.  (I am gagging - typing something nice about Windows.   Just a moment, I have to go and disinfect my fingers with alcohol).   Burned.  But that is better.  My thought is to install Wine.   Then use the Windows based palm programs.   I really wish to hear someone who uses Wine who can tell me if they have extensively used Wine with the Palm programs?  Does this configuration directly work without a lot of typing intervention.    Does Wine and Palm work at all?

  Linux users seem to have a lot of affection for typing extra commands in.  I want to use my computer, not spend hours fiddling with the Operating System.   For me to install Wine I would either have to download it, or try to slip it off another distro (which I would have to buy).   Sourceforge (which has the Wine download, likes to crash a lot during download.   I am not sure that the download manager in Firefox (for Windows 95B) is going to get a clean copy.   I can not get online with my Linux computer (Winmodem problems).  So I will have to find a way to use my Windows 95 computer to create a spanned floppy set of Wine for the Linux computer.    I only have Ubuntu CD which installs, not live CD.  (I thought I was both)  So it would take a lot time for me to test if  Wine and the Windows Palm desktop will cooperate.   I am tempted to wait until next month when I have money and buy an external serial modem.   Some distros like Kbuntu, Knoppix, live CD of Ubuntu.   Then try working on this.   If any of you has an easier way for me to test this without my spending more money, then let me know.   

  Anyway, Please let me know what you find out.

---

