---
title: "Which version is the most appropriate"
date: 2013-06-03
forum: General Help
---

### Post by anon_private on 2013-06-03
Hi,

Processor: Pentium D 915 Dual Core, 2.8 GHz.
Ram: 1GB.
Requiremene: A good quality word processor that must support MS doc formatting

 Am i right in thinking that UBUNTU is the best option?

On another point

If I can't boot from Vista and decide to repalce it with UBUNTU could UBUNTU preseve my files?

---

### Post by DeMus on 2013-06-04
Make a good backup from all your important files. Make sure you've got them all.
Download either Ubuntu 13.04 (latest version) or the 12.04 LTS version (a bit older but still 4 years receiving updates) and burn it to a CD or DVD
Boot the computer from the new disk and try Ubuntu in the live version to see if it is what you like. If so, install it to hard disk and copy your files from the backup to your home directory.

Have fun.

---

### Post by 3rdalbum on 2013-06-04
Yes, Ubuntu is probably the best option for you.

Ubuntu cannot install to a Windows filesystem without completely formatting it, so you need to backup your files or do a side by side installation (dual boot).

---

### Post by Impavidus on 2013-06-04
Whether a word processor has good quality is subjective, but support for MS Word .doc and (especially) .docx will only be partial. The best program for MS Word documents will always be MS Word. But if you are fed up with Windows Vista, then give Ubuntu a try. With 1GB of RAM it should run acceptably, but also consider using one of the lighter flavours, like Xubuntu.

Consider running Ubuntu as a dual boot next to Windows, or on a second machine, if you happen to have two. Many people who just replace Windows with Ubuntu find out there is one Windows program they can't live without (yet).

---

### Post by mörgæs on 2013-06-04
If the word processor is important I would recommend 13.04 over 12.04 because of the better Libreoffice package.

---

### Post by anon_private on 2013-06-05
Thank you.

I am running Ubuntu 12.10 from a pendrive. It does has Libre Office.
Is it worth downloading 13.04, evidently the latest?

How much RAM does 13.04 need?

Thanks

Ps. I sometimes get a mouse freeze that recovers. I have a new motherboard. Is this likely to be due to have only 1 GB of memory, or could it be UBUNTU

---

### Post by Frogs Hair on 2013-06-05
If your video card/chip does't have its own memory consider Xubuntu which is more traditional and less resource hungry. It doesn't come with Libre Office, but a search indicates it can be easily installed.

---

### Post by sudodus on 2013-06-05
> **anon_private said:**
> Thank you.

I am running Ubuntu 12.10 from a pendrive. It does has Libre Office.
Is it worth downloading 13.04, evidently the latest?

How much RAM does 13.04 need?

Thanks

Ps. I sometimes get a mouse freeze that recovers. I have a new motherboard. Is this likely to be due to have only 1 GB of memory, or could it be UBUNTU

If you have a fairly good internet connection, download also the Xubuntu and Lubuntu desktop iso files and try them live before you decide what to install. Choose your balance between speed and eye-candy. With 1 GB RAM I would recommend either of these light-weight flavours instead of standard Ubuntu (but it is your decision).

If you have a slow internet connection, you can install the corresponding desktop environments and select which one to run at the log in screen.

```
 sudo apt-get install lubuntu-desktop
```
```
 sudo apt-get install xubuntu-desktop
```

and remove what you do not need afterwards. See this link

[http://www.psychocats.net/ubuntu/](http://www.psychocats.net/ubuntu/)

---

### Post by Mark Phelps on 2013-06-05
> **anon_private said:**
> ... 
Requiremene: A good quality word processor that must support MS doc formatting

Sorry, but the honest truth is that NO Linux distro is going to provide full MS doc formatting.  IF you are content to stick with OLDER MS Word versions (like Office 2007) and can be assured of NOT receiving MS Word docs in the new (since Office 2007) .docx format, then Wine will probably work well, and LibreOffice, and even the older Open Office, should both work OK.

But,  if you need to use something newer (like Office 2010) and also need to be able to work with the newer .docx format documents, then Wine is not a good solution, neither are LibreOffice nor Open Office.

Finally, if you need to use Office 2013, then forget Linux, period. That only works with MS Windows.

>  Am i right in thinking that UBUNTU is the best option?  If by that, you mean your best alternative to using Vista for general purpose computing, that might be true -- but with that processor, and that little memory, like the others suggested, I would avoid Ubuntu, especially 13.04.  One of the lighterweight distros would probably work better.

> If I can't boot from Vista and decide to repalce it with UBUNTU could UBUNTU preseve my files?
If you overwrite Vista, then no -- your files will get overwritten.

To preserve data files, you will need to copy them somewhere else (USB  stick, for example) that you can then access after you install Ubuntu.

---

### Post by TNFrank on 2013-06-05
You might be able to use the wubi to install a version of Ubuntu inside Windows so you can try it out and see if you like it. Then if you do you can make a bootable copy of the flavor of Ubuntu that you like using the Startup Disk Creator in Ubuntu. You can do that for a CD or USB as long as you've got enough space.  For Ubuntu 12.04.2 it just did fit on a 700MB CD but IIRC 13.04 is a bit larger. 
 Either way I think you'd do well with Ubuntu and LibreOffice for your needs.  If you can I'd try to bump up the RAM to 2GB though just to give you more then enough space. Good luck.

---

### Post by QIII on 2013-06-05
Hello!

If you have the disk space, I +1 a dual boot (AFTER backing up everything, just in case)

This is not an either/or choice and you should always use what works best for the task you are trying to accomplish.  Who cares if that is Windows?

I RDP into a Win 7 machine from my main Kubuntu machine all the time to use Office.  I think sneering at Windows is a bit fanboyish.

Use what works.

Best wishes!

---

### Post by anon_private on 2013-06-06
Thank you

Is Ubuntu 12.10 still supported, and will it be supported for a length of time?

If I install a version and later decide to install another flavour, or update, is it easy to simply replace the OS. How would I go about this?

Thanks

Ps. I may/maynot bge able to get VISTA working

---

### Post by DJWYMAN on 2013-06-06
12.10 is supported until April 2014.  here is a chart to show the life cycle of the releases: [https://wiki.ubuntu.com/LTS](https://wiki.ubuntu.com/LTS)

if you cannot boot up into vista you can use your live usb to put your personal files on to another removible drive before getting rid of vista.

---

### Post by Impavidus on 2013-06-06
Installing a new flavour (Ubuntu/Kubuntu/Xubuntu/Lubuntu) can be done by installing a package and choosing the new desktop environment at login. You than can remove the old: [http://www.psychocats.net/ubuntu/purexubuntu](http://www.psychocats.net/ubuntu/purexubuntu), or just keep it as a backup. It only takes some disk space.*

Moving from one version to the next (12.04 LTS>12.10>13.04>13.10>14.04 LTS, any version to the next LTS version) is possible by upgrading. Usually this works and keeps all your data & installed apps (unless they've been removed from the repos), especially if you haven't changed your system too much from a default install, but sometimes it doesn't. Therefore many prefer clean installs. Any other upgrades/downgrades have to be performed by clean installs. These work best if you have all your data on a hard drive partition separate from the OS, so that you can keep your data when wiping the / partition.

*Edit: That's not entirely true, there are some incompatibilities, which shouldn't harm you too much. Especially Ubuntu and Xubuntu play together nicely.

---

### Post by anon_private on 2013-06-06
Thank you

A few questions (these will cover a number of topics)

I am not sure how a clean install would work (I am sure it does). If I am using the pc does it not need to OS at all times?

Another point.

I have the following live cd's:

Ubuntu 12.10
Ubuntu 10.04 LTS
Ubuntu 9.10

Bearing in mind my processor, Pentium D, and 1 MB of RAM, which would be the best to install?

I tried Lubuntu, I don't like it it is too light. I get the impression that the 'heavier' the OS the better (by better, I mean more facilities and more options with programs - just a better OS).

Regarding Ubuntu 12.10, where are all the utilities. I see the icon list at the left hand side, but no mention of utilities or tools?

Regarding the creation of a persistent pendrive.

I have a live pendrive (not presistent). I also use this pendrive to store personal files. If I created a persistent pendrive would I lose the personal files and directories. Would I still be able to use the pendrive for storage after creating a persistent pendrive.

---

### Post by sudodus on 2013-06-06
> **anon_private said:**
> Thank you

A few questions (these will cover a number of topics)

I am not sure how a clean install would work (I am sure it does). If I am using the pc does it not need to OS at all times?

It needs an OS to do something useful. But the OS could be on a live CD/DVD/USB drive, it need not be installed to an internal drive. Typically linux is installed from a live drive.
> 
Another point.

I have the following live cd's:

Ubuntu 12.10
Ubuntu 10.04 LTS
Ubuntu 9.10

Bearing in mind my processor, Pentium D, and 1 MB of RAM, which would be the best to install?

a. Ubuntu 9.10 passed end of life years ago. Ubuntu 10.04 desktop passed end of life last April, but Ubuntu 10.04 Server has two more years to go, but then you have no graphical desktop (only text). Ubuntu 12.10 is new but not the newest version, end of life is April 2014. Ubuntu 12.04 has LTS (long time support) until 2017. Ubuntu 13.04 is the newest version, but has end of life in January 2014. Do not use versions that have passed end of life, because there are no security updates!

b. Unless you want to increase RAM to 2 GB or more, I would recommend a lighter desktop than the standard Ubuntu.
- So if you have a fast internet access, I recommend that you download Xubuntu 12.04 LTS with support until April 2015.
- If you have a slow (or expensive) internet access, start from Ubuntu 12.10. It might work but very slowly. Then you can install Xubuntu-desktop and select desktop environment at the log in screen.

```
sudo apt-get install xubuntu-desktop
```
> 
I tried Lubuntu, I don't like it it is too light. I get the impression that the 'heavier' the OS the better (by better, I mean more facilities and more options with programs - just a better OS).

Regarding Ubuntu 12.10, where are all the utilities. I see the icon list at the left hand side, but no mention of utilities or tools?

Click on the Ubuntu symbol at the top left corner ...
You can also start a terminal window with the hotkey combination ***ctrl + alt + t*** and you can start any program from there.
> 
Regarding the creation of a persistent pendrive.

I have a live pendrive (not presistent). I also use this pendrive to store personal files. If I created a persistent pendrive would I lose the personal files and directories. Would I still be able to use the pendrive for storage after creating a persistent pendrive.

You can do both, but if the drive is small, it it best to choose either to have free space for files in the first partition or to keep files in the casper-rw file or partition (which stores the persistent properties (files, programs, tweaks). But persistent drives are sensitive and prone to break, because writing of the current system to the storage is very slow and if you unplug the drive too early, the information is damaged. So you need frequent backup to maintain persistent system.

---

### Post by Impavidus on 2013-06-06
> **anon_private said:**
> 
Bearing in mind my processor, Pentium D, and 1 MB of RAM, which would be the best to install?

I tried Lubuntu, I don't like it it is too light. I get the impression that the 'heavier' the OS the better (by better, I mean more facilities and more options with programs - just a better OS).


The most important difference between Ubuntu, Lubuntu and any other flavours is the user interface. The interface of Xubuntu looks quite similar to the one of older Ubuntus. I like it. But all flavours have the same programs available, although not all the same programs installed by default. Under the hood they are all the same, just the user experience and resource consumption are different.

Installing Xubuntu 12.04 LTS would be a good option.

---

### Post by anon_private on 2013-06-07
I rather like Ubuntu 12.10 and although I have only 1MB of RAM is seem to run alright.

I expect the latest UBUNTU will require more RAM than I have available. How much RAM does the latest version require?

If I have a positive experience with UBUNTU 12.10 as a live pendrive. Is there any reason not to install it?

Thanks

Ps. At present, I am still struggling to get VISTA up and running. I will wait untill I get this OS running before installing UBUNTU so I can install side by side.

A couple of other points. I have a floppy drive on my pc. The LED is on all the time when running UBUNTU from the pendrive. Can I switch this LED off in case I need to use the floppy?

Whe I boot into UBUNTU from the pendrive it takes about 25 seconds to see the wireless authentication page. Is this due to having only 1MB of memory?

'12.04 has LTS (long time support) until 2017.'

Maybe I should try this OS. How much RAM is needed?

---

### Post by sudodus on 2013-06-07
There is no absolute limit (except what is needed for the installer to run), but I would say that it is about the same for 12.04.2 LTS and 12.10. You have 1 GB, and you are fairly happy with it. I would say the sweet point is at least 2 GB for the 32-bit version and 4 GB for the 64-bit version of standard Ubuntu with Unity. But the preferred balance between speed and eye-candy is very different between people. It is easy to try 12.04.2, so go ahead and download it :-)

I should also add, that I prefer the LTS versions because they get well debugged and polished.

---

### Post by anon_private on 2013-06-07
A few points, I note what you said regarding memory, but I am also influeeced by what is said on the CD's. In the case of 12.10 it says a minimum of 768 MB. I have a 1GB. I realise that there is a relationship betwen RAM size and speed. In addition, if I were to install a version, I assume that I create a cache that would help.

Someone mentioned the importance of support and security. Is security that important. After all, UBUNTU is not Windows and malware and viruses are rare?

Are there other resources for applications and utilities other that the UBUNTU repository. For example, are there sites when someone can simply download the application and install it, rather along the line of Windows?.

I am going to have alook at the versions, especially the LTS OS's

Ps. Any idea why my floppy LED is constantly on when using UNUNTU as a live pendrive?

Are there details and the look of 12.04 LTS on the site (images application details, etc).
That page that lists LTS etc seems to predict the future

I've just found the min ram for 12.04 LTS (384 MB) for 32 bit. Half of that needed for 12.10.

Has anyone noticed a critical limit for memory. That is the ammount of memory that can be used before things become unstable?

I tried loading an mp3 but without success. Am I right in thinking that the mp3 player does not come with the algorithm as a live pendrive/cd?

---

### Post by sudodus on 2013-06-08
> **anon_private said:**
> A few points, I note what you said regarding memory, but I am also influeeced by what is said on the CD's. In the case of 12.10 it says a minimum of 768 MB. I have a 1GB. I realise that there is a relationship betwen RAM size and speed. In addition, if I were to install a version, I assume that I create a cache that would help.

Someone mentioned the importance of support and security. Is security that important. After all, UBUNTU is not Windows and malware and viruses are rare?

See this link [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)
> 
Are there other resources for applications and utilities other that the UBUNTU repository. For example, are there sites when someone can simply download the application and install it, rather along the line of Windows?.

Yes, you can activate some other repositories (built in sources of program packages) using for example ***Synaptic***. There is also the ***Software Center***, where many programs are found and installed easily.

Only when you cannot find what you want there, you should start downloading programs manually. Deb-files can be installed in a way similar to Windows self-installing files. Source code packages can be compiled and installed, but that is more complicated.
> 
I am going to have alook at the versions, especially the LTS OS's

Ps. Any idea why my floppy LED is constantly on when using UNUNTU as a live pendrive?

No, I have not used floppy with linux. I tested that it works maybe ten years ago, but that's all.

> **anon_private said:**
> Are there details and the look of 12.04 LTS on the site (images application details, etc).
That page that lists LTS etc seems to predict the future

12.04 LTS and 12.10 look rather similar. The differences are mainly under the hood. The tradition is to release an LTS in April even years (.. 2012, 2014 ...)

> **anon_private said:**
> I've just found the min ram for 12.04 LTS (384 MB) for 32 bit. Half of that needed for 12.10.
Well, that figure is ***very*** theoretical for a graphical desktop. I would not even recommend it for the ultra light-weight flavour Lubuntu. But it might work for a server with only text screen interface.

See this link about old hardware

[http://ubuntuforums.org/showthread.php?t=2130640](http://ubuntuforums.org/showthread.php?t=2130640)

> **anon_private said:**
> Has anyone noticed a critical limit for memory. That is the ammount of memory that can be used before things become unstable?

I tried loading an mp3 but without success. Am I right in thinking that the mp3 player does not come with the algorithm as a live pendrive/cd?

Normally you will get a swap partition on the hard disk drive (virtual memory) when you install Ubuntu. When you run live from a CD or USB drive, you have no swap partition, unless you make it manually, or there was already one on the hard drive (created by another linux system).

When you run out of RAM, code is swapped into the swap partition to create space for the new code to use. This swapping is very slow, and the computer starts lagging. But it works, if you are patient, so it will not be unstable. But I think you have found one reason to have more RAM or a lighter desktop environment than standard Unity. If the operating system fills the RAM, there is no space for application program.

An music player comes with every Ubuntu flavour. You can add codecs and other proprietary packages to play multimedia (CD, video clips as mp4 files etc). Due to legal reasons, such software can not be delivered with a system that you buy (unless someone pays for licenses, and in the end it is you), and you can buy a computer with Ubuntu. However, in most countries it is allowed to download it for personal use, and it is easy.

The other flavours, Lubuntu, Xubuntu, Kubuntu, Ubuntu Studio etc, can only be downloaded, so they can include more proprietary software.

---

### Post by anon_private on 2013-06-08
The RAM that I quoted (for 12.04 LTS) was given by the producers of the OS - as far as I know.
I have by no means filled my RAM. Under normal circumstances I have not exceeded more that about 60%, usually less.
I have had no real problems with 12.10 as a live pendrive and would expect the 12.04 LTS to be even more suitable. I also like LTS.
However, If I do make a mistake it is not irrevocable. I can always download and install other OS's based on my experience of using UBUNTU.

Best wishes.

Ps. The links you supplied are very useful

---

### Post by sudodus on 2013-06-08
Yes, you can even add the lighter desktop environments and have a choice at the log in screen. So for some applications you might prefer standard Ubuntu, but for others you might prefer Lubuntu or Xubuntu, for example when you want to run high definition multimedia (720p might work, while 1080p is probably too much for the computer).

```
sudo apt-get install xubuntu-desktop
```
```
sudo apt-get install lubuntu-desktop
```

You can wipe the unwanted desktop environment afterwards if you like, see the [Psychocats link]("http://www.psychocats.net/ubuntu/").

Good luck :-)

---

### Post by prodigy_ on 2013-06-08
> **Impavidus said:**
> support for MS Word .doc and (especially) .docx will only be partial. The best program for MS Word documents will always be MS Word.
While the latter statement is true, the former isn't. A DOCX document is just a set of XML files compressed into a ZIP archive. Since [OOXML is an open standard](http://en.wikipedia.org/wiki/Office_Open_XML), it's **easier** to achieve compatibility with DOCX than with DOC and other legacy MS Office document formats.

---

### Post by 3rdalbum on 2013-06-08
There is no MP3 playback support included in Ubuntu, but it can be installed. The ubuntu-restricted-extras package is available in Ubuntu Software Center and will download and install virtually everything you will need for media.

There are no sites where you can download software like on Windows. On Linux we download and install software via a package manager, not by downloading a radon binary from a website, double-clicking it and hoping there's no malware in it.

Some proprietary software is still done this way on Linux, but the repository system (Ubuntu Software Center) is the best way to get and update your programs.

---

