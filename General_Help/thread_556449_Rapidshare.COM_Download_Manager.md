---
title: "Rapidshare.COM Download Manager"
date: 2007-09-21
forum: General Help
---

### Post by phissen on 2007-09-21
I tried wellget, some scripts from net but nothing works very well :(

Anyway, i need some download manager who can download link**s** from rapidshare.com. like flashget - can remember username & pass and can download files one after another (all i need) :)

thanx. :)

---

### Post by phissen on 2007-09-22
anyone...any idea?

btw. i need to download some stuff.... :lolflag:

---

### Post by loell on 2007-09-22
i don't know if its possible, i think rapidshare is using redirect or rather dynamically loading a url download.

---

### Post by bren21 on 2007-09-28
I'm looking for one as well. All the ones I've tried are half as fast as I can download them in windows. By the way, if there is no login, simply copy all the links into gedit and paste username:password@rapidshare.com/file... and then add those links to the download manager

---

### Post by Skimi on 2007-10-01
I want it too... that's the only reason i have to use windows... Rapidshare download's...

---

### Post by Karahana on 2007-10-01
Google for Universal Share Downloader and try using it with WINE! :) I used it a while back on 'doze and it had frequently updated plugins that always got over rapidshare's protection.  I decided not to be lazy and googled it for you : [http://www.dimonius.ru/](http://www.dimonius.ru/). The site is in Russian but it translates well with Google or Babelfish. Good luck! Btw, if you manage to get it working with WINE and there is something "special" that needs to be done, post here so other people can use it if they ever need to! :D

---

### Post by kris2pe on 2007-10-01
Use Vmware or Virtualbox! 
Then configure it to seamless mode.
Trust me Windows, sad to say has the best download manager & torrent managers around!

---

### Post by Karahana on 2007-10-01
1st of all, OT... 

> **kris2pe said:**
> .
Trust me Windows, sad to say has the best download manager & torrent managers around!

Well I beg to differ. rTorrent is the best torrent client I used and I've been using uTorrent a lot... :)  As for download managers, well who really needs them? There are a bunch of FF extensions (like USD) and they do the job. The only thing linux is missing is a decent GUI FTP client!

---

### Post by SreckoMicic on 2007-10-05
Download [rapget]("http://www.rapget.com/en/") (it is for Win), and launch it via Wine.
Works for me like :KS charm.:KS

---

### Post by kris2pe on 2007-10-07
> **Karahana said:**
> 1st of all, OT... 
Well I beg to differ. rTorrent is the best torrent client I used and I've been using uTorrent a lot... :)   
Have not tried it! But if this is NOT GUi base? Why would I use it when I can get a gui based, easy to use on XP?
> **Karahana said:**
> 
As for download managers, well who really needs them?
This is why ppl don't like using Linux. This careless disdain for other users!

---

### Post by RobotJox on 2007-10-15
d4x works with rapidshare - or rather "worked" until Gutsy came along - there's a bug in gutsy or d4x that adds an extra slash in filenames that you try to download from rs.

 So if you're still using Feisty install d4x - it works perfectly with flashgot and rs.

---

### Post by Marquis_de_Carabas on 2007-10-29
D4x and FlashGot was a perfect combination - FlashGot passes the cookies to D4x so you're logged in to Rapidshare automatically, and D4x downloads quickly and simply. The only thing you had to watch out for was when sites have links listed with .html on the end as you then end up downloading two copies of every file.

But Gutsy broke it! I've tried installing older versions of d4x and d4x-common but there is still the same problem, so I assume it must be an issue with one of the libraries it depends on. Unfortunately there's quite a few of those (see [http://packages.ubuntu.com/feisty/net/d4x](http://packages.ubuntu.com/feisty/net/d4x)) and I'm not sure I can be bothered to install older versions of all of them...

Edit: Thanks SreckoMicic, RapGet does indeed work like a charm. I'll be glad when D4x works again, but in the meantime this will do very well indeed.

---

### Post by ariel on 2007-10-29
> **Karahana said:**
> 1st of all, OT... 



Well I beg to differ. rTorrent is the best torrent client I used and I've been using uTorrent a lot... :)  As for download managers, well who really needs them? There are a bunch of FF extensions (like USD) and they do the job. The only thing linux is missing is a decent GUI FTP client!

Let me suggest: filezilla; you can find it in gutsy repos

---

### Post by in_rainbow on 2007-11-05
I had the same problem. Here's the best solution I've tried.

1. Install KGet

2. Install Konqueror.

3. Install the FlashGot Firefox extension.

4. Log into your rapidshare premium account in Konqueror. (KGet shares cookies with Konqueror.)

5. Configure FlashGot to use KGet as download manager.

6. Right click on the list of rapidshare links in Firefox and got to 'FlashGot Selection'.

All the links should be added to Kget and automatically start downloading.

Woohoo!

---

### Post by janfsd on 2007-11-15
> **Marquis_de_Carabas said:**
> D4x and FlashGot was a perfect combination - FlashGot passes the cookies to D4x so you're logged in to Rapidshare automatically, and D4x downloads quickly and simply. The only thing you had to watch out for was when sites have links listed with .html on the end as you then end up downloading two copies of every file.

But Gutsy broke it! I've tried installing older versions of d4x and d4x-common but there is still the same problem, so I assume it must be an issue with one of the libraries it depends on. Unfortunately there's quite a few of those (see [http://packages.ubuntu.com/feisty/net/d4x](http://packages.ubuntu.com/feisty/net/d4x)) and I'm not sure I can be bothered to install older versions of all of them...

Edit: Thanks SreckoMicic, RapGet does indeed work like a charm. I'll be glad when D4x works again, but in the meantime this will do very well indeed.

I got similar problems opening files with mplayer. I am just guessing but you could try editing /usr/share/applications/d4x.desktop and change %U with %F in the exec= line.

---

### Post by Marquis_de_Carabas on 2007-11-15
> **janfsd said:**
> I got similar problems opening files with mplayer. I am just guessing but you could try editing /usr/share/applications/d4x.desktop and change %U with %F in the exec= line.

Thanks for the suggestion, but unfortunately the same problem remains even after trying that.

---

### Post by janfsd on 2007-11-15
> **Marquis_de_Carabas said:**
> Thanks for the suggestion, but unfortunately the same problem remains even after trying that.

I think it was another kind of error, so that won't help. I just tried it and saw problem.
You can try filling a bug report...
His web is [http://www.krasu.ru/soft/chuchelo/](http://www.krasu.ru/soft/chuchelo/)
It seems the author is making a new one, so you could try to write him an e-mail with the issue.

EDIT: I've found a fix: [https://bugs.launchpad.net/ubuntu/+source/d4x/+bug/155368](https://bugs.launchpad.net/ubuntu/+source/d4x/+bug/155368)
Get there and grab the deb, or just modify the source and compile, it should work now!

---

### Post by Sh@m@n on 2007-11-15
> **phissen said:**
> I tried wellget, some scripts from net but nothing works very well :(

Anyway, i need some download manager who can download link**s** from rapidshare.com. like flashget - can remember username & pass and can download files one after another (all i need) :)

thanx. :)

sudo apt-get install aria

---

### Post by Marquis_de_Carabas on 2007-11-15
> **janfsd said:**
> EDIT: I've found a fix: [https://bugs.launchpad.net/ubuntu/+source/d4x/+bug/155368](https://bugs.launchpad.net/ubuntu/+source/d4x/+bug/155368)
Get there and grab the deb, or just modify the source and compile, it should work now!

Thank you! Now I can delete Rapget, which was working okay but leaving annoying little windows which refused to minimise littering my desktop :)

---

### Post by whazooo on 2007-12-16
Classic flashget 1.73 
it works perfectly with gutsy and wine

---

### Post by Azathoth_ on 2007-12-16
> **whazooo said:**
> Classic flashget 1.73 
it works perfectly with gutsy and wine

Really??? I can run this application but i cannot download any file. I have added my premium accounts of rapidshare and megaupload but if i add any [www.megaupload.com](www.megaupload.com) or rapidshare.com file it never begin,

I have tried it with rapidget (some versions) and flashget and i cannot download any file.

Please, anyone could help me???? I have to use windows to download a list of files

---

### Post by dethredic on 2007-12-20
> **in_rainbow said:**
> I had the same problem. Here's the best solution I've tried.

1. Install KGet

2. Install Konqueror.

3. Install the FlashGot Firefox extension.

4. Log into your rapidshare premium account in Konqueror. (KGet shares cookies with Konqueror.)

5. Configure FlashGot to use KGet as download manager.

6. Right click on the list of rapidshare links in Firefox and got to 'FlashGot Selection'.

All the links should be added to Kget and automatically start downloading.

Woohoo!

Ok I did this, and everything worked fine. But now like 5 days later this does not work. Well, all the files get added to KGet, but they finish in 1 second, and they are all 5.6Kb and have the extension .rar but they are actually .html files. Weird, anyone else had this problem?

---

### Post by janfsd on 2007-12-20
> **dethredic said:**
> Ok I did this, and everything worked fine. But now like 5 days later this does not work. Well, all the files get added to KGet, but they finish in 1 second, and they are all 5.6Kb and have the extension .rar but they are actually .html files. Weird, anyone else had this problem?
Maybe the files were deleted? or you have already passed the 25 GB limit without noticing? Try to download the same files within firefox to see if you can.

---

### Post by dethredic on 2007-12-20
Yes it works when I copy and paste the link in.

---

### Post by Chal on 2007-12-21
just google for jdownloader

its a nice java rapidshare and other downloader with automatic captcha thing

and the best is you open it with a bookmark in your browser and don't have to install it ;)

---

### Post by dethredic on 2007-12-21
ok cool.

Thanks for this.

Umm, I can't find it. Link please

---

### Post by Chal on 2007-12-21
if you mean the jdownloader

here is the webstart link with this you can open jdownloader via browser:
[http://jdownloaderwebstart.ath.cx/]("http://jdownloaderwebstart.ath.cx/")
i just set a bookmark in my browser for this

but there is a prob for me cuz i used this a long time ago and it doesnt work for me now

just try it and if there is a prob download it and istall it by open the 
JDownloader.jar

[http://jdownloaderinstall.ath.cx/]("http://jdownloaderinstall.ath.cx/")

hope it works for you

---

### Post by Marquis_de_Carabas on 2007-12-21
> **dethredic said:**
> Umm, I can't find it. Link please

[http://jdown.cwsurf.de/](http://jdown.cwsurf.de/)

I gave it a quick try but my German is pretty shaky (I can order a veggie burger in McDonalds, and I can say "I speak a little bit of German" but that's about it) and I haven't been able to find an English version of the program. The D4X solution is still working perfectly for me anyway (with just one slight problem which is that Update Manager constantly prompts me to 'update' it to the same version number, but I can live with that little niggle).

(Edit: Chal beat me to it :) )

---

### Post by Chal on 2007-12-21
just saw that there is only a german langagefile in the package 

hm thougt i had it in english

as i said i used it a long time ago

next time i will try the things before i post sorry ;)

---

### Post by dethredic on 2007-12-21
Darn, ohh well

Still looking for other solutions.

---

### Post by dethredic on 2007-12-21
Ok, I e-mailed the rapidshare suppot and they were no help at all.

They didn't even address the fact that I was on ubuntu and just copyed and pasted in the part of the FAQ, although I insisted in my e-mail that I had read it, and it did not realate to my problem.

This is really weird. This happened before, until I hit 25 gigs, now it has gone down and I still can't download.

---

### Post by Azathoth_ on 2007-12-24
:(

If anyone find any working software, please let us know

---

### Post by Azathoth_ on 2007-12-24
I think i finally have it:

- If we use GNOME: we can install d4x but this one (solved issue on "/" ):[http://rapidshare.com/files/67726078/d4x_2.5.7.1-4ubuntu1_i386.deb.html](http://rapidshare.com/files/67726078/d4x_2.5.7.1-4ubuntu1_i386.deb.html)  according to this issue: [https://bugs.launchpad.net/ubuntu/+source/d4x/+bug/155368](https://bugs.launchpad.net/ubuntu/+source/d4x/+bug/155368)

- Now we must have firefox and the addon flashgot. After reboot firefox, we should type in the addres bar:** about:config**
Find **flashgot.rsPremium**  and change *false* to *true*

- Now, we must long in in rapidshare premium, megaupload premium, .... and after we can select links and shoose **"Flashgot Slection"** if we previusly have choosen **d4x** in the list of flashgot downloader.

:D

---

### Post by phissen on 2007-12-27
hello people xD
i was using xp this few month because of rapidshare ofcourse (I couldn't find working download manager :confused:), yesterday I give a second try to ubuntu - and i found "Aria" - the best download manager for rapidshare :)

tnx. to ubuntu community :mrgreen:

I stay at Linux, one Linux user more :)

---

### Post by Chal on 2007-12-27
thanx for this

here is the link:
[http://aria2.sourceforge.net/]("http://aria2.sourceforge.net/")

-------------edit-------------------
lol just install it with
sudo apt-get install aria2

hehe

but how do i get the rapidshare captchas working with this?

---

### Post by phissen on 2007-12-27
> **Chal said:**
> but how do i get the rapidshare captchas working with this?

:confused: - for PREMIUM accounts there is no captcha :confused:

if you think "cheat" rapidshare as free user and download "as premium" - you can't ;)

---

### Post by Chal on 2007-12-27
i don't want to cheat rapidshare this way (to get premium account or whatever)

i just don't want to enter the captchas everytime and there are downloaders which enter the captchas for you like cryptload in win

the problem when u have to enter the captcha manually is that u cant let the comp download over night when u don't need it

---

### Post by andrek on 2008-01-04
Rapget works great with wine.

---

### Post by pedja_portugalac on 2008-01-04
Hi everybody 
I have just found link on which a guy is claiming knowing how to set up wget the way it'll accept rapidshare downloads for premium users. I have tested first step of creating cookie but may-be I was wrong somewhere. The procedure and also script which he have made looks ok to me but then again I would like to ask for the opinion somebody with more experience then mine. There is also 3 comments favorable to this method. This is link with instructions and the script for download: [http://nerdplanet.co.uk/index.php?option=com_content&task=view&id=50&Itemid=63&limit=&limitstart=&mosmsg=Thanks.+Your+comment+has+been+successfully+saved](http://nerdplanet.co.uk/index.php?option=com_content&task=view&id=50&Itemid=63&limit=&limitstart=&mosmsg=Thanks.+Your+comment+has+been+successfully+saved).

PS. The script file is 2.5mb just because there is pdf book together with script and the book is about installing RH server. Don't worry, there's no viruses or other malware inside. I have checked .rar content with clamav and also have a look at the script. It'll be nice if you find this method working to make some tutorial for the rest of us. :):lolflag:

---

### Post by kossik on 2008-03-02
Try rapidshare-dl .. I am using and it works fine to me..
link : [http://mundogeek.net/rapidshare-dl/](http://mundogeek.net/rapidshare-dl/)

---

### Post by GabrielWolff on 2008-06-04
> **kossik said:**
> Try rapidshare-dl .. I am using and it works fine to me..
link : [http://mundogeek.net/rapidshare-dl/](http://mundogeek.net/rapidshare-dl/)

Works like a charm for me :)

Thanks!

---

### Post by janfsd on 2008-06-05
Does rapidshare-dl has multisource download support?

Other possibility is to use aria2c. Here is a good how-to:
[http://10penguins.org/index.php/2008/01/22/using-rapidshare-premium-on-linux](http://10penguins.org/index.php/2008/01/22/using-rapidshare-premium-on-linux)

---

### Post by Re1lly on 2008-06-08
Rapget was working fine for me until i had this issue the other day: the program remains in the tray and it won't maximize. are there any config files i can delete from wine so it will think it's running the program for the first time?

---

### Post by LexLuthor08 on 2008-07-13
this rapidshare-dl would be a nice program... unfortunately I typed in the wrong password and I dont know how to change it. I uninstalled it, but after reinstallation it still remembered to wrong password... :(

---

### Post by coolworm on 2008-07-14
[http://ubuntudoitall.blogspot.com/](http://ubuntudoitall.blogspot.com/)

Here is how to fix D4X best download manager for linux:)

Thanks

---

