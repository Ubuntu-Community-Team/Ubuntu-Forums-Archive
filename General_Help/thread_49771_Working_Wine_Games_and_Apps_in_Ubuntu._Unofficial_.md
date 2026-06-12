---
title: "Working Wine Games and Apps in Ubuntu. Unofficial help!"
date: 2005-07-17
forum: General Help
---

### Post by Omnios on 2005-07-17
Wine in Linux gets a lot of flach but needless to say it is a Lunux other app! 

 This thread is to gather of list of Working WIne Games and apps in wine under Linux as well as how to's and hints etc. I played around with wine for quite a while and spent weeks trying to get Delta Force 2 working under wine to no avail it would not ethenticate the cd launcher making it so I could not play. I have had DF for years and this is my main reason for trying wine so I can use them in Linux.

 Also there is little help when it comes to wine expecialy when it comes to synaptic version of wine which is a bit dated.

 The format of this thread is if you have a short post or comment post it here. If you are planning a series of long post such as an effort to document how to set something up in Wine post a seperate post such as "Delta Force in Wine" with a edited link to that post in this thread. This would allow for a centralised wine effort to get games working in wine as well as a post specific to that game in wine. 

 I seriosly hope this works out to help people get things running in wine.

[Wine Homepage for reading about wine](http://www.winehq.com/)

---

### Post by Omnios on 2005-07-17
I spent a few weeks truing to get Delta Force running in Wine and it seems it can not detect the cd which is needed to launch the game. The install when't well and I even managed to update it but can not play with oput the cd. Aperently this also occurs in DF1 but think you can still play MP without the cd though.

---

### Post by Omnios on 2005-07-17
I want to try to get this game going in wine. It has some wierd anti cheat scanners that may cause a problem though. Driving force behind this game is it is free huge online game!

 [http://www.knightonlineworld.com/](http://www.knightonlineworld.com/) 

 First I have to install Wine again and figure out how to config it to my vFat 32 drive.

 Another staple is a very old game called the 4th comming which has licenced online server from many companies for exaple : [RealMud Server](http://www.realmud.com/faqs.php) When I get around to installing and figuring how to config Wine I am going to try this game as its an old win 98 based game and has free weekday and low priced pay to play online play. SOme of them allow you to play for free from Monday to Thursday. Here is a list of websites. [Goodle 4th comming Directory!](http://directory.google.com/Top/Games/Video_Games/Roleplaying/Massive_Multiplayer_Online/4th_Series,_The/) . There are many 4thcomming servers with different flavores but like Linux you get what you pay for.

Cheers

---

### Post by bored2k on 2005-07-17
What you need is a Cedega account.

By the way, isn't the poll way too redundant ? I mean, aren't games Applications ? :roll:

Anyways, I'd love to see Bitcomet work on Linux.

---

### Post by Omnios on 2005-07-17
[WIne Home page Ubuntu install with synaptic](http://www.winehq.com/site/download-deb) 

 This should allow an easy way of installing the latest Wine From sourceforge. Personaly there are some things I like to stick to synaptic for downloading and wine was one of them. This greatly eleviates my iffyness of getting it from there as they are for Debian and Ubuntu distros.

---

### Post by professor_chaos on 2005-07-17
My vote is "I don't like wine"

But I use wine currently for running ...M$ Office, Textpad, Topo(a mapping program), dvd_shrink, dvd decrypter.....
But I still don't like wine. I prefer to, when possible, support native versions of software. I play Doom3 and ET, and UT2004 in native formats, and really try hard to dedicate my time and effort to learning and using native programs. 
IIf I vote with my money, and purchase native programs for linux, they will make more.
So while I still use wine (and think its a very valueble program) I hope I won't always need it.

---

### Post by Omnios on 2005-07-18
Personaly my interest in wine is getting my old games working in Linux I have one game nwn that is Linux compliant and probably will buy Linux compliant games in the future. Also I have XP but barely use it any more just mainly to play games that I can not play in Linux. There are a few winX online games that I have played for years and would like to continue playing them. 

 Currently I want to install IE and Windows mediaplayer 9 just for the sole purpose of listening to launchcast radio as it will not play in Linux.

 Also I see wine sort of different and see its future as being called the windows thingy in Linux if it stays free. Years down the road may be an important modual for Linux for those who like it.

---

### Post by Omnios on 2005-07-19
Quick question about installing wine. I backported win to get version= ....419.
 Read a lot of posts recomending using wine-tools to do the isntall. However wine tools in the repository seems to be an older version and says so when you try running wine tools with 419. In the repository it is listed under otherosfs like wine but the main thing is the warning about version numbers when you try to run tools. Im contiplating whether to try wine tools or setuptk as I wan't it to be it in menu and have exe associated with wine exe files so I can double click exe files to launch them.

 Cheers

[Wine Tool home page / supported versions](http://www.von-thadden.de/Joachim/WineTools/index.html#winever)

---

### Post by Omnios on 2005-07-19
Link to thread on how I moutned and set up my vfat Documents drive for wine. It has to be mounted as your username in order to install wine




[Setting Up Vfat partition for use wine as fake windows](http://ubuntuforums.org/showthread.php?t=49830) 

 Cheers

---

### Post by JoeUbuntu on 2005-07-19
I think I will like wine, if I can get it working 100%... I finally got wine working after much hassle (because the latest cvs in the guide, found elsewhere on these forums does not work with the latest wine tools). 

I made an attempt at installing Knights of the Old Republic, however when it asks for CD2, I unmount CD1, insert CD2 and the installer tells me it can't find the second disc, even though I've selected KOTOR_2 in the installer. Any ideas?

---

### Post by Omnios on 2005-07-19
Wierd thing I noticed about never winter nights all 4 cds was the web site stated to use mount and unzip to install. I found I get errors trying to mount the cds and finaly just used /media/cdrom0 unxip.... to install the cds. This brings up a question as to weather how Ubuntu handles cdroms as I also found that when I installed Delta FOrce two it could not detect the Cdrom even though the dist was in the cd rom. This leads me to think this is a Wine Ubuntu compadability issue caused by the different Linux set ups. Wine might be trying to do something pertaining to detecting cd roms such as being set up for other distros which is causing huge problems. Hopefully we can find a solution.

---

### Post by Omnios on 2005-07-20
I downloaded the synaptic backport wine ....419 and read something about wine-tools being a modifed vertion for ubuntu etc. Anyways I tryed setting up wine base set up using wine tools and got a message every 10 second claiming there was a wine server open and this was not nessassarily bad if you have a slow computer or are downloading. Anyways I waited a couple min and it just kept doing that so I killed it. I wanted to use winetools to get a few windows packages that seem to be needed for installing certain programs. Anyways I tryed setting up a fake windows earier with tk and when I launched wintools it gave me an error that no fake windows was found etc.

 Main things I need is a font and DCOM98 and possibly IE 6 to try installing a game to see if I can get it work. The game im trying to get running in wine was on the wine page a long time ago so I know it will work.

---

### Post by artinla on 2005-07-20
I forked out the $ for cedega/Point2play, and haven't regretted it.  Punkbuster doesn't work under wine, nor does ventrilo, but everything else I have tried has worked.

Crossover Office will also let you run many windows apps in linux.  It is a quality product, however IMO is much less appealing now that OpenOffice 2.0 seems to be shaping up so nicely.

My opinion is that wine works fine, but is too hard to manually configure for the average linux newb.

---

### Post by Omnios on 2005-07-21
K kind of got winetools running with ...419 with a hole bunch of regestry errors and also could not get IE to install with winetools. I think this is because I was playing around with configs before getting winetools working. ALyways im going to uninstall it an reinstalling it again with winetools. ALso fonts is Kind of borked and read another post where someone had a link to get links that works properly.

 I did some reading at the Wine page guides and also remember readign that some versions of wine require you to config your regestry. 

 "CD problem solved "" To make your cd work with wine aperently you have to add the unhide your cd rom in fstab otherwise wine wont be able to access it dont have any games that requore a cd to check it out though. 

```
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto,unhide  0       0
``` 

 Hopefully I can get it working properly.

---

### Post by Omnios on 2005-07-21
Im trying to get Wine 20050524 Wine 20050524 and Winetools 2.1.1 backported as I read a post that this version works with winetools. 
[Read it here "Whats with Wine"](http://ubuntuforums.org/showthread.php?t=50036&highlight=wine+winetools) 
All credit goes to them for figuring this out I just read the post! 

 Hopefully this will give us a working version of wine with winetools in backports.

[Backports request link](http://ubuntuforums.org/showthread.php?t=50830)

---

### Post by Omnios on 2005-07-22
The wine 20050524 and Winetools 2.1.1  backport request has been moved to accepted requests so hopefully we will have a working wine with winetools.

 Also keeping with the original theme im including some links to the wine site and wintools which I found realy helpfull. One link is a list of working games and apps.

 [http://www.winehq.com/](http://www.winehq.com/)
 [Wine page/ Documentation very informative](http://www.winehq.com/site/docs/wine-user/index)
 [Wine Page/ DataBase of working apps](http://appdb.winehq.org/appbrowse.php)   
 [Wine tools lots of usefull info](http://www.von-thadden.de/Joachim/WineTools/) 

 Reading these pages gave me an apreciation for wine and what if can do and generaly how it sets up and works. Remember Wine is an Alfa and there are still many problems but the good note is we tend to forget its still an alfa so I can't wait to see the finished product.

---

### Post by JoeUbuntu on 2005-07-23
My wine installs fine after going through a few guides. I'd just love to know how to get the cd to eject when it asks for a cd change.

---

### Post by Omnios on 2005-07-23
[QUOTE=JoeUbuntu]My wine installs fine after going through a few guides. I'd just love to know how to get the cd to eject when it asks for a cd change.[/QUOTE]

 First thought would be to open Computer right click the cdrom and choose eject, I find sometimes this is the only way I can eject a cd even in Linux and the actual button on the cd does not always work.

Edit: Also many of the wine versions work but many games and apps require you to launch IE of have DCOM98  wich can not be installed by some of the wine versions with winetools which will also not install these with certain versions. Im trying to get The 4th Comming working because its a 2d rpg with like 350mhz reuirments working and without DCOM98 it came out with an ubknown exe error then after thatit tryed launching IE which I could not install yet. It has worked in wine before so it it a realistic project as this gam though being old totaly rocks.

---

### Post by JoeUbuntu on 2005-07-23
[QUOTE=Omnios]First thought would be to open Computer right click the cdrom and choose eject, I find sometimes this is the only way I can eject a cd even in Linux and the actual button on the cd does not always work.

Edit: Also many of the wine versions work but many games and apps require you to launch IE of have DCOM98  wich can not be installed by some of the wine versions with winetools which will also not install these with certain versions. Im trying to get The 4th Comming working because its a 2d rpg with like 350mhz reuirments working and without DCOM98 it came out with an ubknown exe error then after thatit tryed launching IE which I could not install yet. It has worked in wine before so it it a realistic project as this gam though being old totaly rocks.[/QUOTE]

I've been searching for ages on the topic, and I found another old post by an ubuntu user, as follows:

"subterrific
12-05-2004, 04:36 PM
When I do that, I still cannot eject the CDROM, nor can I unmount the drive (even as root).

Yeah, --monitor-cdrom-eject doesn't work on Ubuntu because it uses pmount to mount removable media, such as cdroms, automatically. I don't understand the internals, but apparently it isn't compatible with mount/umount

I read in the wine docs that the other way to eject a cd is to send wineserver SIGUSR2, so: "killall -USR2 wineserver" will eject the cd."

Neither of those methods work. Does it have to do with the way ubuntu handles media? I just can't change cd. If I do

sudo eject /media/cdrecorder -m

it ejects, but when I remount cd2 wine doesn't detect it

I've tried everything. I can't be the only ubuntu user having problems in wine installing from more than 1 cd?

---

### Post by Omnios on 2005-07-23
[QUOTE=JoeUbuntu]I've been searching for ages on the topic, and I found another old post by an ubuntu user, as follows:

"subterrific
12-05-2004, 04:36 PM
When I do that, I still cannot eject the CDROM, nor can I unmount the drive (even as root).

Yeah, --monitor-cdrom-eject doesn't work on Ubuntu because it uses pmount to mount removable media, such as cdroms, automatically. I don't understand the internals, but apparently it isn't compatible with mount/umount

I read in the wine docs that the other way to eject a cd is to send wineserver SIGUSR2, so: "killall -USR2 wineserver" will eject the cd."

Neither of those methods work. Does it have to do with the way ubuntu handles media? I just can't change cd. If I do

sudo eject /media/cdrecorder -m

it ejects, but when I remount cd2 wine doesn't detect it

I've tried everything. I can't be the only ubuntu user having problems in wine installing from more than 1 cd?[/QUOTE]


 Not shure if this works as im waiting for a new backported version of wine till I try stuff out. A few posts up mentions that I read the the documention on the wine site pertaining to cd's and as wine is set up it will not detect your cd unless it is unhidden. Your fist cd is lauched my navigating the cd and launching it with wine however this will come into affect with the second cd as wine is looking for it. I had the same problem with Delta Force 2 which needs to read the cd for copy right protect and would not. I will also check this out when I get the new backport. Try unhiding your cd in fstab and see if that helps

---

### Post by JoeUbuntu on 2005-07-23
[QUOTE=Omnios] Try unhiding your cd in fstab and see if that helps[/QUOTE]

The fstab entry for my cd drive is already as follows:

/dev/hdc /media/cdrecorder udf,iso9660,ro,user,noauto,unhide

So it doesn't seem to do anything  ](*,)

---

### Post by carlc on 2005-07-24
Has anyone got Quicken to run with wine? I have tried and get this error:

carlc@blackbox13:~$ wine "/media/windows/Program Files/Quicken/qw.exe"

Invoking /usr/lib/wine/wine.bin /media/windows/Program Files/Quicken/qw.exe ...

err:module:import_dll Library MFC71.DLL (which is needed by L"Z:\\media\\windows \\Program Files\\Quicken\\qw.exe") not found

err:module:import_dll Library MSVCR71.dll (which is needed by L"Z:\\media\\windo ws\\Program Files\\Quicken\\qw.exe") not found

err:module:LdrInitializeThunk Main exe initialization for L"Z:\\media\\windows\\ Program Files\\Quicken\\qw.exe" failed, status c0000135

Wine failed with return code 1
Warning: Missing charsets in String to FontSet conversion
Warning: Unable to load any usable fontset

---

### Post by JoeUbuntu on 2005-07-25
Hi guys,

I have had limited success with installing games from multiple cd's as of today - I forgot I had another cd drive, so if I put the 2nd cd in my other drive when prompted, it accesses that disk fine! I know cedega is perfectly fine with ejecting cd's, as it uses it's own cd management thingie (I'm not up on the technical things with it). 

Is that going to be implemented in wine in the future? I can't use cedega, because after wineX 3.3.2, support for ATI cards (in pthreading) was broken in the ATI drivers (see this post :[http://www.transgaming.com/showthread.php?msg=41163&forum=1262&thread=41163](http://www.transgaming.com/showthread.php?msg=41163&forum=1262&thread=41163) 

I guess I'm limited to 2cd games, then  [-X

---

### Post by Boggles3 on 2005-07-25
hey man im havent run into this problem cuz i have an nvidia card and you can eject and insert and then continue with that..
but i would like to let you know that i have seen answers for this problem in forums and i think there is a how to posted in the ubuntu gaming forums somewhere..
just letting you know in case you havent checked.. good luck:)

---

