---
title: "OpenOffice 2 final was released... how do I upgrade?"
date: 2005-10-20
forum: General Help
---

### Post by ymmotrojam on 2005-10-20
The final release of open office 2 was released today... I'm a newbie and all, and just now figured out how to use the Synaptic Package Manager, but I don't see the latest release in there. How would I go about upgrading my copy of Open Office? Thanks! :)

---

### Post by KingBahamut on 2005-10-20
Wait for the Repos to update their package lists. Im assuming thats something that will be in the works and done relatively quickly. 

If not, you can grab OOo's installer and install a non-Repository copy yourself.

---

### Post by guoweiok on 2005-10-20
Let me put it in this way:
If the package is not insider Synaptic, that means the Ubuntu group havent completed the packaging process yet. So just wait for a while!
If you really want to use it now, try to download the source code from the OpenOffice.org and compile yourself. It is not that difficult, there is always a "README" or "INSTALL" text file inside the package folder.

---

### Post by jasplund on 2005-10-20
You can get DEBs from [http://ftp.linux.cz/pub/localization/OpenOffice.org/2.0/](http://ftp.linux.cz/pub/localization/OpenOffice.org/2.0/)

Johan

---

### Post by The_Saint on 2005-10-20
[QUOTE=jasplund]You can get DEBs from [http://ftp.linux.cz/pub/localization/OpenOffice.org/2.0/](http://ftp.linux.cz/pub/localization/OpenOffice.org/2.0/)

Johan[/QUOTE]  I think from there one can find only Czech and Slovakian language versions.

I suggest the following - download it from [www.openoffice.org](www.openoffice.org)

alien the rpm's to deb, install the deb's (it installs it automatically to /opt/openoffice2.0 i think) and voila - start using it :)

I used this scheme with all the RC's of ver 2. Worked every time.

---

### Post by PuleX on 2005-10-20
Well, I have the patience to wait for the Ubuntu guys to package and test it for a bit. Otherwise, I might as well install Etch on my system... :)

---

### Post by jasplund on 2005-10-20
[QUOTE=The_Saint]I think from there one can find only Czech and Slovakian language versions.

I suggest the following - download it from [www.openoffice.org](www.openoffice.org)

alien the rpm's to deb, install the deb's (it installs it automatically to /opt/openoffice2.0 i think) and voila - start using it :)

I used this scheme with all the RC's of ver 2. Worked every time.[/QUOTE]

You can find language packs at [http://ftp.linux.cz/pub/localization/OpenOffice.org/2.0/OOo_2.0_native_LinuxIntel_langpacks_deb/](http://ftp.linux.cz/pub/localization/OpenOffice.org/2.0/OOo_2.0_native_LinuxIntel_langpacks_deb/)
for a bunch of other languages

---

### Post by Muffe on 2005-10-20
It is publihed official OpenOffice2 english debs on openoffice.org. Don't know how well they work on Ubuntu, so I'll wait a few days until some other have tried first.

---

### Post by SickTwist on 2005-10-20
The official Ubuntu repositories will not have OpenOffice 2.0 for Breezy. Breezy development is over since it is now a stable release. Daper Drake will be when OO.o 2.0 is included.

The backports repositories may eventually have OO.o 2.0 for Breezy although this is not officially supported.

It might be better just to stick with the OO.o that is shipped with Breezy. This has been tested and will receive security updates for 18 months. There are not going to be drastic changes in the 2.0 release of OO.o.

---

### Post by ymmotrojam on 2005-10-20
[QUOTE=SickTwist]The official Ubuntu repositories will not have OpenOffice 2.0 for Breezy. Breezy development is over since it is now a stable release. Daper Drake will be when OO.o 2.0 is included.

The backports repositories may eventually have OO.o 2.0 for Breezy although this is not officially supported.

It might be better just to stick with the OO.o that is shipped with Breezy. This has been tested and will receive security updates for 18 months. There are not going to be drastic changes in the 2.0 release of OO.o.[/QUOTE]
hmm... you think the release of ubuntu could have been planned any worse as far as open office is concerned? ;). I mean I know they align it after the gnome releases and all, but...

---

### Post by unexpected on 2005-10-20
Well, Open Office has been in beta 2 for forever. I'm not too sure what's the point in upgrading.

Does anyone have a list of features included in Ubuntu OO.org 2 Beta and the one released today?

---

### Post by matthew on 2005-10-20
[quote=ymmotrojam]hmm... you think the release of ubuntu could have been planned any worse as far as open office is concerned? ;). I mean I know they align it after the gnome releases and all, but...[/quote]
The only other option was to wait until Ooo was released. However, with no prior announcement as to when that might happen waiting would have been a bad idea. Especially in the light of the set-in-stone six month release schedule. If Ubuntu devs had waited for this piece of software then it would have begged the question "Why not this other piece of software?" and so on. Pretty soon you have Debian...wait until someone says it's all perfect, and then we will have a release. Debian already exists and does what it does quite well--slow, steady and stable releases. I see no need to duplicate that. Ubuntu seeks to stabilize the bleeding edge of software and releases the best thing in existence every 6 months. If it's ready at code freeze, it's in there. If it isn't, it will have to wait for the next release. That's how it goes.

---

### Post by taurus on 2005-10-20
[QUOTE=ymmotrojam]hmm... you think the release of ubuntu could have been planned any worse as far as open office is concerned? ;). I mean I know they align it after the gnome releases and all, but...[/QUOTE]

If you want OO 2.0 so bad, download it and install it yourself!!!  I don't even know why you cry about why ubuntu would have waited to OO 2.0 to come out...

[B]
Lets try to keep the flames down....KB[/B]

---

### Post by matthew on 2005-10-20
[quote=taurus]If you want OO 2.0 so bad, download it and install it yourself!!! I don't even know why you cry about why ubuntu would have waited to OO 2.0 to come out...

[B]
Lets try to keep the flames down....KB[/B][/quote]

Good point, KB.

For what it's worth, I just downloaded the newest Ooo and installed it on my test box to see what the changes were. I really didn't see any from the version in the repos other than the version number being solidified. There may be some differences/bugfixes, but there are no obvious new features. I really don't think it would be worth the work to do a fresh install for anyone other then the "I have to have the newest, shiniest, etc." crowd.

---

### Post by stoeptegel on 2005-10-20
You don't want to rush your mother when she's cooking your favorite meal do you? Just sit back and enjoy the ride...

---

### Post by angrykeyboarder on 2005-10-20
[quote=guoweiok]Let me put it in this way:
If the package is not insider Synaptic, that means the Ubuntu group havent completed the packaging process yet. So just wait for a while!
If you really want to use it now, try to download the source code from the OpenOffice.org and compile yourself. It is not that difficult, there is always a "README" or "INSTALL" text file inside the package folder.[/quote] 
And 9 X out of 10 I get errors after I run "./configure".

There is always some option that I'm supposed to be including but I've never been able to figure that out (regardless of what program I'm trying to complie).

---

### Post by angrykeyboarder on 2005-10-20
[quote=KingBahamut]Wait for the Repos to update their package lists. Im assuming thats something that will be in the works and done relatively quickly. 

If not, you can grab OOo's installer and install a non-Repository copy yourself.[/quote] 
I'm not so sure we'll see an update. Ubuntu generally only updates the packages in thier distros when it's a major bugfix or security update. 

This is technically neither (unless it it happens to fix a major bug that was in the version they gave us).

We just might have to wait for it to appear in backports....

---

### Post by oblib on 2005-10-20
I thought Breezy came with OO 2. Wasn't that one of the major features? My Writer says OpenOffice.org 2 1.9.129. It has Base, which is one of the new OO features. My 2 cents anyway.

---

### Post by angrykeyboarder on 2005-10-20
[quote=PuleX]Well, I have the patience to wait for the Ubuntu guys to package and test it for a bit. Otherwise, I might as well install Etch on my system... :)[/quote]

You may have a long wait.

See my previous post in this thread.

---

### Post by angrykeyboarder on 2005-10-20
[quote=SickTwist]The official Ubuntu repositories will not have OpenOffice 2.0 for Breezy. Breezy development is over since it is now a stable release. Daper Drake will be when OO.o 2.0 is included.

The backports repositories may eventually have OO.o 2.0 for Breezy although this is not officially supported.

It might be better just to stick with the OO.o that is shipped with Breezy. This has been tested and will receive security updates for 18 months. There are not going to be drastic changes in the 2.0 release of OO.o.[/quote]

Since when does beta software recieve security updates?

---

### Post by angrykeyboarder on 2005-10-20
[quote=SickTwist]The official Ubuntu repositories will not have OpenOffice 2.0 for Breezy. Breezy development is over since it is now a stable release. Daper Drake will be when OO.o 2.0 is included.[/quote] Surprise, surprise....
[quote=SickTwist]The backports repositories may eventually have OO.o 2.0 for Breezy although this is not officially supported.[/quote] 
Backports ***are*** officially supported (at least to the extent that the universe repository is) "Extras" are not supported at all.

There is not chance of 2.0 being in backports till it's in Breezy or Debian unstable/testing (that is unless the backports folks have changed thier policy).

[quote=SickTwist] It might be better just to stick with the OO.o that is shipped with Breezy. This has been tested and will receive security updates for 18 months. There are not going to be drastic changes in the 2.0 release of OO.o.[/quote] 
If I were running Windows right now I'd just download the freaking program from [www.openoffice.org]("http://www.openoffice.org") and install and be done with it.  I'd not have to wait 6 months for Microsoft to "Update Windows".

The program I'd be downlading would alrezdy be compiled and ready to go with a "windows compatible" installer program. I'd not need to con vert it to a Debian, RedHat, Gentoo or Slackware-compatible installer in order for me to keep track of it once installed.

It's absolutely absurd to expect users to wait nearly ***six months*** after a product is released for an update.

Unless they've changed I'd expect to see OOo 2.0 final available for any number of Linux distros in the near future (in supported repositories). It's too bad Ubuntu won't be one of those.

I'm trying to find logic here, but I fail to.

Untill crap like this changes, Linux will remain soley in the "Geek Domain" (as far as the desktop is concerned anyway).

At the very least Ubuntu needs to look at how most of the major Linux distros handle updates like this one. 

But in the meantime, Ubuntu has gone with what Debian does (more or less) even though they claim not to (othewise) be Debian.

Don't get me wrong, I'm not dumping Linux (although my loyalty to Ubuntu is pretty fickle and this doesn't help), but crap like this is just inexcusable.

Yes, I know I paid for Windows and it's commercial software whereas Ubuntu Linux is not, however OpenOffice.org is open source and runs on Windows, Mac and many flavors of Linux/Unix.

So how about it Ubuntu? Give us OOo 2.0 final soon OK?

---

### Post by angrykeyboarder on 2005-10-20
[quote=The_Saint]I think from there one can find only Czech and Slovakian language versions.

I suggest the following - download it from [www.openoffice.org]("http://www.openoffice.org")

alien the rpm's to deb, install the deb's (it installs it automatically to /opt/openoffice2.0 i think) and voila - start using it :)

I used this scheme with all the RC's of ver 2. Worked every time.[/quote]

There are no RPMs for 2.0 final (at least not yet anyway).  Only the generic Linux installer.

---

### Post by angrykeyboarder on 2005-10-20
[quote=oblib]I thought Breezy came with OO 2. Wasn't that one of the major features? My Writer says OpenOffice.org 2 1.9.129. It has Base, which is one of the new OO features. My 2 cents anyway.[/quote]

Take a closer look at that version number.  It's v 1.9.129 which was the last of the numbering schemes that OOo was using for the beta/RC versions.

Unfortunatly 2.0 was not out till today.

[http://www.openoffice.org/press/2.0/press_release.html](http://www.openoffice.org/press/2.0/press_release.html)

---

### Post by professor_chaos on 2005-10-20
can I ask you AngryKeyboarder? What is the huge motive for updating right now from v1.9.129 to the big 2?

are there features in 2 that you cannot absolutely live without? 

I use ooo to write some compatible documents on occasion, but mostly use gedit and the like. I really love that synaptic and the repositories exist. My machine updates itself and I thank all of the developers who take the time to build packages and test them. Thank you, Thank you, Thank you.

---

### Post by angrykeyboarder on 2005-10-20
[quote=professor_chaos]can I ask you AngryKeyboarder? What is the huge motive for updating right now from v1.9.129 to the big 2? [/quote]

I've been following the beta for months and had been hoping it would be final before Breezy was released but it missed the mark by a few weeks.  So, I'd like to have it now.
[quote=professor_chaos]are there features in 2 that you cannot absolutely live without?[/quote]

Not that I'm currently aware of, no.

[quote=professor_chaos]I use ooo to write some compatible documents on occasion, but mostly use gedit and the like. I really love that synaptic and the repositories exist. My machine updates itself and I thank all of the developers who take the time to build packages and test them. Thank you, Thank you, Thank you.[/quote]

I'm happy you're so happy.

---

### Post by angrykeyboarder on 2005-10-20
[quote=taurus]If you want OO 2.0 so bad, download it and install it yourself!!! I don't even know why you cry about why ubuntu would have waited to OO 2.0 to come out...

[B]
Lets try to keep the flames down....KB[/B][/quote]

Because there are oher packages that go along with it that I don't think OpenOffice.org is providing.

e.g.:

openoffice.org2-evolution - Evolution Addressbook support for OpenOffice.org
openoffice.org2-gnome - GNOME Integration for OpenOffice.org (Widgets, Dialogs, VFS, GConf)
openoffice.org2-java-common - OpenOffice.org office suite Java support arch. independent files
openoffice.org2-kde - KDE Integration for OpenOffice.org (Widgets, Dialogs, Addressbook)

As I stated previously, Ubuntu included a *beta* version of a *major* software program in Breezy.

I think that's justificatoin for them to break their "rule" about not offering us an upgade to the final version upon release.

---

### Post by angrykeyboarder on 2005-10-20
[quote=stoeptegel]You don't want to rush your mother when she's cooking your favorite meal do you? Just sit back and enjoy the ride...[/quote]

It doesn't take my mom ***6 months*** to cook anything. ;-)

---

### Post by Qrk on 2005-10-20
Don't worry... I will personally give you your money back. :smile: 

I don't think you'll have to wait, though. The ubuntu team does gives new versions of software inbetween releases; they probably wouldn't do big updates, like 1.1 to 2.0, but I'm sure the'll have some way to get the beta to stable upgraded. Whether its in backports or main... thats a good question. But seeing how good the devolopment team has been, its only a matter time.

---

### Post by towsonu2003 on 2005-10-21
hmm,
I see from posts that while an extremely big component of ubuntu is updated from beta/rc to stable, people are happy with the current thing they have now. Is this correct? That's weird, especially for the geek linux community.

---

### Post by jasplund on 2005-10-21
I don't get why people are expecting a bunch of new features going from 1..9.129 to 2.0. Wasn't OOo in feature freeze when 1.9.129 was released. It's only bugfixes

---

### Post by angrykeyboarder on 2005-10-21
[quote=towsonu2003]hmm,
I see from posts that while an extremely big component of ubuntu is updated from beta/rc to stable, people are happy with the current thing they have now. Is this correct? That's weird, especially for the geek linux community.[/quote]

My sentiments exactly.

---

### Post by angrykeyboarder on 2005-10-21
[quote=jasplund]I don't get why people are expecting a bunch of new features going from 1..9.129 to 2.0. Wasn't OOo in feature freeze when 1.9.129 was released. It's only bugfixes[/quote]

I've been whining about this more than most in this thread and I've never said anything with regard to "expecting a bunch of new features going from 1..9.129 to 2.0"

I just prefer not to use "beta" software when the final product is out.

(and especially not 2, 3 or 5 months afterwards - this assumnes 2.0 never shows up in updates or backports).

---

### Post by matthew on 2005-10-21
[quote=angrykeyboarder]There are no RPMs for 2.0 final (at least not yet anyway). Only the generic Linux installer.[/quote] 1. The rpms are contained in the tarball that you download from the openoffice.org website. I did this earlier today and installed them on a test computer using alien just like the other poster suggested and it worked GREAT. You extract the tarball to any directory you want (I would create /home/openoffice2) and you will find a directory nested inside labeled RPMS.

2. I didn't see any real change from 1.9.129 to 2.0, certainly nothing worth the hassle of downloading and installing (for someone who considers it a hassle, I thought it was pretty easy, but I still won't do it on my other three machines as there is no advantage over 1.9.129).

3. Your anger is obvious. I'm sorry you aren't finding what you want here. I think your anger is misdirected and unfortunate. I really doubt anyone here is going to be able to do or say anything that will please you. I hope the ranting helped you feel better. 

I would like to share an old story.

**Story**
A man moved to a new city. Upon arrival he entered the corner market and announced his presence to the shopkeeper. He then inquired what the people were like in his new town. The shopkeeper responded, "What were they like in your last town?" The man replied that they were wonderful people, warm and kind. "Well," the shopkeeper said, "I expect you will find them the same here."

Not long after that another man moved into town. He also entered the corner market and announced his presence to the shopkeeper. He also inquired what the people were like in his new town. The shopkeeper responded, "What were they like in your last town?" The man replied that they were horrible people, viscious, mean and hard to get along with. The shopkeeper replied, "Well, I expect you will find them the same here."

---

### Post by ymmotrojam on 2005-10-21
Although I'm fine with OOo as it came with breezy.... I still would like more effort put into getting out the latest thing. Many mention that there aren't big feature differences. Of course there aren't, but it's just the nice feeling that you're using a product that you know relatively well won't break, because it's got that official seal of approval on it. It's not really about having more features or not. Unless there is an update to Ubuntu, OOo will be stuck in that pre-stamped/pre-approval stage until the next release...

Maybe this hints at some other changes that should take place...
Now I realize there are probably more things than just OOo that are included in Ubuntu that are beta/rc versions, but wouldn't it be nice if the Ubuntu OS installer asked you whether you wanted to install apps that were known betas? Now this is a newbie talking, but it seems logical to me.

---

### Post by Jingo on 2005-10-21
[QUOTE=towsonu2003]hmm,
I see from posts that while an extremely big component of ubuntu is updated from beta/rc to stable, people are happy with the current thing they have now. Is this correct? That's weird, especially for the geek linux community.[/QUOTE]

Agree..
I hope Ubuntu users are not set back for having the latest and greatest of the big programs out there.

Sure OOo 2 final is just a bug-fix release. I don't know what these bugs were, but anyway OOo is the most importent app. for office use. I would like bug-fix upgrades!!!

---

### Post by flibble on 2005-10-21
rotflmao

So... you don't want to download an official .rpm from openoffice.org and use alien to install it, which would take two commands and 30 seconds to install... you want to download an official ubuntu .deb and install it with a click. And on this basis you're ranting that, "crap like this is just inexcusable"? :D 

Ok, so you choose not to do the 30 second, two command, installation.

Then you say, "It's absolutely absurd to expect users to wait nearly six months after a product is released for an update." (!)

You don't have to... several people in this thread have pointed that out. They're already happily using OO.o version 2.0. :rolleyes:

This "absolute absurdity" of a 6 month release cycle is a decision, taken to ensure a level of stability that can't be provided, for free, with continuous rolling updates. Maybe you need to exercise your choice to use another distro that does do this. If you don't want to, maybe reflect on what it is about Ubuntu that you like and whether this has anything to do with the 6 month release cycle.

I can see why you call yourself "angrykeyboarder". It seems like you'd rather spend five minutes typing a rant than solve your problem in 30 seconds. :p

---

### Post by veritas366 on 2005-10-21
I thought the new database program came in OO2. Is that not correct?

---

### Post by bertilow on 2005-10-21
[QUOTE=flibble]rotflmao
So... you don't want to download an official .rpm from openoffice.org and use alien to install it, which would take two commands and 30 seconds to install...[/QUOTE]

I have no idea what the "alien" command is (sounds a bit scary...), what it does or how or when I'm supposed to use it.

The "man" page says "alien" is "rather experimental software. It’s been under development for many years now, but there are still many bugs and limitations". That does not sound very inviting for someone who's never even heard of the program before.

Could someone explain how to use it (in particular with the OpenOffice 2 RPMs), and also perhaps detail what the risks of using "alien" could be? I don't know what's riskier: use a possibly very buggy beta version of OpenOffice 2 (it does crash sometimes), or perhaps fry my entire system with the mysterious "alien" command (I could get abducted, who knows...).

---

### Post by Muffe on 2005-10-21
Why not just download the official debs (the debs released by the openoffice.org team)?

---

### Post by bertilow on 2005-10-21
[QUOTE=Muffe]Why not just download the official debs (the debs released by the openoffice.org team)?[/QUOTE]

Where are they? When I go to "openoffice.org" and try to download, I only get a choice of OS, "Linux", and then I get RPMs. I can't find any mention of debs.

---

### Post by poofyhairguy on 2005-10-21
[QUOTE=bertilow]
Could someone explain how to use it (in particular with the OpenOffice 2 RPMs), and also perhaps detail what the risks of using "alien" could be?[/QUOTE]

The risk is it not working. Here is example of how to use it:

[http://www.ubuntuforums.org/showthread.php?t=38526](http://www.ubuntuforums.org/showthread.php?t=38526)

I almost promise that it won't be a lot more stable than the version on Breezy- it was not long between the two.

---

### Post by poofyhairguy on 2005-10-21
[QUOTE=angrykeyboarder]
So how about it Ubuntu? Give us OOo 2.0 final soon OK?[/QUOTE]


Jdong will probably backport it when Dapper has it. Then it will sit in the official backports repo, ready to be installed.

Thats why backports is so cool. Sorry it takes too long for yourself, I can wait.

(and yes I know that you don't like the fact that it probably won't go in the main, but that is Ubuntu policy. )

---

### Post by jeremy on 2005-10-21
I take the same view as poofyhairguy, but I do think that it is a shame that breezy was packaged with the release candidate rather than the last stable version.

---

### Post by stoeptegel on 2005-10-21
What just a versionnumber can do... :-s
The reason is all about policy and release time why it's not included, and what's wrong with a little respect for that. I think a more important question is: do we miss something or is the ubuntu version we now have instable? For me, both awnsers are no, so i don't care waiting for that stupid number.

---

### Post by lemontea on 2005-10-21
Let me add the point that you have to also consider people in remote region that has old computer, no network access, and can **only** obtain ubuntu via shipit program. Poor they, they've to wait for 6 months when this can actually be prevented.

Just my quick thought.

---

### Post by bertilow on 2005-10-21
[QUOTE=stoeptegel]do we miss something or is the ubuntu version we now have instable?[/QUOTE]

It's crashing a lot. The final version has a few bug fixes. Maybe those bug fixes will make the program crash less.

---

### Post by Joeb on 2005-10-21
[QUOTE=angrykeyboarder]Surprise, surprise....

 
If I were running Windows right now I'd just download the freaking program from [www.openoffice.org]("http://www.openoffice.org") and install and be done with it.  I'd not have to wait 6 months for Microsoft to "Update Windows".

The program I'd be downlading would alrezdy be compiled and ready to go with a "windows compatible" installer program. I'd not need to con vert it to a Debian, RedHat, Gentoo or Slackware-compatible installer in order for me to keep track of it once installed.

So how about it Ubuntu? Give us OOo 2.0 final soon OK?[/QUOTE]


So, why don't you just go to [www.openoffice.org](www.openoffice.org) and download the pre-compiled linux version?  No one is making you wait six months to get it.

Joeb

---

### Post by stoeptegel on 2005-10-21
[QUOTE=lemontea]Let me add the point that you have to also consider people in remote region that has old computer, no network access, and can **only** obtain ubuntu via shipit program. Poor they, they've to wait for 6 months when this can actually be prevented.

Just my quick thought.[/QUOTE]


That's true, i agree, though you can never do things right for all people at the same time, that's theoretical and practical impossible.

---

### Post by matthew on 2005-10-21
[quote=bertilow]Could someone explain how to use it (in particular with the OpenOffice 2 RPMs), and also perhaps detail what the risks of using "alien" could be? I don't know what's riskier: use a possibly very buggy beta version of OpenOffice 2 (it does crash sometimes), or perhaps fry my entire system with the mysterious "alien" command (I could get abducted, who knows...).[/quote] 
alien is a pretty easy command to use and has worked perfectly for me every time I have used it (about 20 different installs of stuff). I know it works fine for OpenOffice 2 as I have used it for that. Here is what you need to do if you want to install the final Ooo 2.0.

First, make sure alien is installed on your computer. 

Make sure all the extra repositories are enabled on your computer
[http://www.psychocats.net/sources.html]("http://www.psychocats.net/sources.html")

Open a terminal window at Applications->Accessories->Terminal and in the window type:
```
sudo apt-get update

sudo apt-get install alien
``` 
Then download the linux version for Open Office 2.0 from openoffice.org. I like to download things to a directory made specifically for that piece of software as it makes it easier to find later. I will use the directory /home/matthew/openoffice2 for this example.

In your file browser go to to the directory where you downloaded the file from openoffice.org and unpack the archive by doing a right click on the file OOo_2.0.0_LinuxIntel_install.tar.gz and select "Extract Here" from the right click menu.

Now, go back to the terminal and move to the directory just created that contains the rpms.

```
cd /home/matthew/openoffice2/OOO680_m3_native_packed-2_en-US.8968/RPMS
``` 
Now let's use alien to convert them to debs

```
sudo alien -d *.rpm
``` and wait a while while the conversion is done. You will see each file created appear on the screen as it is created. When all have been done you will be given a new command prompt. Then we need to install the new debs.
```
sudo dpkg -i *.deb
``` And wait again. The cool thing here is that later, if you want to uninstall Openoffice2.0 you will find it in Synaptic and can just uninstall it from there. When it finishes, the software is installed, but you still need to get it into your menus. There is an easy way to do this that the kind folks at OpenOffice have included for people using Debian-based distributions. We will change to the desktop-integration directory and install that.
```
cd /home/matthew/openoffice2/OOO680_m3_native_packed-2_en-US.8968/RPMS/desktop-integration
sudo dpkg -i openoffice.org-debian-menus_2.0.0-3_all.deb
``` And voila! You are done.

---

### Post by yhotg on 2005-10-21
hi.
do u unistall the repositories' package before installing the aliened final one?
or u do it later?
or what?

---

### Post by Laz on 2005-10-21
I did it after, - completely removed any openoffice with version 129. But maybe it's best to do it first.
But there is no longer any ref. in the new version to java runtime, and I'm not sure it will work with the JRE using Gij installed from start. Or the Blackdown JRE.
I'm used to Sun-java, so I'll try to find out how to make good debs from j2sdk-1_4_2_09-linux-i586.bin. I need Sun's version for other things like Eclipse.

Can any one help me ?

---

### Post by christooss on 2005-10-21
[QUOTE=Muffe]Why not just download the official debs (the debs released by the openoffice.org team)?[/QUOTE]

Where are those debs?

---

### Post by floyd27 on 2005-10-21
Why do i have openoffice 2 on my comp..?
I didnt DL a beta version it just came like that..

Is Oo 2 different then Oo 2.0  ?

I just checked and it is Open office 2.0...
I dont think I did anything special to get it...it was just there..

---

### Post by gmleuty on 2005-10-21
[QUOTE=floyd27]Why do i have openoffice 2 on my comp..?
I didnt DL a beta version it just came like that..
Is Oo 2 different then Oo 2.0  ?
I just checked and it is Open office 2.0...
I dont think I did anything special to get it...it was just there..[/QUOTE]

What you have is not actually 2.0 but 1.9.129. A few more bug fixes were applied between 1.9.129 and 2.0 Final.

I'd be highly surprised if 2.0 final is not made available in the next few days, either as  a "normal" security update, or from the backports repository.

Mike

---

### Post by jonesy on 2005-10-21
This is mostly to angrykeyboard, but if you check the release schedule for the other major distros, there are not rolling updates of major packages along the way.  For instance, when you install Fedora, you will only be installing security patches until the next major release, they don't roll out feature upgrades.  I believe Mandrake and SuSe are similar, there woulnd't be much of a point in doing releases if software was updated on a continual basis.  Henc the reason that source based distros (i.e., Gentoo) exist.  Yeah, they release a CD every once in a while to use for installs, but there is no real point in downloading it once you have Gentoo up and running.

The problem with the Linux world (discussed on slashdot many times) is choice.  The linux community wants choice, they thrive on it.  That's why there are 400+ distributions of linux (yeah, count them).  This makes it practically impossible for anyone to release packages suitable for all of those systems.  It's much easier to release a windows package, or a mac package, hence the reason OpenOffice does.  Just to support RedHat alone they'd have to release upwards of 10 packages.  If you want to see that kind of support in the linux world, it's not going to happen until standards are adopted that address packages, directory structures, and libraries so that only one package is needed to install on any linux based distro.

Anyway, there are no feature changes between beta 2 and 2.0 as far as i know, and the fact that it's part of the breezy release indicates that it's undergone significant debugging, it hasn't crashed on me yet . . .  There's no real reason to upgrade.

---

### Post by Benchrest on 2005-10-21
The base feature hasn't been available till now. I use the database feature of Works quite a bit. I think after I receive my breezy shipit I may try to install the new OO2 on my own. Be an educational experience. But I hadn't thought that it's available for windows too. I guess I'll check and see if it might be easier to do my conversion under Windows and then move my files to Ubuntu or ?. I can't migrate all my Works applications at once, but the Database function is the only one I haven't tested migrating a few test documents. I have used the spreadsheet a little but have heard it had problems. Rich

edit
PS Just downloaded the OO2 from thier web site and installed on my xp system. I was able to create a test db which doesn't work with 1.9.x on Ubuntu. Look forward to installing 2.0 on breezy. I am concerned about corequesites required but chances of it working should be better on breezy.

---

### Post by christooss on 2005-10-22
I created this how to

[http://ubuntuforums.org/showthread.php?t=80392](http://ubuntuforums.org/showthread.php?t=80392)

:)

---

### Post by angrykeyboarder on 2005-10-22
[quote=matthew]1. The rpms are contained in the tarball that you download from the openoffice.org website. I did this earlier today and installed them on a test computer using alien just like the other poster suggested and it worked GREAT. You extract the tarball to any directory you want (I would create /home/openoffice2) and you will find a directory nested inside labeled RPMS.[/quote] 

I wonder why they tarball an RPM?   Interesting.  

 In any event, the tradeoff is that you don't get all the other packages I mentioned previously (the KDE and GNOME integration, for example).

So I'll just do without. When it comes right down to it, I have OOo, KOffice and the so-called "GNOME-Office" and rarely use any of them. lol

My rants were based on principle anyway.

---

### Post by christooss on 2005-10-22
Hm how would you share around 15 rpm's?

---

### Post by tomwell on 2005-11-24
[QUOTE=angrykeyboarder]It doesn't take my mom ***6 months*** to cook anything. ;-)[/QUOTE]


LMAO!!!!

---

### Post by cjazz on 2005-11-25
I'm not sure when or even how I came across this, but several (??) weeks ago, I included the line

deb [http://people.ubuntu.com/~doko/OOo2](http://people.ubuntu.com/~doko/OOo2) ./

in my sources. list file, did a Synaptic search, and. lo and behold, Open Office 2 came cascading onto my system. Not that it changed much in the way I use my system. My work is word processor-intensive anyway, and I usually use AbiWord, which tends to be quicker than Open Office.

However, if it really did make that much of a difference to me, I'd probably use the generic Linux installer. It definitely wouldn't be an Ubuntu-killing issue for me.

---

