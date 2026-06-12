---
title: "i need help! My computer just started to boot to memtest and cant get out"
date: 2024-03-08
forum: General Help
---

### Post by xrtc21 on 2024-03-08
Im still new here to this forum so if i put this thread in wrong section on this forum i am sorry i didnt know where to write this.

I dont know what to do.everytime i start my computer it just goes in to memtest. and i even have done the regularly test that took about 6 hours and i have even tried the fail safe mode and the multi test and when  its done it still goes in to memtest i dont know what to do to get out of here. 

So i thought i would do a hail Mary and ask you experts to try to help me.

My OS is Xubuntu 22.04 

Its a laptop - Acer emachines E6

I have been taking screen pictures with my phone i hope will help me. 

Im new to this forum still so i dont know what info you will need but just ask and i will give you all info i can get.



[[img]https://i.ibb.co/QNBmZgv/IMG-20240308-145924729.jpg[/img]](https://ibb.co/Hzvg0ST)



[[img]https://i.ibb.co/BPYDPMN/IMG-20240308-144033676-1.jpg[/img]](https://ibb.co/YWV9WsZ)

[[img]https://i.ibb.co/4fH2df4/2024-03-0817-08-592705086806803801793.jpg[/img]](https://ibb.co/qnvC5nm)

---

### Post by xrtc21 on 2024-03-08
I dont know what to do and l would really appreciate all the help and input i can get.

---

### Post by yancek on 2024-03-08
Did your install of Xubuntu ever boot successfully?  If you have booted the installation successfully, what changes if any did you make?  How old is your hardware?   Is Xubuntu the only OS installed?  Can you boot the USB device you used to install Xubuntu?

---

### Post by dragonfly41 on 2024-03-08
I might be barking up the wrong tree but the clue "err = 00000024"  points to a Windows error.

[https://recoverit.wondershare.com/computer-problems/fix-blue-screen-error-0x00000024.html](https://recoverit.wondershare.com/computer-problems/fix-blue-screen-error-0x00000024.html)

Is Windows still lurking around in dual boot mode?

---

### Post by xrtc21 on 2024-03-08
Yes the installation was no problem im not new to Linux ive tried some different distros mostly xubuntu and lubuntu because my laptop is about 10 years old 
There was no dual OS i just had xubuntu installed

---

### Post by xrtc21 on 2024-03-08
Yeah that is really confusing i google that too and i dont get it because this is a new SSD i bought for a few months ago.

The thing is that this laptop is originally a windows computer that i installed Linux distro on the new SSD

---

### Post by xrtc21 on 2024-03-08
Alright after looking around my place i found a usb drive with Linux live and it worked !! I got in and im doing a timeshift backup right now i think in good now.

Uppdated 
I just did a backup and it worked and im back in and it seems to be working and no problem.

I feel pretty stupid for making this thread now and i cant seems to delete it so 

Thanks guys for your input and i really appreciate it :)

---

### Post by Bashing-om on 2024-03-08
xrtc21
\o/

Great that you have restoration -
Appreciate that you gave the update and your solution.
> 
this thread now and i cant seems to delete it so


Instead of deleting the thread - mark it as "solved" for the edification of others. Good backups are good to have :D
Howto:
[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

[INDENT]keep right on keep'n on
[/INDENT]

---

### Post by xrtc21 on 2024-03-09
Well im not sure this thread will be much help to anyone 

I am curious about what dragonfly41 wrote tho. When i Google this problem it just came up windows just like what he wrote. 
I dont understand that, it may be a Windows laptop from start but i installed Linux on a new SSD i had bought. 
So why do i have windows boot setup?

---

### Post by Rubi1200 on 2024-03-09
Without seeing the output from the boot info script, I would be just guessing.

However, it is possible that when Ubuntu installed it did not remove the Windows boot partition. I suppose that might explain what you saw.

---

### Post by xrtc21 on 2024-03-09
......

---

### Post by xrtc21 on 2024-03-09
i have done the system info script and i uploaded the file here[URL="https://file.io/QvpqhIbipQA9"][COLOR=#000000][FONT=inter]
[/FONT][/COLOR][/URL]
[https://paste.ubuntu.com/p/mTxr252yH3/](https://paste.ubuntu.com/p/mTxr252yH3/)

---

### Post by xrtc21 on 2024-03-09
.....

---

### Post by dragonfly41 on 2024-03-09
Once you are in the Try Ubuntu session check if you have GParted (Partition Editor) installed (otherwise install).

You can then run GParted to scrutinise all your partitions.

---

### Post by xrtc21 on 2024-03-09
> **dragonfly41 said:**
> Once you are in the Try Ubuntu session check if you have GParted (Partition Editor) installed (otherwise install).

You can then run GParted to scrutinise all your partitions.


I dont understand... why should i do this?

---

### Post by dragonfly41 on 2024-03-09
To look for partitions with boot flags. Unless you invest time in reading about GParted (before using) and learn you may as well forget about it.

---

### Post by xrtc21 on 2024-03-09
> **Rubi1200 said:**
> Without seeing the output from the boot info script, I would be just guessing.

However, it is possible that when Ubuntu installed it did not remove the Windows boot partition. I suppose that might explain what you saw.


Here it is for you i have done it both :)

But i should mention that i did the boot system info on a Linux live usb flashdrive with xubuntu on it 

the boot system info 
Its uploaded here 

[https://paste.ubuntu.com/p/NWv48V2Xn4/](https://paste.ubuntu.com/p/NWv48V2Xn4/)

And the system info i didnt do it on a Linux live usb Flash drive. If that was wrong i will do it in Linux live usb Flash drive if thats necessary 

And here is the system info

[https://paste.ubuntu.com/p/mTxr252yH3/](https://paste.ubuntu.com/p/mTxr252yH3/)

---

### Post by xrtc21 on 2024-03-09
> **dragonfly41 said:**
> To look for partitions with boot flags. Unless you invest time in reading about GParted (before using) and learn you may as well forget about it.

Do i have to do that in Linux live ?

---

### Post by dragonfly41 on 2024-03-09
Why should I have to trawl through this?
It is easier shown in GParted.
But viewing bootinfo report .. the clues are there.
Bottom line:
“ The current session is in BIOS-compatibility mode. Please disable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD [COLOR=#666666]([/COLOR]or live-USB[COLOR=#666666])[/COLOR] that is compatible with UEFI booting mode. For example, use a live-USB of Boot-Repair-Disk-64bit [COLOR=#666666]([/COLOR]www.sourceforge.net/p/boot-repair-cd[COLOR=#666666])[/COLOR], after making sure your BIOS is [COLOR=#aa22ff]set[/COLOR] up to boot USB in EFI mode. This will [COLOR=#aa22ff]enable[/COLOR] this feature.”
“You may want to retry after changing it to UEFI mode”.

Recap:
Why is there reference to “[COLOR=#bb4444]Microsoft basic data[/COLOR]” if as you wrote this is Windows free?
Post #1 "Its a laptop - Acer emachines E6."
Post #5 “There was no dual OS i just had xubuntu installed”
Post #6 “The thing is that this laptop is originally a windows computer that i installed Linux distro on the new SSD”
Post #7 “Alright after looking around my place i found a usb drive with Linux live and it worked !! ”
Post #9 "I dont understand that, it may be a Windows laptop from start but i installed Linux on a new SSD i had bought.
So why do i have windows boot setup?"


My suspicion is that the “new” SSD you bought was not a virgin SSD. Did you buy this from a manufacturer?


Finally all the clues point to you being in Legacy mode (Acer going back 10 years) and not in UEFI mode.


Researching "Acer emachines E6":-
[https://winraid.level1techs.com/t/bios-unlock-and-maybe-uefi-support-if-its-possible/34052/3](https://winraid.level1techs.com/t/bios-unlock-and-maybe-uefi-support-if-its-possible/34052/3)
[https://bbs.archlinux.org/viewtopic.php?id=283930](https://bbs.archlinux.org/viewtopic.php?id=283930)


You might need a more modern notebook and cut your losses.
Or study this thread.
[https://ubuntuforums.org/showthread.php?t=2130640](https://ubuntuforums.org/showthread.php?t=2130640)

---

### Post by xrtc21 on 2024-03-09
Damn i have been worried about just what you wrote but i waswnt sure. About that UEFI but i never really know what to do. 

Thanks. I really appreciate the input i will look it up right now.

Yeah i dont understand all that what it said in the boot. Info report 

I feel like im still new to Linux even after i started with Linux about a year ago. There is so much information to read and know im still reading about all kind of stuff.

That about UEFI you wrote sounded very complicated but i will try to figure it out

About the new SSD.. i bought on Amazon and it suppose to be new.

Its a 
 Kingston
Kingston SSDNow Halvledardrivenhet, 240 GB, 2,5 tum

But i was stupid enough to not read more about it before buying it. I have google it and there is no support for Linux or firmware for Kingsdom

---

### Post by xrtc21 on 2024-03-09
Well about the UEFI your wrote. I dont really understand what i am gonna do. That sounds very complicated 

" The current session is in BIOS-compatibility mode. Please disable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD (or live-USB) that is compatible with UEFI booting mode. For example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd](www.sourceforge.net/p/boot-repair-cd)), after making sure your BIOS is set up to boot USB in EFI mode. This will enable this feature." "You may want to retry after changing it to UEFI mode".

---

### Post by xrtc21 on 2024-03-09
That boot repair cd software sounds very complicated. Software like that can break a computer esdy

Ah thanks for the links dragonfly41 i am reading about that last link you wrote. Very interesting its keeping me busy very much to read xD

---

### Post by dragonfly41 on 2024-03-09
[Narrow down your studies. ]("https://ubuntuforums.org/search.php?searchid=32824444")

---

### Post by xrtc21 on 2024-03-09
Could you give more information about the UEFI thing. 
 give more information about this
 UEFIThe current session is in BIOS-compatibility mode. Please disable BIOS-compatibility/CSM/Legacy mode in your UEFI firmware, and use this software from a live-CD (or live-USB) that is compatible with UEFI booting mode. For example, use a live-USB of Boot-Repair-Disk-64bit ([www.sourceforge.net/p/boot-repair-cd](www.sourceforge.net/p/boot-repair-cd)), after making sure your BIOS is set up to boot USB in EFI mode. This will enable this feature.&#8221;
&#8220;You may want to retry after changing it to UEFI mode&#8221;.

---

### Post by xrtc21 on 2024-03-09
And btw that link yulou wrote dont work

---

### Post by dragonfly41 on 2024-03-09
"UEFI thing".
The link I posted (drawing on search features in forum) works fine for me.
Pehaps I'm getting old but I find it much easier to contribute to discussions by pointing to Phind.com in your browser then pasting in a succinctly crafted "prompt".

> Explain to a user who has a 10 year old Acer emachines E6 notebook the importance of UEFI when installing modern day Ubuntu or Xubuntu OS. Can this legacy notebook in fact install latest Xubuntu?.

A new AI skill to learn.

---

### Post by xrtc21 on 2024-03-09
Alright i see. I usually dont register or write on forums sites.

Yeah well in that last link you send before... There was a test to write many things in the terminal and what it looks like i should be able to run xubuntu 

So i have just downloaded the boot repair disk iso file and gonna burn it to a usb Flash drive soon
What i read that software can fix my UEFI EFI problem som im gonna try that soon. And hope for the best 

PS: i should mention that English aint my first language. Im from Sweden :)

---

### Post by xrtc21 on 2024-03-09
I am just confused about it said "use a live usb of boot repair disk ....... (after making sure your bios is set up to boot usb in EFI mode) Its this i dont understandm jö

---

### Post by oldfred on 2024-03-09
I always suggest using your Ubuntu or in your case Xubuntu live  installer and add the ppa per the second set of instructions. The ISO can be used, but is not updated as often and better to use latest version.
Boot-Repair's main fix is reinstall of grub or update of grub menu. 
But report and show other boot issues or sometimes other issues. Best to see report before you make any changes with Boot-Repair.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Do you have latest UEFI/BIOS?
Many Acer models have needed latest UEFI/BIOS firmware.

Some older links, but most details should apply as Acer issues are common across many models.
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)

Acer is unique in requiring "trust" on "ubuntu" entry in UEFI settings.
Acer Very latest UEFI/BIOS works, downgrade not required if no trust screens, you must now upgrade:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044) & 
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)

Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 

Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

---

### Post by dragonfly41 on 2024-03-09
The answer to earlier prompt .. requested in Swedish ..

[COLOR=#1B1642][FONT=&quot]Att förstå UEFI (Unified Extensible Firmware Interface) är viktigt när du installerar moderna operativsystem som Ubuntu eller Xubuntu, speciellt på äldre hårdvara som en 10 år gammal Acer emachines E6 notebook. UEFI är efterträdaren till det traditionella BIOS och erbjuder flera fördelar, inklusive snabbare starttider och stöd för större hårddiskar. Eftersom din bärbara dator sannolikt använder det traditionella BIOS, kan det finnas kompatibilitetsproblem när du försöker installera en ny version av Ubuntu eller Xubuntu som är optimerad för UEFI.
[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&quot]Din gamla Acer notebook kan fortfarande installera den senaste versionen av Xubuntu, men du kan behöva utföra några extra steg för att göra den kompatibel:
[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&quot]
[LIST]
[*]Skapa en startbar USB: Använd ett verktyg som Rufus för att skapa en startbar USB-enhet. Se till att välja alternativet för att skapa en USB-enhet som är kompatibel med både UEFI och BIOS (Legacy).
[/LIST]
[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&quot]
[LIST]
[*]Inaktivera Secure Boot: Om din bärbara dator har ett UEFI-firmware med Secure Boot, kan du behöva inaktivera detta alternativ i UEFI/BIOS-inställningarna för att tillåta start från din Xubuntu-installationsmedia.
[/LIST]
[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&quot]
[LIST]
[*]Välj rätt partitionsschema: Under installationen, se till att välja MBR (Master Boot Record) istället för GPT (GUID Partition Table) om din bärbara dator kör i Legacy BIOS-läge. Ubuntu-installatören bör automatiskt hantera detta om den upptäcker att du använder Legacy BIOS.
[/LIST]
[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&quot]
[LIST]
[*]Manuell partitionering: Du kanske behöver manuellt partitionera din hårddisk under installationsprocessen för att säkerställa att den är kompatibel med din äldre hårdvara.
[/LIST]
[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&quot]Det är också viktigt att notera att även om det är möjligt att installera Xubuntu på äldre hårdvara, kan vissa hårdvarukomponenter (som trådlöst nätverkskort eller grafikkort) ha begränsat stöd eller kräva ytterligare konfiguration för att fungera korrekt. Det rekommenderas att du kör Xubuntu från en live USB-enhet för att testa hårdvarukompatibiliteten innan du genomför en fullständig installation.
[/FONT][/COLOR]
[COLOR=#1B1642][FONT=&quot]Sammanfattningsvis, även om din Acer emachines E6 notebook är 10 år gammal och ursprungligen designad för BIOS istället för UEFI, bör du fortfarande kunna installera den senaste versionen av Xubuntu genom att följa dessa steg och eventuellt göra några extra konfigurationer.
[/FONT][/COLOR]

---

### Post by xrtc21 on 2024-03-09
> **oldfred said:**
> I always suggest using your Ubuntu or in your case Xubuntu live  installer and add the ppa per the second set of instructions. The ISO can be used, but is not updated as often and better to use latest version.
Boot-Repair's main fix is reinstall of grub or update of grub menu. 
But report and show other boot issues or sometimes other issues. Best to see report before you make any changes with Boot-Repair.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

Do you have latest UEFI/BIOS?
Many Acer models have needed latest UEFI/BIOS firmware.

Some older links, but most details should apply as Acer issues are common across many models.
Aspire E1-522 InsydeH20 Bios unlock -  7 min video
[https://www.youtube.com/watch?v=7SkBFkzOW0A](https://www.youtube.com/watch?v=7SkBFkzOW0A)

Acer is unique in requiring "trust" on "ubuntu" entry in UEFI settings.
Acer Very latest UEFI/BIOS works, downgrade not required if no trust screens, you must now upgrade:
[http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141](http://ubuntuforums.org/showthread.php?t=2298380&p=13419141#post13419141)
Acer Aspire ES1-512-C39M Details on supervisor password and settings to enable trust on ubuntu entries Also R14 model same fix
[http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044](http://ubuntuforums.org/showthread.php?t=2256083&p=13203044#post13203044) & 
[http://ubuntuforums.org/showthread.php?t=2290594](http://ubuntuforums.org/showthread.php?t=2290594)

Acer Trust Settings - details, some now report that then secure boot has to be on to set trust:
[https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](https://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742) & 
[https://ubuntuforums.org/showthread.php?t=2297947](https://ubuntuforums.org/showthread.php?t=2297947) & 

Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot)

yeah i am still thinking what to do. i am not really sure to be honest. but i am first of all gonna do a timeshift backup before i do anything else. and thinking of downloading some rescue software to a usb drive just in case it <snip>. you have any suggestions?
--
"I always suggest using your Ubuntu or in your case Xubuntu live installer and add the ppa per the second set of instructions" after xubuntu live insttaller "And add the ppa per the second set of instructions" 
-
so should i use boot repair home or the regular? 
because i used my xubuntu live flash drive and clicked on the "try xubuntu" and i followed this guide on this site. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
and i follow this :
**2nd option : install Boot-Repair in Ubuntu**

[COLOR=#333333][FONT=Ubuntu]- either from an Ubuntu live-session ([boot your computer on a Ubuntu live-USB]("https://help.ubuntu.com/community/BootFromCD") then choose "Try Ubuntu") or from your installed Ubuntu session (if you can access it)[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]- connect to the Internet[/FONT][/COLOR]
[COLOR=#333333][FONT=Ubuntu]- open a new [Terminal]("https://help.ubuntu.com/community/Terminal"), then type the following commands (press Enter after each line):[/FONT][/COLOR]

sudo add-apt-repository ppa:yannubuntu/boot-repair && sudo apt update
sudo apt install -y boot-repair && boot-repair

-----------------------------
Do you have latest UEFI/BIOS?
Many Acer models have needed latest UEFI/BIOS firmware.

Well i dont really know if i do have the latest firmware. where do i find out if i do got it? 

And I really didint know all that about acer ... now this went way complicated :(  

Maybe i should install some other lighter distro then xubuntu or what do you suggest?

---

### Post by dragonfly41 on 2024-03-09
Did you read post #30 - in Swedish? Source: Phind.com assistant.

---

