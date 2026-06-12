---
title: "Laptop Windows Vista croaked"
date: 2013-04-16
forum: General Help
---

### Post by jaxinco on 2013-04-16
Hi -- I'm new to the forum.  My Lenovo laptop will not boot up.  :( Long story short...laptop got unplugged accidentally [has no battery] while doing One-Key Recovery, so only part of Windows Vista was recovered. :mad: It comes on past the Lenovo Logo and I can get setup, but can't do anything with set up.  I don't want to pay for new upgrade of Windows on this laptop which is already 4+ yrs old.  I already learned it's not powerful enough for UBUNTU, but can I download Xbuntu to a CD and install it on this x@X# laptop?  Doe xbunto need Windows to work?  Sorry, for dumb questions. :confused: Lenovo IdeaPad Y530  I will come back later to the forum or you can email me with advice.  Have to go shovel the driveway.  Snowed-in in Denver!  TYVM in advance, jax

---

### Post by Mark Phelps on 2013-04-16
You don't need Windows in order to install Xubuntu, quite the opposite -- it will install without anything on the existing PC.

But, before you just go in and wipe Windows, you should boot the laptop from the CD, choose the Try Ubuntu option -- and see how well the laptop works.  Laptop suppliers are infamous for using special hardware, which requires special drivers, which often don't come with Linux.  If you can identify the things that don't work before you make the switch, you'll be in a better position to get those things working after the switch.

And, you need to think about what Windows-only apps you will need to replace in Ubuntu -- because it does not generally run Windows apps.

---

### Post by fantab on 2013-04-16
If the following are your laptop's specs then you can install and use Ubuntu:
[QUOTE=Lenovo IdeaPad Y530]
[TABLE="width: 389"]
[TR="bgcolor: #FFFFFF"]
[TD]Processor[/TD]
[TD="align: center"]2.0GHz Intel Core 2 Duo P7350[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD]Memory[/TD]
[TD="align: center"]2GB of 667MHz[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD]Hard drive[/TD]
[TD="align: center"]250GB at 5,400rpm[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD]Chipset[/TD]
[TD="align: center"]Mobile Intel PM45 Express[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD]Graphics[/TD]
[TD="align: center"]256MB Nvidia GeForce 9300M GS[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD]Operating System[/TD]
[TD="align: center"][Windows Vista Home Premium ]("http://reviews.cnet.com/Windows_Vista_Home_Premium/4505-3672_7-32013237.html") (32-bit)[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD]Dimensions (WDH)[/TD]
[TD="align: center"]14.2x10.3x1.2-1.4 inches[/TD]
[/TR]
[TR="bgcolor: #FFFFFF"]
[TD]Screen size (diagonal)[/TD]
[TD="align: center"]15.4 inches[/TD]
[/TR]
[/TABLE]
[/QUOTE]

Also, if Windows Vista can run on a computer then Ubuntu surely will. However, Xubuntu consumes far less system resources than Ubuntu. Lubuntu is even lighter.

---

### Post by jaxinco on 2013-04-16
Thanks Mark.  I'll have to go buy a blank CD so I can DL Ubuntu today using my husband's Dell.  I only used it for Facebook and yahoo.  I don't want to mess with drivers.  I doubt any apps I use are MIE only.  I used Firefox exclusively [hate MIE].  Yet....Other guy on this forum checked my system reqs for Lenovo IdeaPad Y530 and said it is good enough for Ubuntu.  Sooooo hope to get that CD today and let you know how it goes...:P  jax

---

### Post by GameX2 on 2013-04-16
You could install install Ubuntu/Xubuntu (Or other flavours) from a USB drive!

---

### Post by jaxinco on 2013-04-16
Thank you.  I wanted to get those reqs myself so I could see if I can run Ubuntu proper, but had to go shovel snow.  Ugh.   I'm happy to have a shot at getting the laptop back.  Hope I can get all my documents/photos back too.  But if not, Ohhh well.  At least with the laptop I'm not tied to this desktop! Sooooo hope to get a blank CD today and let you know how it  goes...:razz:  jax

---

### Post by fantab on 2013-04-16
There is a good probability that you can rescue your data. It should still be on the HDD. But before you actually install Ubuntu do consult the forum on how to rescue DATA.

---

### Post by Mark Phelps on 2013-04-16
You didn't specifically say you wanted to recover any of your data previous in Vista, but if you do want to do that, and are willing to spend some money, then read on ...  

In my experience, Windows filesystem utilities have been best at recovering data from former Windows partitions; Linux filesystem utilities have been best at recovering data from former Linux partitions. Your best bet at recovering data in a useful form from the Windows filesystem is to do as indicated below ...

Since your data was on a Windows partition, based on my experience at doing this successfully, my suggestions are the following:
[NOTE: If your PC has a working copy of MS Windows on it, skip to step 4]
1) Find someone with a working MS Windows PC
2) Remove your drive from this PC.
3) Connect your old drive to the MS Windows PC.
4) Download and install the trial version of RecoverMyFiles from Runtime Software in MS Windows.
5) Right-click the RecoverMyFiles shortcut and select "Run as Administrator"
6) Select the option to Recover a Drive
7) You will get a list of drive, scroll down to find the one for your USB stick or memory card
8) Select Automatic Driver recovery, press Start button
9) It will run for a while but when done, will show a directory tree in the left pane. Do NOT interrupt it.
10) When done, browse the folders in the directory tree -- and be SURE to check the filesizes of the files you want to recover.  If the filesize is zero, the file is trashed and you will NOT be able to recover it.

If the files look OK, you will need to contact Runtime Software to purchase a license for the recovery. You won't have to reinstall the app; instead, they will email you an activation code which you can use to turn on the recovery feature.

According to their website, the "standard" version of the app is $70 USD.  They also have a Pro version for $99 dollars, but if you go to the website below, you can compare the features and (at least for me) the extra cost wasn't worth it:

[http://www.recovermyfiles.com/data-recovery-software-purchase.php](http://www.recovermyfiles.com/data-recovery-software-purchase.php)

Your data ... your money ... your choice.

---

### Post by Irihapeti on 2013-04-16
@Mark Phelps

Your suggestions are only needed if the data has actually been wiped.

@jaxinco

First of all, try booting from a liveCD (when you can get one) and see if your documents etc are still there. They may well be. If not, then is the time to be thinking about complex data recovery.

---

### Post by fantab on 2013-04-16
My guess is, since jaxinco was trying to do a "One-Key Recovery" when the recovery went bad, I don't think the process would have re-formatted or deleted the partiton. And the data should be accessible from Ubuntu Live Media. And if the data to be rescued was NOT on C: partiton then it can definitely be backed up from Ubuntu Live media.

---

### Post by pqwoerituytrueiwoq on 2013-04-16
@fantab +1

[unetbootin](http://unetbootin.sourceforge.net/) can make you a bootable flash drive
i suggest using a 64bit os on that (these are over 700mb and don't fit on a cd, a 1gb usb is good though)
UBUNTU: [http://cdimage.ubuntu.com/daily-live/current/raring-desktop-amd64.iso](http://cdimage.ubuntu.com/daily-live/current/raring-desktop-amd64.iso)
XUBUNTU: [http://cdimage.ubuntu.com/xubuntu/daily-live/current/raring-desktop-amd64.iso](http://cdimage.ubuntu.com/xubuntu/daily-live/current/raring-desktop-amd64.iso)
LUBUNTU: [http://cdimage.ubuntu.com/lubuntu/daily-live/current/raring-desktop-amd64.iso](http://cdimage.ubuntu.com/lubuntu/daily-live/current/raring-desktop-amd64.iso) (Should fit on a cd)
KUBUNTU: [http://cdimage.ubuntu.com/kubuntu/daily-live/current/raring-desktop-amd64.iso](http://cdimage.ubuntu.com/kubuntu/daily-live/current/raring-desktop-amd64.iso)
UBUNTU GNOME: [http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/raring-desktop-amd64.iso](http://cdimage.ubuntu.com/ubuntu-gnome/daily-live/current/raring-desktop-amd64.iso)

These links are the current developmental version, it will be a release candidate in a couple days, at this time i don't think it is worth the effort of installing 12.10
i have been using xubuntu since before beta 1 for 13.04 and there has been nothing that has messed me up and interfered with daily activity

---

### Post by afz12 on 2013-04-17
My third Acer 3003 notebook is well over 10 years old and it ran Ubuntu 8.04 from scratch without and real issues. I had to download a broadcom wifi driver using either an Ethernet connection to another notebook, or a port on a wifi modem or a dial-up telephone connection. It only had 512 MB of RAM and runs OK (I don't use it much these days!). I found that Ubuntu 8.10 resulted in screen display issues but 8.04 was fine. Your specifications seem more than adequate for any Ubuntu version - if it ran Vista then it should run anything.   If you have an Ubuntu etc installation disk, you can run the OS directly from this - or use a USB stick formatted as a  boot device (e.g. use Ubuntu' startup disk creator). If the LInux version runs OK, I suspect it should equally install OK. I also note that in my dual boot notebooks, I can always "see" other partitions from Ubuntu or Mint. If you open the file icon then you may be able to access any files you need and transfer these to a USB stick or disk. The other posts seem to present excellent advice - good luck. I suspect you will end up with a far better OS than Vista.

---

### Post by kurt18947 on 2013-04-17
The O.P. may already know this but the user interface on Ubuntu is quite a bit different than Windows prior to Windows 8.  It might be wise to go with another more traditional 'flavor' of *buntu such as Kubuntu, Lubuntu or Xubuntu.  Many people find linux mint with cinnamon a nice alternative with a 'traditional' user interface.  I use gnome but there is a bit of a learning curve associated as there is with Unity, Ubuntu's default U.I.  I wouldn't characterize Unity or Gnome shell as 'bad', once familiar I prefer gnome 3 shell to gnome 2 but it took some familiarization.

Re recovering data unless the Windows file system has been corrupted, any *buntu live CD or USB should mount and 'see' Windows installs including user data folders/directories.  If the NTFS file system has been corrupted as opposed to Windows O.S.files being corrupted then life gets more complicated.  I'd sure see what shows up once a live install is booted as a first step though.  Windows installations typically show up as "xxx GB file system"  Double click on that and see what shows up.

---

### Post by jaxinco on 2013-05-01
Thanks for all the suggestions, all of you.  Tonite we finally bought some 80 min Memorex CDs, then we came home and used my husband's Dell Desktop with Windows 7 to DL the file pack for Ubuntu 12 onto his computer.  We figured out his computer has the Image Burner thingie and so after we DL'ed the Ubuntu 12 files, we clicked on the iso image and tried to burn the CD. BUT the windows burner said the file was too large to burn on the CD.  So I checked on WWW for this problem and found that others also have had this problem.  It seems the downloaded Ubuntu files are often slightly too large for the 700 MB 80 minute CD.  I still want to try Ubuntu on my busted laptop, as cheaply as possible because it is not new enuff to warrent spending a lot of $$, and if I can get aUbuntu CD burned.. I'm willing to be hostage to the laptop answering questions every ten minutes to get Ubuntu installed.  @fantab I really don't think I could do a complex recovery of Windows Vista myself, but I might get my son [computer engineer] to do it in order to salvage my photos, etc.  @fantab  I do hope installing Ubuntu will enable me to get my data through Live Media whatever that is...Now I need to know what to do about not being able to burn the files onto the CD.  I have read some solutions about it.  One is to write the file slower during download (however that is done), another is use a different brand of CD, one is use a DVD Disk instead of CD, another is Download and use Brasera Burner instead of Standard Windows Image burner,  etc etc.  Help?

---

### Post by jaxinco on 2013-05-01
yeh i think I will DL Lbuntu [forgot about it] and see if I can burn it onto the CD instead of Ubuntu 12.  All I want the laptop for is Facebook, Hasbro Scrabble game, and Yahoo email and to be able to have the laptop close at hand wherever I am in the house or deck [we have a big house].  Let u know how it transpires....Thanks.

---

### Post by C0NFU53D2 on 2013-05-01
if you have a spare usb laying around that is 750mb or larger, and your computer can boot from USB you could try that, a few guys have already suggested that while you were away, and what is cool about using a usb is you can then format it and reuse it for something else!  most modern computers, including vista ones (especially laptops) have the ability to boot from USB, my old 2003 Dell desktop that came with Win XP has the ability to boot from USB.  just another alternative you can try! 

Goodluck!

---

### Post by jaxinco on 2013-05-01
More snow in N Denver ...ugh.  Ok  USB?  Is that a little plug in thingie?  I have one here and it has 1G on it so I assume that means 1 gig... We looked at one dl site for Lubuntu at [www.lubuntu.net](www.lubuntu.net) so far.  It says to use "torrent" but we have never done torrent so would rather just download the files to my husband's Dell [win7] and then burn the CD with his Windows Image Burner...hopefully Lubuntu will FIT on the CD.  So I will try to find another Lubuntu site that doesn't require Torrent.  Someone gave me an address in these forum messages last night for Lubuntu download.  Will try to find that one.  Any advice appreciated.  Thanks to all.  jax

---

### Post by Cheesemill on 2013-05-01
All of the different versions of Ubuntu can be downloaded from here, both normal downloads and torrents.

[http://releases.ubuntu.com/](http://releases.ubuntu.com/)

---

### Post by jaxinco on 2013-05-01
@cheesemill I was just about ready to try this one given to me last night.  LUBUNTU: [http://cdimage.ubuntu.com/lubuntu/da...ktop-amd64.iso]("http://cdimage.ubuntu.com/lubuntu/daily-live/current/raring-desktop-amd64.iso") (should fit on a CD) but will write your suggestion down too.  Thanks   jax   Added note:  after looking at the releases site you gave I am stymied about what to do with that stuff.  I just need a regular userfriendly dl site for lubuntu, so will go with the first one.

---

### Post by jaxinco on 2013-05-01
sheesh   I downloaded the lubuntu file at lubuntu-13.4-desktop-i386.iso and it took 4+ hours to download.  Then when I went to burn it on a CD, I got File Invalid message from the burner. I tossed it in the Recyle bin.  Now what?

---

### Post by jaxinco on 2013-05-01
it's really weird, but on my husband's Dell, when I type in the Lubuntu address u gave, it fails.  But on our old Dell, it works when I click on it and gives me the download window.  Maybe if I open the forum post on the new Dell, and click on it there...it will work.  This is getting to be a real PITA!  LOL

---

### Post by jaxinco on 2013-05-01
ok   got ubunto forums open on husband's computer and am now downloading the file for Lubuntu you gave me. It worked fine when I clicked on it.  Gonna take hours again to DL it, but WTH.  Hope the windoze image burner will be able to burn this one.

---

### Post by Mark Phelps on 2013-05-01
I noticed that in your first post, you have only 2GB of memory and were running Vista 32-bit.  With that little memory, 64-bit will give you no advantages at all over 32-bit.  If I were you, I'd go for a 32-bit version at present.

---

### Post by jaxinco on 2013-05-01
OK  so I stop the DL of the 64 and trash it.  NOW ... where can I find the 32-bit Lubuntu download?  Sorry, I didnt say thanks... :)  My husband told me I needed 32-bit...shoulda listened to him.

---

### Post by jaxinco on 2013-05-01
Bye.  Have to reboot to get rid of the 64-bit file.  L8R

---

### Post by jaxinco on 2013-05-01
OK...found lubuntu-12.10-desktop-i386.iso to download.  It's 32-bit.  Gonna take 4-5 hrs to download, but the time jumps around so it may only be 2 hours.  Oh what fun.  LOL  At this point, I don't care what version it is, just as long as I can get it burned on a CD and install it on my laptop.

---

### Post by Mark Phelps on 2013-05-02
> **jaxinco said:**
> OK...found lubuntu-12.10-desktop-i386.iso to download.  It's 32-bit.  Gonna take 4-5 hrs to download, but the time jumps around so it may only be 2 hours.  Oh what fun.  LOL  At this point, I don't care what version it is, just as long as I can get it burned on a CD and install it on my laptop.

The one I downloaded was 794MB -- too large to fit on a CD.  While some CDs can be "overburned" to hande a little more than 700MB, none can handle an image this size.

You will need to either burn it to a DVD, or, if your PC can handle booting from USB, use either Unetbootin or PendriveLinux to image that ISO to a USB stick and install from that.

---

### Post by fantab on 2013-05-02
Until recently I had only 2GB RAM, and I dual booted Win7 32bit (earlier it was Vista 32bit) and Ubuntu 64bit... no issues. So, IMO, Lubuntu 64bit should work great unless you have 32bit processor/CPU. Since you've already downloaded 64bit Lubuntu, I suggest you install it, if there are any issues related to processing speed then switch to 32bit. I don't think there should be.

My two cents...

---

### Post by jaxinco on 2013-05-02
yes...we are dloading 32 bit 12.10 LUBUNTU now.  Have tried it several times, but something happened and the dl failed.  Tried it overnite and the PC went to sleep and it stopped, so continuing the DL this morning.  Hubby works on his computer all day, so hopefully the cable can handle the DL while he is working.  I'm worried 12.10 LUBUNTU wont fit on the CD when we go to burn it.  If that happens, we will have to figure out how to torrent and put it on a USB thingie, which we have never done.

---

### Post by jaxinco on 2013-05-02
The 64 bit failed to DL yesterday.  Hubby rebooted PC, forgetting the DL was happening. grrr  anyway, by that time, Mark had told me 32 bit would be best since my laptop is 32 bit CPU. [which my husband had already told me and I ignored].  So last night we were DL the 32-bit LUBUNTU and it was slow because he was watching a netflix movie.  Overnite, we let it continue to DL but the PC went to sleep and so it stopped.  NOW he says Firefox just crashed so we lost that DL too.  So trying to figure out if our OLD Dell can handle the DL with me babying it for hours, and not doing anything else to interfere with the DL.  If I can get the DL done, then DL a free burner to old Dell and do the burn on the CD on the old Dell, leaving the New Dell free for my husband's work.  Guess it's worth a try...heh heh

---

### Post by fantab on 2013-05-02
I assume that you are downloading from Windows... why don't you do a torrent download it supports resume and it checks the download for errors etc. IMO [uTorrent]("http://www.utorrent.com") (torrent downloader) should serve you well. Also consider '[freedownload manager]("http://www.freedownloadmanager.org")' for regular downloads it too supports 'resume' function.

---

### Post by jaxinco on 2013-05-02
We finally got the lubuntu 13.04 downloaded, verified, and burnt onto a CD.  Put CD in laptop.  Nothing.  we could hear it trying to read the CD.  Triued soft boot [alt-cntrl-del] all we have it the blinking cursor in the top left hand corner of blank black screen.  Now what?  Help!

---

### Post by jaxinco on 2013-05-02
We did download from windows.  Finally got one to download fully today.  We verified it before we burnt it and it did burn properly. We did the lubuntu 13.04 release in order for it to fit on a CD, otherwise we would have to go buy blank DVDs. But now that we have put the disk in the laptop, it isn't booting up.  We thought lubuntu would boot up from the CD and not need Windows (which is defunct and only loads to setup if we repeatedly hit F12, but wont boot from setup either because it got unplugged during 1 key recovery and Windows Vista didn't get fully recovered).  As for bit torrent, we have never done any of those.  What we need to know now, is how to get the lbuntu 13.04 to boot up from the CD.

---

### Post by jaxinco on 2013-05-03
Rejoice!  We got the blue Lubuntu screen to come up from the boot list or whatever it's called.  The CD is running so sounds like something is happening in there.  Under the Lubunto Logo in the middle of the blue screen are 5 dots....two are white and last tree are still blue.  What now?  How long does installation from live CD take?

---

### Post by fantab on 2013-05-03
Ubutnu or Lubuntu the install procedure is same. This should help: [http://www.ubuntu.com/download/desktop/install-desktop-latest](http://www.ubuntu.com/download/desktop/install-desktop-latest)

About Torrents: There is nothing illegal in downloading legal material via torrents. Downloading Ubuntu via torrent is legal and it is offered legally, [See Here]("http://www.ubuntu.com/download/alternative-downloads"). Torrents are very good to download copies of legal software/OS because the integrity of the downloaded material is almost guaranteed when compared to regular, non-torrent downloads.

---

### Post by jaxinco on 2013-05-03
thanks for the torrents info.  makes sense.  we plan to learn more about torrents.  Right now, trying to get chrome installed on lubuntu.  We did get Lubuntu installed last night by choosing the Try Lubuntu without installing option.  Well, it did have an install icon so we installed it anyhoo.  Had to wipe windoze, but WTH.  NOW want to install Chrome in order to get Adobe Flash working.  Chromium comes with Lubuntu, but has no Adobe flash!  I need Flash for watching videos on Facebook.  I downloaded Chrome 3 times but cant get it to install automatically.  sheesh

---

### Post by fantab on 2013-05-03
Use CHROMIUM, instead. It is the open source version of Google Chorme and is available from 'Software Cener'. Chromium Browser is Google Chrome minus "Google Branding" and everything you can do with Chrome can be done with Chromium. Google just brands CHROMIUM and adds a few 'bells and whistles', that is all. 

Also install "Synaptic" Package Manager it far better, IMO, than default "Software Center".

You have to install "[lubuntu-restricted-extras]("https://help.ubuntu.com/community/RestrictedFormats")" package to have "flash" and play music in 'mp3' or in other 'closed source' file formats and to play videos. EDIT: This package also installs Microsoft Fonts.

---

### Post by jaxinco on 2013-05-03
well...i hope i got the extras.  i did the command thingie and at the end of it was some microsoft copyright message and I couldnt figure out how to accept it.  I dont know where to go to see if I got it or not, since lubuntu is so freaking weird.  u have top tell me where to find things on lubuntu or whether I need to look for these apps on WWW.   I did find the extras on WWW so went with that.   I'm using my Dell desktop computer for this forum. I will try to dl Abobe Flash again on my laptop (has lubuntu) to see if it will work now.

---

### Post by fantab on 2013-05-04
Don't install anything from WWW. it will create problems. I suggest you start a new Thread on the forum and ask for help with Lubuntu... I don't use Lubuntu so I can't exactly tell you where to look.

The Following are general instructions and they should work.

Open Terminal (ctrl+alt+T):

```
sudo apt-get update
sudo apt-get install synaptic
synaptic
```

The last command will run Synaptic Package Manager, you will have to enter your password. In the synaptic window you will see a search box... type in whatever package you want to install, with right click on the listed pkg. "Mark for installation" and APPLY.

You will get more help if you start a new thread.

---

### Post by kurt18947 on 2013-05-04
You don't need Chrome unless you need the latest version of Flash.  Adobe has stopped *developing* versions of flash for linux beyond 11.2xx but the version in the repositories still works (unless you get bit by the blue man bug, and the fix for that is readily available).  Adobe does issue security fixes for 11.2xx.  Synaptic is a good package manager, search for 'flash' and you should find "flash-installer" or similar.  I usually install *buntu-restricted-extras from the repositories.  That will also get you some codecs and video player help as well as flash player.

---

