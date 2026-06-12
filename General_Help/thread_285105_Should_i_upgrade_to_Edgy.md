---
title: "Should i upgrade to Edgy?"
date: 2006-10-26
forum: General Help
---

### Post by 2pacalypse on 2006-10-26
I've noticed that the new ubuntu, Edgy Eft was released and so im thinking about upgrading to it. however before i update i want to check some things... i looked in other threads but they dont really anwser my question. Basicly I want to know if Edgy is worth while for me.

I use the computer for Internet(Firefox&Azuerus), abit of Games (Mainly WoW), Homework (especially in C language) and, ofcourse trying to learn the Linux system step by step, And one of the two most importent things for me is Stablity and then Performence. however I would like the new ubuntu because it says its faster, and has more up to date software (firefox 2.0 etc.) and im willing to put up with bugs as long as they arent seriosly effecting the system preformence/stablity and the system is actually better then Dapper.further more i would like to preserve all my system information if possible, and still use the same programs i used in Dapper. So, I Should i upgrade to Edgy?

p.s.

Does the Sys. Requirments for Edgy are higher then Dapper?

---

### Post by PriceChild on 2006-10-26
> **2pacalypse said:**
> And one of the two most importent things for me is Stablity and then Performence.
If it ain't broke... don't fix it. Remember the dapper desktop will be supported for another year after they stop supporting edgy.
> and has more up to date software (firefox 2.0 etc.)
read up on the backports project
> and im willing to put up with bugs as long as they arent seriosly effecting the system preformence/stablity and the system is actually better then Dapper.
In my opinion definately better ;)
> further more i would like to preserve all my system information if possible, and still use the same programs i used in Dapper.
A normal upgrade should keep all settings and documents...
> So, I Should i upgrade to Edgy?
Its your call ;)

---

### Post by ssalman on 2006-10-26
The only person who can determine that is you. Install Edgy on a separate partition, give it a run for few days, and if you like it, you can either switch your main partition, or upgrade your Dapper partition to Edgy...  Or if you don't like missing with all this, you can give the liveCD a trial for few days, but I really recommend installing Edgy on a separate partition as you'll have more room to fix any issues you may run into with your hardware.


just my $0.02  :D

---

### Post by Dinerty on 2006-10-26
If you want to learn about linux and use the newer software, then I do highly recommend it, I personally been using it since knot 3 and have had no real problems at all with stability, (Only problems I have are using Beryl with it).

gnome 2.16 is noticably faster then it predecesor and makes your system more responsive.

I don't really use that many programs, just the usual Opera, Firefox, Kopete, all of which work perfectly even with Flash 9 beta.

You could just download the CD and run it from that to take a brief peak around the system, or dual boot dapper/edgy?

---

### Post by skymt on 2006-10-26
> **PriceChild said:**
> read up on the backports project

Firefox 2 isn't likely to be back-ported. Too many packages in Dapper require FF 1.5 for Gecko.

---

### Post by PriceChild on 2006-10-26
> **skymt said:**
> Firefox 2 isn't likely to be back-ported. Too many packages in Dapper require FF 1.5 for Gecko.Doesn't FF2 include gecko also though?

At the end of the day, there're howtos out there to install the latest firefox anyway.

---

### Post by skymt on 2006-10-26
> **PriceChild said:**
> Doesn't FF2 include gecko also though?Of course it does. It's just that Dapper packages that use Gecko are compiled against FF 1.5, and won't work with 2.0 without a recompile. That's a lot of work. There could conceivably be a back-port package of 2.0 that installs alongside 1.5. That would be the easiest option, until XULRunner is finished.

---

### Post by PriceChild on 2006-10-26
Thanks for clarification :) you learn something every day :)

---

### Post by beerfan on 2006-10-26
> **ssalman said:**
> Install Edgy on a separate partition, give it a run for few days, and if you like it, you can either switch your main partition, or upgrade your Dapper partition to Edgy...
Who doesn't partition all available disk space when they install an OS? :-) I guess gparted lets you resize partitions though. Is that safe to do?

---

### Post by Old Pink on 2006-10-26
Everything in Edgy can be acheived in Dapper, really. 

Why not compile Firefox 2.0 or even 3.0 (alpha nightly build) from source in Dapper? :)

---

### Post by 2pacalypse on 2006-10-26
> **PriceChild said:**
> 
If it ain't broke... don't fix it. Remember the dapper desktop will be supported for another year after they stop supporting edgy.

I know. but eitherway theres probably gonna be a newer version after Edgy (after all new ubuntu comes out approx every 6 months) and the new version will be supported longer ;)

> **PriceChild said:**
> 
In my opinion definately better ;)

Can you describe in what way it is better? wheres the diffrent between them both?

> **PriceChild said:**
> 
A normal upgrade should keep all settings and documents...


uh, I probably forgot to mention im kinda noob ;) Im only recently learned  about basic *nix system structure. 

> **PriceChild said:**
> 
Its your call ;)

Here lies the problem, decisions ;).

I'll probably try the liveCD and if I like it I'll give it a little partition (eitherway i was gonna format the Windows partition this weekend ;))

Thanks for the advice ;) if you got anything else to add, please do.

---

### Post by beerfan on 2006-10-26
> **Old Pink said:**
> Everything in Edgy can be acheived in Dapper, really. 

Why not compile Firefox 2.0 or even 3.0 (alpha nightly build) from source in Dapper? :)

Why not? Why I ask? What's wrong with the Mozilla builds?

---

### Post by skymt on 2006-10-26
> **Old Pink said:**
> Everything in Edgy can be acheived in Dapper, really. 

Why not compile Firefox 2.0 or even 3.0 (alpha nightly build) from source in Dapper? :)

Everything? How about installing Upstart in Dapper? I'd sure like to see *that* howto. Not to mention all the replies it would get, complaining of broken systems.

Xorg 7.1? Gnome 1.16? Some things are just not that easy to install without a package.

---

### Post by PriceChild on 2006-10-26
> **2pacalypse said:**
> I know. but eitherway theres probably gonna be a newer version after Edgy (after all new ubuntu comes out approx every 6 months) and the new version will be supported longer ;)No... Dapper will be supported for another 6 months after Feisty's ends...
> Can you describe in what way it is better? wheres the diffrent between them both?Well boot times are amazing and will improve even more in Feisty when upstart is properly implemented. There's just so many little tweaks and features everywhere...
> uh, I probably forgot to mention im kinda noob ;) Im only recently learned  about basic *nix system structure.We're all newbs, you haven't seen me on gentoo ;)
> Here lies the problem, decisions ;).
I'll probably try the liveCD and if I like it I'll give it a little partition (eitherway i was gonna format the Windows partition this weekend ;))
that's the best plan of action :)
> 
Thanks for the advice ;) if you got anything else to add, please do.good luck :)

---

### Post by SebMKd on 2006-10-26
Just would like to understand one thing: Can you "upgrade" dapper with the Edgy CD and keep all the programs you've installed? (Totem-Xine, Script for Nautilus - such as Baobab -, Listen, GnomeBaker, Realplayer, Flash for Firefox, VLC... etc) Or would you have to reinstall everything because of dependency issues?:neutral: 

Thanks!

---

### Post by skymt on 2006-10-26
> **SebMKd said:**
> Just would like to understand one thing: Can you "upgrade" dapper with the Edgy CD and keep all the programs you've installed? (Totem-Xine, Script for Nautilus - such as Baobab -, Listen, GnomeBaker, Realplayer, Flash for Firefox, VLC... etc) Or would you have to reinstall everything because of dependency issues?:neutral: 

Thanks!

The best way to upgrade is a simple apt dist-upgrade from the net repositories. If you already have a CD, add it to your sources.list before the dist-upgrade, and it will pull whatever upgrades it can from there, saving you the download time.

---

### Post by SebMKd on 2006-10-26
> **skymt said:**
> The best way to upgrade is a simple apt dist-upgrade from the net repositories. If you already have a CD, add it to your sources.list before the dist-upgrade, and it will pull whatever upgrades it can from there, saving you the download time.

Hey Skymt. Thanks for the prompt answer. I take that if you advise upgrading it means that the answer to my question is: yes, upgrade and you won't lose your programs. Right? :-? 

I'm new to Linux. Could you point me towards a page where the 'apt dist-upgrade' is more detailed? I've never even open my source.list :( 

S.

---

### Post by skymt on 2006-10-26
> **SebMKd said:**
> Hey Skymt. Thanks for the prompt answer. I take that if you advise upgrading it means that the answer to my question is: yes, upgrade and you won't lose your programs. Right? :-? 

I'm new to Linux. Could you point me towards a page where the 'apt dist-upgrade' is more detailed? I've never even open my source.list :( 

S.

You won't lose your programs. You should back up, of course, because any system change can have bad consequences.

Option 1: If you don't mind a long download, and haven't messed with your system too much, you should try the automated install. Basically, you open a terminal and run:```
gksudo update-manager -c
```Enter your password, and follow the prompts. Restart when you're done, and if nothing went wrong, you'll be running Edgy.

Option 2: Option 2 is the manual upgrade. If the automatic way doesn't work, ask about this way.

Option 3: If you have an Edgy CD, you can upgrade from the CD to save download time. You end up with the same result, though, and the total download time (including downloading the CD image) will be longer. Only go with this option if you already have an Edgy CD. If you go with this option, ask how first.

---

### Post by andyfraser on 2006-10-26
I think I'm a bit late here but I'd wait before upgrading. I've only been using Edgy for a couple of hours and so far it seems a bit rough. This could be because it's supposed to be more bleeding edge than Dapper. Knowing the Ubuntu devs it'll smooth out in time.

I had installation problems. I've tried every version of Ubuntu and this is the first time I've had problems installing it.

Evolution only seems to let me set up one account. Attempts to set up another account seem to work but it doesn't appear. Instead the first account is renamed to the same name as the second. I'm still investigating this one before I file a bug report. I'll try KMail in the meantime.

Gnome 2.16 seems slower than 2.14 on my machine. There doesn't seem to be any new features worth the upgrade so far. I've heard that CD burning in Nautilus has been improved but I haven't tried it yet.

Setting up Samba file sharing still seems to require the use of smbpasswd on the command line, at least I can't find a GUI to add a user. Fedora Core 5 had this.

On the plus side, it's good to see Firefox 2 so soon.

Overall I'd say Edgy is only slightly worse than Dapper (which is excellent) but the with the problems I've encountered so far I wouldn't recommend it yet. I'll still be handing out Dapper CDs for the foreseeable future.

A sticking point for me with Dapper was that not all software automatically appears in the menu, most notably the KOffice suite and some other KDE apps. It's no real problem to add the software manually but it's a pain. So far everything I've installed on Edgy has appeared in the menu but KOffice is still downloading. The repositories are slow tonight. I guess everyone's hitting them hard.

Update: As with Dapper, only some KDE software appears in the menu automatically. KMail works beautifully.

---

### Post by nardis_Miles1 on 2006-10-27
Thanks for the practical advice. What I would like to know is:

1. Now that edgy is released, have any other users experienced difficulties with the upgrade? Does X break? are fonts mysteriously lost or uglified? Does your system run slower? Did the upgrade put you in broken dependency hell?

2. If the answers to 1 are pleasant (no major breakage), do you (subjectively) like edgy better? Are there packages that work better (better xorg?, better openoffice?) Is gnome better?

---

### Post by 2pacalypse on 2006-10-27
Ok, First impression of Edgy...

Exactly like Dapper :P. only slightly faster boot up (maybe 5 secs) Firefox 2.0 (The Only real advantage of it) and, a really annoying/ugly Windows XP like start up. Unlike the old ubuntu which showed a little ubuntu logo + loading line and details about boot up. generally I'm pretty disappointed because i hoped theres going to be a serious difference like Dapper did to breezy 

I'll still keep Edgy for a few days, just to check it out. but i think that eventually I'll stay with dapper

P.S.

Does any1 know how to install Firefox 2.0 on Dapper?

---

### Post by ferd on 2006-10-27
I installed Swiftfox2 instead. It is ready with a Debian installer. Saves a lot of hassle and is faster.:cool:

---

### Post by skymt on 2006-10-27
> **nardis_Miles1 said:**
> Thanks for the practical advice. What I would like to know is:

1. Now that edgy is released, have any other users experienced difficulties with the upgrade? Does X break? are fonts mysteriously lost or uglified? Does your system run slower? Did the upgrade put you in broken dependency hell?

2. If the answers to 1 are pleasant (no major breakage), do you (subjectively) like edgy better? Are there packages that work better (better xorg?, better openoffice?) Is gnome better?

1. I've had no problems. X worked throughout the upgrade, fonts are fine, my system seems a bit faster, and dependency-wise this was the easiest upgrade I've ever done. I can't guarantee it will be as easy in your case, I'm just telling you it was in mine. Also, I upgraded a couple weeks before release, so it may be even easier now.

2. Edgy isn't really that much different, outwardly. All the packages are newer versions, which is nice. Gnome is up to 2.16. A major bug in QT 3 Designer is apparently finally fixed, but I'm using 4 now. :rolleyes: 

A lot of people whine about the new usplash, but I like it. If you don't, there are hi-res versions of the Dapper usplash available various places.

Upstart has promise, but it isn't used much in Edgy. I expect a much greater performance gain in Feisty.

---

### Post by skymt on 2006-10-27
> **2pacalypse said:**
> Ok, First impression of Edgy...

Exactly like Dapper :P. only slightly faster boot up (maybe 5 secs) Firefox 2.0 (The Only real advantage of it) and, a really annoying/ugly Windows XP like start up. Unlike the old ubuntu which showed a little ubuntu logo + loading line and details about boot up. generally I'm pretty disappointed because i hoped theres going to be a serious difference like Dapper did to breezy 

I'll still keep Edgy for a few days, just to check it out. but i think that eventually I'll stay with dapper

P.S.

Does any1 know how to install Firefox 2.0 on Dapper?

You can get the old Usplash back. [Tangerine Edgy Usplash](http://www.gnome-look.org/content/show.php?content=46645) is a hi-res version of the Dapper Usplash. If you want the status text, edit /boot/grub/menu.lst and remove "quiet" wherever it appears.

There are some serious differences internally, so you may want to rethink that downgrade.

---

