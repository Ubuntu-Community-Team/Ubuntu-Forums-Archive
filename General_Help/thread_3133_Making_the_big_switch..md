---
title: "Making the big switch."
date: 2004-11-03
forum: General Help
---

### Post by TravisNewman on 2004-11-03
OK I want to completely get away from Windows if I can. I already have mostly. There are a few things holding me back, and Ubuntu has alleviated a lot of them already. I'm genuinely looking for advice here, so if it seems like I'm bashing anything (other than Windows) I'm not, I swear.

Resolved:
[INDENT]*First off, I have an HP Deskjet 712C that I can't get to work with any of the print utilties I've tried in ANY distro (except Mandrake, oddly enough, that picked it right up. Kinda odd that the WORST distro I've used in my opinion would do that). Does anyone have this printer (or a 710 series) that they know how to set up?*[/INDENT]

Second, I have a palm m515 that I just recently got working with Ubuntu. This was a first. I had followed the instructions in Fedora, Mandrake, and Gentoo and gotten nowhere. Now my question, what are some good programs to sync with? Obviously Evolution for a few things, but it doesn't pick up the expense, email, or memos.

Third, is there a single freakin program for linux that can transfer files reliably to AIM, MSN, Yahoo!, and ICQ? I don't care if I have to use 4 different programs, or even the official clients (if there even are any anymore), I'll just switch over when I need to send a file, which I already do in Windows. Gaim's file transfer isn't very reliable. It would be good to note here that I'm behind a NAT router, so if there's a way to make any of the common programs work around a router reliably, that'll be great. Also of note here is that my Fiancee and my Webserver (or soon to be webserver) are on the same network, and my Fiancee uses file transfer as well, and when I'm doing work on this one, I use the soon-to-be webserver for chatting, etc. So if there's a tutorial for configuring MULTIPLE computers running gaim/licq/kopete/whatever clients for file transfers, that would be great.

Resolved as much as it's going to be I think:
[INDENT]
[I]Fourth, as a hobby, I do a lot of web design. I'd like a CSS editor as capable as Bradbury Topstyle if one is available. That's an amazing program. I'd also like to get into flash design a bit, and I don't think I've ever seen a flash designer for Linux, but I'm just curious about that one.
Edit: I've heard a lot of suggestions on some programs, but I'd still like to hear some more.[/I][/INDENT]

Resolved:
[INDENT]*Fifth, kinda on the same idea as the last one, when I'm uploading files to my webspace, I use Filezilla in Windows. gFTP is pretty awesome, so I'm pretty satisfied, I'm just wondering if there's anything better (in your opinion, obviously)*[/INDENT]

Very thoroughly resolved (I have about all the Wine/WineX resources I could ever need now):
[INDENT][I]Sixth, I've dropped a lot of money on PC games over the years. Is there any website with a games database explaining how to get them working with WineX? Like a Linux gaming forum with howtos? Also, is there an Ubutu/Debian how-to for installing WineX over CVS?
Edit: Gotten a lot of help on this one, but any info is great[/I]. [/INDENT]

*phew* that was a mouthful. To conclude, 1 and 3 are the only ones really holding me back, because whenever I want to send a file or print I have to go into Windows. The others are just requests for advice. Again, I'm not trying to be nasty or bash anyone for lack of support-- I know HP, AOL, etc all use proprietary techniques, so it's impossible to have 100% compatibility. I'm basically just looking for workarounds, because I seem to get things done faster and more enjoyably in Linux. Especially Ubuntu. Sorry about the long winded post, I just hope you had the stamina to get through this (I didn't. I had to stop and re-read what I'd already written. Damn ADD. And I'm serious there, I do have ADD, so if things seem slopped together, it's to be expected. ;))

---

### Post by adbak on 2004-11-03
For number 1, you need to open Synaptic or use Apt to open up the Universe repositories.  Then refresh the lists and search for cupsys-driver-gimpprint and cupsys-driver-gimpprint-data.  Install both and you should be able to get your printer working again.

As for the other ones, I can't help you.

---

### Post by TravisNewman on 2004-11-03
[QUOTE=adbak]For number 1, you need to open Synaptic or use Apt to open up the Universe repositories.  Then refresh the lists and search for cupsys-driver-gimpprint and cupsys-driver-gimpprint-data.  Install both and you should be able to get your printer working again.

As for the other ones, I can't help you.[/QUOTE]
 That didn't seem to change anything. It seems like it's connecting to it correctly, but it just won't print anything. It's trying to use a network printer, even though it's not a network printer, it's connected to the parallel port. Whenever I tell it to be local, it changes back to network.

---

### Post by TravisNewman on 2004-11-03
[QUOTE=panickedthumb]That didn't seem to change anything. It seems like it's connecting to it correctly, but it just won't print anything. It's trying to use a network printer, even though it's not a network printer, it's connected to the parallel port. Whenever I tell it to be local, it changes back to network.[/QUOTE]
 Wahoo! I got it working. I had to remove the printer and then re-add it. I may have been an idiot when installing it. Thanks for the help adbak.

Now, Palm Sync, IM transfers, CSS Editor, FTP client, PC games.
Anyone? :)

---

### Post by im_ka on 2004-11-03
gftp is the best ftp client imho

---

### Post by TravisNewman on 2004-11-03
[QUOTE=im_ka]gftp is the best ftp client imho[/QUOTE]
 That's what I figured. Except wget, and the other command line tools that have become necessary (for me at least). Graphical tools are just more convenient sometimes. Thanks im_ka!

2 down :)

---

### Post by jwb on 2004-11-03
[QUOTE=panickedthumb]Wahoo! I got it working. I had to remove the printer and then re-add it. I may have been an idiot when installing it. Thanks for the help adbak.

Now, Palm Sync, IM transfers, CSS Editor, FTP client, PC games.
Anyone? :)[/QUOTE]

FTP- try gFTP. Simple, easy to use.

CSS- I use Bluefish for most of my HTML and CSS, though I use Komodo for work projects. I like TopStyle (I liked Homesite back in the day when Nick developed that too...... ever use Homestyle 1.2?) I haven't found something to compare with TS. However, Bluefish does CSS syntax checking, and I've found that by writing the style manually, I end up going just as fast. Not much of an answer..... "Do it yourself".... I know. But between that and 
[this W3C reference on CSS](http://www.w3schools.com/css/css_reference.asp) I end up writing it all manually without missing TopStyle.

PC Games- this is probably flame bait..... *but*...... I gave up with the hassle of Linux Gaming (TM). I play games for fun, and I'm lazy. I want to buy it, install it, and blow stuff up. Transgaming has some stuff you may want to look at, and many people have great luck with it. ([http://www.transgaming.com/products_linux.php](http://www.transgaming.com/products_linux.php)) Like I said, I'm lazy...... so I keep an XP box for gaming. Or buy games made to run on Linux..... there are a few- Doom 3 I believe is one. Or get real excited about Tux Racer, Frozen Bubble, and Pingus. Yes, they are fun games. No, they are not SW Battlefront or Far Cry.

The rest..... I don't know what to tell you, don't use them that much if ever.

---

### Post by im_ka on 2004-11-03
[QUOTE=panickedthumb]That's what I figured. Except wget, and the other command line tools that have become necessary (for me at least). Graphical tools are just more convenient sometimes. Thanks im_ka!

2 down :)[/QUOTE]

you've got a pm ;)

---

### Post by TravisNewman on 2004-11-03
[QUOTE=jwb]FTP- try gFTP. Simple, easy to use.[/quote]
Yeah I've been using it. Just wondering if there was something phenomenal out there.

[QUOTE=jwb]CSS- I use Bluefish for most of my HTML and CSS, though I use Komodo for work projects. I like TopStyle (I liked Homesite back in the day when Nick developed that too...... ever use Homestyle 1.2?) I haven't found something to compare with TS. However, Bluefish does CSS syntax checking, and I've found that by writing the style manually, I end up going just as fast. Not much of an answer..... "Do it yourself".... I know. But between that and 
[this W3C reference on CSS](http://www.w3schools.com/css/css_reference.asp) I end up writing it all manually without missing TopStyle.[/quote]
I'll give all those a shot. Basically I use TopStyle for stuff I didn't originally write from scratch myself, so I don't know what it all does yet.

[QUOTE=jwb]PC Games- this is probably flame bait..... *but*...... I gave up with the hassle of Linux Gaming (TM). I play games for fun, and I'm lazy. I want to buy it, install it, and blow stuff up. Transgaming has some stuff you may want to look at, and many people have great luck with it. ([http://www.transgaming.com/products_linux.php](http://www.transgaming.com/products_linux.php)) Like I said, I'm lazy...... so I keep an XP box for gaming. Or buy games made to run on Linux..... there are a few- Doom 3 I believe is one. Or get real excited about Tux Racer, Frozen Bubble, and Pingus. Yes, they are fun games. No, they are not SW Battlefront or Far Cry.
[/quote]
Yeah, probably flame bait. *L* I don't have an extra machine, so it'd involve restarting into xp. I wish you could get free conversion packs or installers for games you already own. Doom 3 comes to mind. I have the Win version, but not the linux version.

[QUOTE=jwb]
The rest..... I don't know what to tell you, don't use them that much if ever.[/QUOTE]
That's fine, you've been great. Thanks a lot!

---

### Post by jdodson on 2004-11-03
[QUOTE=panickedthumb]
Now, Palm Sync, IM transfers, CSS Editor, FTP client, PC games.
Anyone? :)[/QUOTE]

ok palm sync, cant help, im transfers.... well you could use [kopete](http://kopete.kde.org/) just apt-get it from universe, betcha its there and it might support file transfers better, though i have no idea for sure.

what pc games do you want to play?  if you just want to rock starcraft or war3 i think wine plays those games fine as is.  as far as winex you can download the CVS version, [here is a nice google search for you](http://www.google.com/search?q=winex+cvs+howto&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox-a&rls=org.mozilla:en-US:official) to help get things going.  i would try the ubuntu wine package first(if one exists) first and then winex next.  plus if the games you want to play are: neverwinter nights, unreal tournament, 2003, 2004 or doom3 or quake3 or wolfienstien enemey territory or americas army, rest assured they all have linux ports.  unreal games have linux install scripts on the win cds and wolf. enemy territory and americas army are both completley free of charge and avail for download.

---

### Post by jdodson on 2004-11-03
[QUOTE=panickedthumb] Doom 3 comes to mind. I have the Win version, but not the linux version.
[/QUOTE]

you are in luck, [check this out.](http://zerowing.idsoftware.com/linux/doom/).

btw this goes out to everyone, a simple google search goes a really REALLY long way.  i found this info in less than 1 minute. ;-)

---

### Post by ulrich on 2004-11-03
[http://frankscorner.org/](http://frankscorner.org/) has some tuts on wine and games.
should also apply to wineX.
theres also a howto for cedega-cvs.

for your messenger-thing: i know that yahoo is having a linux-client ready.

css: bluefish and screem have some css-wizards/advanced tools, but none of them is like topstyle. i think coding by hand is what you get :) 
a good powertoy is the 'webdeveloper' extension for firefox. has some really neat functions. (especially for css)
flash + linux  = no way.
there are ways to get flash working with wine, but its more like a pain in the *ss in my opinion. not really usable, though my experience is more than half a year ago. 
so maybe there has something changed? 
theres also an flash4linux-project on sourceforge but last time i checked it seemed dead and the program wasnt the usable. though a really nice effort!

---

### Post by TravisNewman on 2004-11-03
[QUOTE=jdodson]you are in luck, [check this out.](http://zerowing.idsoftware.com/linux/doom/).

btw this goes out to everyone, a simple google search goes a really REALLY long way.  i found this info in less than 1 minute. ;-)[/QUOTE]

Yeah I HAD searched, but it was about a month ago. Thanks much.

---

### Post by TravisNewman on 2004-11-03
[QUOTE=ulrich][http://frankscorner.org/](http://frankscorner.org/) has some tuts on wine and games.
should also apply to wineX.
theres also a howto for cedega-cvs.

for your messenger-thing: i know that yahoo is having a linux-client ready.

css: bluefish and screem have some css-wizards/advanced tools, but none of them is like topstyle. i think coding by hand is what you get :) 
a good powertoy is the 'webdeveloper' extension for firefox. has some really neat functions. (especially for css)
flash + linux  = no way.
there are ways to get flash working with wine, but its more like a pain in the *ss in my opinion. not really usable, though my experience is more than half a year ago. 
so maybe there has something changed? 
theres also an flash4linux-project on sourceforge but last time i checked it seemed dead and the program wasnt the usable. though a really nice effort![/QUOTE]

Yeah I love the webdeveloper extension. Flash, I knew, was a long shot. I never expected it to work. I'll play with Yahoo's official client later and see what I think. 

You guys all kick ass. I love the community here.

---

### Post by jdodson on 2004-11-03
[QUOTE=panickedthumb]Yeah I HAD searched, but it was about a month ago. Thanks much.[/QUOTE]

no problem, and if memory serves a month ago they didnt have this(i.e. the released it a few weeks ago) :mrgreen:

---

### Post by fng on 2004-11-03
I recently discovered screem ([http://www.screem.org](http://www.screem.org)) for php/css-editing.

---

### Post by Nis on 2004-11-03
[QUOTE=panickedthumb]I wish you could get free conversion packs or installers for games you already own. Doom 3 comes to mind. I have the Win version, but not the linux version.
[/QUOTE]
Most games that have native Linux versions have either the clients on the CDs or downloadable clients (not warez or such, check [http://icculus.org](http://icculus.org)).  I know id provides downloadable Linux clients for Doom 3 and Return to Castle Wolfenstein and there's a Linux client on the UT2003 CDs (not sure about UT2004 but should be similar).  Bioware also has a downloadable Linux client for Neverwinter Nights.

I've never been a big fan of WineX/Cedega.  I used to subscribe but the only game I ever got working really well was Black & White.  And after that worked well Roller Coaster Tycoon stopped working so well.  So I guess using WineX/Cedega means you have a trade off.  Transgaming has just released a demo version of Cedega so you can download that and see how it works with your games.  If it provides what you're looking for than go that route.  Myself, I decided to get an XBox since it should be able to run Doom 3 better than my box can.  Also some of the XBox games aren't that bad.  It sure beats buying a copy of Windows and dealing with all the troubles that come with that. ;)

---

### Post by FLeiXiuS on 2004-11-03
I would suggest all of those who want to use windows applications on linux to use Wine / Wine-X.

Wine: [http://winehq.com](http://winehq.com)
Wine-X: [http://transgaming.com](http://transgaming.com)

---

### Post by cacofonix on 2004-11-03
[QUOTE=panickedthumb]
Yeah, probably flame bait. *L* I don't have an extra machine, so it'd involve restarting into xp. I wish you could get free conversion packs or installers for games you already own. Doom 3 comes to mind. I have the Win version, but not the linux version.

[/QUOTE]

if you go [here](http://zerowing.idsoftware.com/linux/doom/)  you can get the linux installer for doom3 its not optimized very well and doesnt work at all with the fglrx drivers.


cacofonix

---

### Post by jeremy on 2004-11-04
For CSS have you tried decss?

---

### Post by fng on 2004-11-04
[http://appdb.winehq.com/appbrowse.php?catId=2](http://appdb.winehq.com/appbrowse.php?catId=2)

Wime application database that allready helped me alot getting some games to work.

---

### Post by TravisNewman on 2004-11-04
Jeremy: No, never tried it. It doesn't seem useful for my purposes.
fng: Thank you :) Bookmarked! And yes, I've been using screem a bit as well. Nifty.
cacofonix: thanks, but jdodson already pointed me in the right direction for the doom3 installer.
Nis: icculus is going to come in handy! Thanks very much!

You guys rock. I've never gotten this much help so fast anywhere. Even the gentoo forums that are supposed to be the best.

---

### Post by jwenting on 2004-11-04
[QUOTE=jeremy]For CSS have you tried decss?[/QUOTE]
 Was that in jest or serious?

CSS is a webpage makeup language (though it has more purposes than just that), stands for Cascading Style Sheets.

deCss is a tool to crack DVD encryption, something completely different.

AFAIK there's no real alternative to TopStyle Pro under *nix, nothing I've seen even comes close to the functionality and userfriendliness.

---

### Post by mercurus on 2004-11-04
I have an HP DeskJet 710C that I configured quite easily for Debian, but I have since moved it back to a windows box. The printing was painfully slow both across the network, and locally - I believe it was related to the speed of the machine and its heavy workload. (A 233 w\ 32 doing routing, firewalling, httpd, nfsd, nis domain serving, samba, cups, exim, bind, squid, and a few others) That said, I was able to share it with Samba, and give both MS and UNIX clients access to the printer. I still recommend linuxprinting.org for any printer issues ...

I'm afraid I've no Palm, and hence no experience there.

I can't go past gFTP, it really is without peer as far as I've seen. 

I have budget-spec machine (Duron 700 w\368 and a 32 MB Geforce 2MX) and limited inclination to play FPS, so I've not really messed around with Linux Gaming. That said, I did install all three quakes at various stages and they worked admirably. I definately had better Quake 2 performance under Linux than I did under Windows 2000. In fact, I think I bettered my FPS rate in Linux than under WinXP SP1 - but don't quote me on that. My favourite though was being able to backup data to CD in one drive, and play Quake 2 (taking music from a CD in the second optical drive) without performance loss - not something that happens under Windows. I did have some ALSA issues with Quake 3 that meant I had no sound, or sound, and no go. I would imagine they have been reoslved in Ubuntu though. I'm very happy with the nVidia drivers for X, and I strongly endorse the wine and WineX resources people have provided - especially Frank's Corner.

Cheers
mercurus

---

### Post by Slapdash on 2004-11-04
[QUOTE=ulrich]
flash + linux  = no way.
[/QUOTE]


 :-D  [CHECK THIS OUT](http://www.google.com/search?q=flash+on+linux&start=0&start=0&ie=utf-8&oe=utf-8&client=firefox-a&rls=org.mozilla:en-US:official)

---

### Post by TravisNewman on 2004-11-04
[QUOTE=jwenting]Was that in jest or serious?

CSS is a webpage makeup language (though it has more purposes than just that), stands for Cascading Style Sheets.

deCss is a tool to crack DVD encryption, something completely different.

AFAIK there's no real alternative to TopStyle Pro under *nix, nothing I've seen even comes close to the functionality and userfriendliness.[/QUOTE]

There's another tool called DeCSS that allows you to strip css from html documents. I think he called it DeCSS just to freak out the MPAA until they realized it wasn't THE DeCSS.

[http://pigdog.org/decss/](http://pigdog.org/decss/)

---

### Post by jeremy on 2004-11-04
[QUOTE=jwenting]Was that in jest or serious?

CSS is a webpage makeup language (though it has more purposes than just that), stands for Cascading Style Sheets.

deCss is a tool to crack DVD encryption, something completely different.

AFAIK there's no real alternative to TopStyle Pro under *nix, nothing I've seen even comes close to the functionality and userfriendliness.[/QUOTE]
 sorry, I got it twisted in my (twisted) brain, I meant CSSED, [http://cssed.sourceforge.net/](http://cssed.sourceforge.net/) , it doesn't have all the great features of topstyle, but it isn't at all bad.

---

### Post by TravisNewman on 2004-11-07
OK guys, one more question. I have officially decided to delete my windows partition altogether. i don't use it, so why keep it? Now, I want to resize my linux partition to fill up that space left by windows, so that's going to change the partition numbers isn't it? /dev/hda1 is now my windows drive, and /dev/hda2 is linux. Just FYI, hda3 is swap and hda4 is storage so I don't lose everything if something dies. I keep downloads, pictures, music, etc here. So...

1. Is there a Linux app that will let me partition easily?
2. What do I have to do to make my system bootable after the partition numbers change?

Thanks for your help guys

---

