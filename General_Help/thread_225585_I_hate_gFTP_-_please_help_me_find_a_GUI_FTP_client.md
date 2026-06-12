---
title: "I hate gFTP - please help me find a GUI FTP client"
date: 2006-07-29
forum: General Help
---

### Post by videodrome on 2006-07-29
I loathe gFTP. I have been using it for about a week, and it has been a truly bad experience. I do not understand why everyone seems to praise this program. 

It just crashed again and that's the final straw (several crashes this week). It is painfully slow in transfers, and the overall speed of the application itself is turtle-like. Furthermore, it lacks the most basic things like "sort by file type." And for the life of me I can't figure out how to stop the "overwriting a file" dialog that pops up every single time I upload a file. I can't save a password for a site and the documentation is non-existant.

I need a good GUI FTP program ala WSFTP for windows. I do not use kde.

Is there no such thing? It seems incomprehensible that gftp is the best there is.

Thanks

---

### Post by aysiu on 2006-07-29
[FireFTP](http://fireftp.mozdev.org/) works for me.

---

### Post by jimmygoon on 2006-07-30
> **aysiu said:**
> [FireFTP]("http://fireftp.mozdev.org/") works for me.

fire craps out with large loads as well as long lists of files.... and big files

stick with a nightly of filezilla for linux or use wine and the latest stable of filezilla for windows... filezilla is simply **the** best...

---

### Post by Shay Stephens on 2006-07-30
I don't like how gftp won't stay connected.  FireFTP crashes on me all the time.  So I have been using nautilus for my ftp transfers.  I just made a "connect to server" connection and it opens in nautilus and away I go.  So far it is stable, stays connected, and works.

---

### Post by videodrome on 2006-07-30
Fireftp might be the one program that is actually worse than gftp. I don't have Nautilis with Xubuntu, so that's out. Sure seems odd that there are no reliable ftp alternatives, when we've got a glut of countless different text editors, email clients, media players, and even distributions themselves etc.

---

### Post by aysiu on 2006-07-30
KFTPGrabber is a good program, if you don't mind Qt.

I'm a bit surprised, though, that people are having issues with FireFTP.

---

### Post by cantormath on 2006-07-30
> **videodrome said:**
> I loathe gFTP. I have been using it for about a week, and it has been a truly bad experience. I do not understand why everyone seems to praise this program. 

It just crashed again and that's the final straw (several crashes this week). It is painfully slow in transfers, and the overall speed of the application itself is turtle-like. Furthermore, it lacks the most basic things like "sort by file type." And for the life of me I can't figure out how to stop the "overwriting a file" dialog that pops up every single time I upload a file. I can't save a password for a site and the documentation is non-existant.

I need a good GUI FTP program ala WSFTP for windows. I do not use kde.

Is there no such thing? It seems incomprehensible that gftp is the best there is.

Thanks

Places>connect to server
In POPUP pick ftp or ssh or whatever you want, fill in the rest of the stuff if you need to or want to.

thats what I use if I need gui.

---

### Post by jordilin on 2006-07-30
> **jimmygoon said:**
> fire craps out with large loads as well as long lists of files.... and big files

stick with a nightly of filezilla for linux or use wine and the latest stable of filezilla for windows... filezilla is simply **the** best...

Where can be obtained filezilla for linux?

---

### Post by yopnono on 2006-07-30
> **jordilin said:**
> Where can be obtained filezilla for linux?

Here: [http://filezilla-project.org/nightly.php](http://filezilla-project.org/nightly.php)
But it don't support non english characters

---

### Post by eqisow on 2006-07-30
Krusader, it should be in the repos.

You will likely have to download some extra libraries though, as it is a kde app.

---

### Post by nix4me on 2006-07-30
KFTPgrabber is very good.

Also I like SecureFTP (Java based and you have to download from their website)

Both of those are very good clients.

nix4me

---

### Post by cprise on 2006-07-30
Konqueror is excellent. Makes FTP just like accessing a drive.

---

### Post by videodrome on 2006-07-30
As I am running xubuntu, without gnome, for speed on an older laptop, I was trying to avoid 1) KDE apps 2) Nautilus 3) Java.

Isn't there a quick lightweight client out there?

---

### Post by Shay Stephens on 2006-07-30
> **videodrome said:**
> As I am running xubuntu, without gnome, for speed on an older laptop, I was trying to avoid 1) KDE apps 2) Nautilus 3) Java.

Isn't there a quick lightweight client out there?

How about gFTP....

I kid, I kid :D

---

### Post by DoktorSeven on 2006-07-30
commandline?

```

$ ftp ftp.site.com

```
;)

---

### Post by jimmygoon on 2006-07-30
I find nautilus to be adequate when compared with the alternatives, and as for fireftp, we're talking like 500mb files and/or lists of files like 2-3000 at a time...

But, I hope for filezilla to be in edgy+1 or edgy+2 ... whenever its near stable because honestly, of all ftp clients I've ever used (and its been ALOT... I have always found filezilla to be the most usable)

---

### Post by yopnono on 2006-07-30
Well I must say, that it's not easy to find a good ftp client, that also support non english characters like åöäñ etc,etc

---

### Post by HanZo on 2006-07-30
I was used to smartFTP on windows... and that prog is still beating any other on any platform by several lenght... would love to see an ftp client of that level on linux. I tried nearly all of the available ftp clients I could find around and yes, filezilla is the one that gave me less problems than the others... gftp was ok but was not good enough for my needs, though it never really failed me badly...

---

### Post by jimmygoon on 2006-07-30
> **HanZo said:**
> I was used to smartFTP on windows... and that prog is still beating any other on any platform by several lenght... would love to see an ftp client of that level on linux. I tried nearly all of the available ftp clients I could find around and yes, filezilla is the one that gave me less problems than the others... gftp was ok but was not good enough for my needs, though it never really failed me badly...

Yea, I did use smartftp although there were things about the UI that were more than my tastes required and I found it almost a it bloated... as for gftp it locks up at the drop of a dime and anytime you modify the quee it craps out and disconnect/crashes...

... besides totem, gftp is the only program that I've had consistency problems with...

---

### Post by nix4me on 2006-07-30
Filezilla is a wast of development time in my opinion.  Has no ability to do TLS or SSL.

KFTPgrabber and SecureFTP are the ONLY clients that do TLS/SSL correctly.  At least the only clients I have found.

nix4me

---

### Post by adamkane on 2006-07-30
If you don't like the Ubuntu solution, and don't want to mess around with Filezilla, then kbear is probably what you want.

---

### Post by yopnono on 2006-07-31
> **nix4me said:**
> Filezilla is a wast of development time in my opinion.  Has no ability to do TLS or SSL.

KFTPgrabber and SecureFTP are the ONLY clients that do TLS/SSL correctly.  At least the only clients I have found.

nix4me

FireFTP support TLS/SSL. And also I did notice non english charaters.
[http://fireftp.mozdev.org/help.html](http://fireftp.mozdev.org/help.html)
```
These days you can never be too careful. 
If the server you are connecting to supports it, 
you can make a secure connection to your FTP session much like the same way..
you have a secure connection when you do online banking.
Now, there are three choices as far as which method of security to use on your FTP connection. 
All three will protect you pretty freakin' great, 
but the best one to use is "Auth TLS" because it offers the best protection. 
If that's not available try using "Auth SSL" and after that "Implicit SSL".
Not all three will work with your FTP server, 
and that's partially why there are three different methods - 
because nobody quite could agree originally on how to go about doing things.
```

---

### Post by cantormath on 2006-07-31
> **jordilin said:**
> Where can be obtained filezilla for linux?

I dont have anything against filezilla, but you can do anything fileszilla can do with ubuntu.  Its also more resource friendly.  Filezilla is a FTP/SFTP server also, not a FTP Client.

---

### Post by _simon_ on 2006-07-31
I use kasablanca, it's a KDE FTP but works under Gnome just fine.

---

### Post by videodrome on 2006-07-31
So basically I am gathering that there is nothing.

A lot of people are suggesting various KDE apps or Nautilus, which really defeats the purpose of an Xubuntu install. I guess I'll have to use the command line.

I guess I'm just tired of these slow buggy and often bloated apps. I have a 2 ghz machine with a gig of ram, and gftp feels like it's running on a Pentium II with 128mb. 

Thanks anyhow.

---

### Post by aysiu on 2006-07-31
On the contrary, KDE apps run just fine in Xubuntu, and I've never noticed a significant slowdown at all. I don't know if FileZilla under Wine takes up "more resources," but I never noticed it doing so--transfers seemed fast to me. And, unlike some of the other post-ers here, I've never had a problem with FireFTP recently.

Maybe I'm just lucky.

---

### Post by Irony on 2006-07-31
Heck I never realised that Nautilus could be used as an ftp device just like in Windows and I've been using gftp all this time!

---

### Post by morningboat on 2006-08-01
[CrossFTP Client]("http://www.crossftp.com/index.htm") is a good GUI FTP client in Java.

---

### Post by Thanol on 2006-08-01
> **Irony said:**
> Heck I never realised that Nautilus could be used as an ftp device just like in Windows and I've been using gftp all this time!

Same here, but I can't get it to CHMOD, so I'm back to gftp :mad:

---

### Post by videodrome on 2006-09-01
Just letting everyone know that I still hate gftp, and now it's what, well over a year old and seemingly a dead project, and yet it is the only one there is. Enough with the 37 different text editors; we need a good graphical ftp client.

---

### Post by The Keeper on 2006-09-01
Agreed, luckily FileZilla 3 is in active development. With any luck we'll be seeing final release before end of the year, or at least usable beta-version.

---

### Post by yopnono on 2006-09-01
> **videodrome said:**
> Just letting everyone know that I still hate gftp, and now it's what, well over a year old and seemingly a dead project, and yet it is the only one there is. Enough with the 37 different text editors; we need a good graphical ftp client.

True but... FireFTP can be used as standalone aswell. And also it works great.

---

### Post by petersjm on 2006-09-01
I've never had a problem with FireFTP, either. And I'm pretty sure there's no cause for concern in using KDE apps in Xubuntu...

---

### Post by Irony on 2006-09-01
You might want to check out Foff;

[http://foff.sourceforge.net/](http://foff.sourceforge.net/)

It got a favourable review in Linux Format and seems to be 'live'.

---

### Post by dannyboy79 on 2006-09-06
I love flashfxp for windows and I was jsut asking my buddy who turned me onto linux and ubuntu what he uses and he said he uses the linux version of flashfxp. So now I just need to find it!

---

### Post by dannyboy79 on 2006-09-06
MY BAD, i just looked into it briefly and it turns out that my friend didn't tell me he weas running it with wine! Sorry for wasting peoples time so that's why I posted this!

---

### Post by Shay Stephens on 2006-09-07
> **Irony said:**
> You might want to check out Foff;

[http://foff.sourceforge.net/](http://foff.sourceforge.net/)

It got a favourable review in Linux Format and seems to be 'live'.

foff is interesting as it is written in python.  I have only tried it once, and it worked, and I hope to maybe learn a little more about python programming with it.

Now if I can just learn how to make a launcher for it ;-) it only runs if I call it from the terminal while in the foff directory.

---

### Post by dsmithnc on 2006-09-07
> **cantormath said:**
> Places>connect to server
In POPUP pick ftp or ssh or whatever you want, fill in the rest of the stuff if you need to or want to.

thats what I use if I need gui.

That's what I love about user forums.  I learn something new everyday.  Thanks cantormath for an excellent tip.

Dick

---

### Post by RTrev on 2006-11-10
The problem I have with gFTP is that it insists on transferring my .html files in ASCII mode rather than binary.  I've set all the options to binary, but it simply won't do it.  If I generate an MD5SUM file, transfer the stuff up to my server, and bring it back down, the MD5SUM fails on every .html file.  It uses binary on the .css, .png, etc., but simply won't use it for .html files.

It works fine for people I know, and honors their choice of binary mode, but simply won't for me (Edgy, Gnome).

Nautilus works okay, but is very slow on my system.  It takes roughly 10 times as long as gFTP or FireFTP.

FireFTP has worked well for me, and it's what I use, but I'd prefer gFTP if not for its insistence on ASCII mode.

Any ideas?

---

### Post by Beernut on 2006-11-10
> **Thanol said:**
> Same here, but I can't get it to CHMOD, so I'm back to gftp :mad:

If you have SSH access just setup Nautilus with SSH instead of FTP and you can CHMOD.

---

### Post by RTrev on 2006-11-11
Just a quick followup to my post about gFTP refusing to use binary mode for .html files.  I found the problem.  There is a hidden directory off /home/user directory called .gftp, and in there was a gftprc file with the settings telling gFTP to use ascii mode for .htm and .html files.  It's working fine now.  Maybe this will help someone.

---

### Post by videodrome on 2006-11-12
I'll look into that config file. Thanks. 

For the record, let it be noted that the default Ubuntu ftp client, gftp, hasn't been updated in what will soon be 2 years.

---

### Post by maniacmusician on 2006-11-12
just use filezilla for linux...sorry if this has been mentioned before. It may not have all the features of windows filezilla yet, but it's sure of a hell lot better than gFTP.

---

### Post by Elaztic on 2006-11-12
I have also been searching for a good GUI FTP client and stubled across IglooFTP ([http://www.iglooftp.com/linux/index.html)](http://www.iglooftp.com/linux/index.html)), which is a commercial product (free try - haven't seen any limits).
It's way ahead of gFTP and stable, but still not marvellous.

Thanks for previous posts from everyone! Good info on FileZilla, FireFTP etc...will check these FTP clients out.

---

### Post by videodrome on 2006-11-16
FireFTP just plain sucks too. Here's what it does. It has done this for the past few versions of both Firefox and Fireftp that I have used, under two differnt machines, on both edgy and breezy:

It works fine for a little while, say uploading 25 jpg's to my ftp site. Then sure enough, even if I have closed fireftp, the webbrowser stops functioning. It doesn't crash, it just stops being able to connect to websites. It just sits there and times out on every site that you try to connect to. Closing and restarting Firefox solves the problem. I am positive that Fireftp is the culprit; the only time this ever happens is after using Fireftp.

---

### Post by yopnono on 2006-11-17
> **videodrome said:**
> FireFTP just plain sucks too. Here's what it does. It has done this for the past few versions of both Firefox and Fireftp that I have used, under two differnt machines, on both edgy and breezy:

It works fine for a little while, say uploading 25 jpg's to my ftp site. Then sure enough, even if I have closed fireftp, the webbrowser stops functioning. It doesn't crash, it just stops being able to connect to websites. It just sits there and times out on every site that you try to connect to. Closing and restarting Firefox solves the problem. I am positive that Fireftp is the culprit; the only time this ever happens is after using Fireftp.


Contact the dev of FireFTP. I had a small problem with it, and he listened fixed it.

---

### Post by adamkane on 2006-11-17
Filezilla:
[http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/](http://3v1n0.tuxfamily.org/dists/dapper/3v1n0/)

---

### Post by videodrome on 2006-11-17
LOL here's Filezilla:

I installed it, ran it, entered my FTP site info, and pressed "connect."

It immediately crashed back to terminal.

loomis@2000:~$ filezilla
Segmentation fault (core dumped)
loomis@2000:~$ 

Faaaaantastic!

---

### Post by adamkane on 2006-11-17
I should have mentioned that the link applies to Dapper only. Don't know if that helps.

---

### Post by nix4me on 2007-01-06
Well, as you have seen, there is not shining star ftp program for linux.  It would be nice if someone could make a gui for lftp command line ftp.  It works perfectly on the command line.

nix4me

---

### Post by Quillz on 2007-01-06
I just use Nautilus's built-in FTP client. It works just fine for me, and it makes FTP browsing very easy.

---

### Post by nix4me on 2007-01-06
Well nautilus does not use TLS/SSL.  Many servers use this now.

nix4me

---

### Post by CoolHand on 2007-01-07
Here are a few I found with a quick search.  gFTP has always been fine for me but I have seen shortcomings in it so I may try a few of these myself.

[DPS-FTP]("http://www.icewalkers.com/Linux/Software/54160/DPS-FTP.html")
[Axy FTP (wxftp reworked)]("http://www.wxftp.seul.org/index.shtml")
[FtpCube]("http://ftpcube.sourceforge.net/")
NCFTP - Don't know the web site.  Not really a full gui.  It's an ncurses ui.
[FileRunner tcl/tk based]("http://www.cd.chalmers.se/~hch/filerunner.html")

Good Luck.

---

### Post by glabouni on 2007-01-12
I'm also hunting for a good GUI ftp client. 

It *has to* be working (no fireFTP), stable (no fireFTP), include all required features (queue management, chmod, custom command, multi thread, ...) (no fireFTP) support secure connections and transfers (no fireFTP), be a full ftp client not an integrated feature of another stuff(no fireFTP, konqueror, nautilus) , and being usable under any environnement (not being gnome or kde specific for instance).
better if it is open source, free and still alive but this is not required. 

These requirements are pretty much ruling out all the ftp client that have been cited here, and all those I've found and tried yet. 

[http://en.wikipedia.org/wiki/Comparison_of_FTP_clients](http://en.wikipedia.org/wiki/Comparison_of_FTP_clients)

I still have to try my luck with kasablanca ([http://kasablanca.berlios.de/](http://kasablanca.berlios.de/)) and ftpcube ([http://ftpcube.sf.net/](http://ftpcube.sf.net/)) which seems promising.

Another solution might come from some midnight commander 

btw the homepage for ncftp is [http://www.ncftp.com/ncftp/](http://www.ncftp.com/ncftp/)

here are a few words for those who may complain about open source not being in my requirements: if a closed source piece of software does the job its open source equivalent does not, I'll go for closed source anytime. As an example don't even bother talking to me about firefox, if it wasn't part of ubuntu-desktop package, this would have been long gone. actually the 2 first things I did after completing ubuntu installation were downloading opera and trying to remove firefox. And when I figured that it is part of ubuntu-desktop package I've even considered switching from ubuntu to debian just to get rid of it, cause I know better than breaking ubuntu package. 
if you have any comment about this note, please don't direct them to me only via private messaging and don't litter the thread. thank you.

---

### Post by Shay Stephens on 2007-01-12
I just recently installed filezilla 3.0 beta1 that is much faster that gftp or nautilus and more stable than fireftp.  No long term experience with it yet though.  There is a newer beta, but I have not tried it yet.

---

### Post by yopnono on 2007-01-23
> **glabouni said:**
> I'm also hunting for a good GUI ftp client. 

It *has to* be working (no fireFTP), stable (no fireFTP), include all required features (queue management, chmod, custom command, multi thread, ...) (no fireFTP) support secure connections and transfers (no fireFTP), be a full ftp client not an integrated feature of another stuff(no fireFTP, konqueror, nautilus) , and being usable under any environnement (not being gnome or kde specific for instance).
better if it is open source, free and still alive but this is not required. 

These requirements are pretty much ruling out all the ftp client that have been cited here, and all those I've found and tried yet. 

[http://en.wikipedia.org/wiki/Comparison_of_FTP_clients](http://en.wikipedia.org/wiki/Comparison_of_FTP_clients)

I still have to try my luck with kasablanca ([http://kasablanca.berlios.de/](http://kasablanca.berlios.de/)) and ftpcube ([http://ftpcube.sf.net/](http://ftpcube.sf.net/)) which seems promising.

Another solution might come from some midnight commander 

btw the homepage for ncftp is [http://www.ncftp.com/ncftp/](http://www.ncftp.com/ncftp/)

here are a few words for those who may complain about open source not being in my requirements: if a closed source piece of software does the job its open source equivalent does not, I'll go for closed source anytime. As an example don't even bother talking to me about firefox, if it wasn't part of ubuntu-desktop package, this would have been long gone. actually the 2 first things I did after completing ubuntu installation were downloading opera and trying to remove firefox. And when I figured that it is part of ubuntu-desktop package I've even considered switching from ubuntu to debian just to get rid of it, cause I know better than breaking ubuntu package. 
if you have any comment about this note, please don't direct them to me only via private messaging and don't litter the thread. thank you.


Mail cuteftp
"There are no plans for a linux version at this time.  I have added your request to the list of votes in favor of this project, so that it will get consideration when this comes up again in the future.

-Ted Marchut
 Product Manager
 GlobalSCAPE"


mailto: [email]gsform190@globalscape.com[/email]
Subject: RE: Feature Request / CuteFTP Home

---

### Post by nix4me on 2007-01-23
kasablanca is very nice.  Seems to work much better than the others mentioned in this thread.

nix4me

---

### Post by bouddidje on 2007-01-24
After tried filezilla on windoz (great !...not win but filezilla)
and gftp

I prefer kasablanca too.
I think You've tried to configure your firewall and/or desable it ?

---

### Post by icedcheese on 2007-02-01
I was in the same boat until reading this thread.  I had tried to give gftp the benefit of the doubt, but have finally given up.  As a php programmer, I need to upload to servers (which happen to be all around the world so some connections are slow).  I liked the ease of use of gftp - in particular the fact that it gave you the option to select skip or overwrite at the start of a bulk upload.  In fact, if it wasn't for the crashes I would say it would be the best out there - including out of the windows ftp's.

However, today (from advise from this thread) I installed filezilla.  I have been running the windows version under wine, however the linux version is much better.  It was available in Synapic, which made it easy to install and its working GREAT!!!!  I couldn't recommend a better ftp client for linux - this should be the default ftp client on Ubuntu!!!

Thanks for your help Ubuntu community, you have saved me hours of waiting and frustrating time!!

---

