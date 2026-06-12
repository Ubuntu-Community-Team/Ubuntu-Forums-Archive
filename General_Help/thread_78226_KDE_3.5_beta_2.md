---
title: "KDE 3.5 beta 2"
date: 2005-10-18
forum: General Help
---

### Post by luna6 on 2005-10-18
Just installed KDE 3.5 beta 2....which is pretty damn slick. Nothing drastically new, but everything just looks nicer from first impressions.

---

### Post by Manny C on 2005-10-18
Has Beta 2 been released? From [here]("http://developer.kde.org/development-versions/kde-3.5-release-plan.html"):
> **October 12th, 2005: Beta2 is prepared**     Beta 2 is prepared and released after some initial testing.     The incoming bugs will be reviewed for their severity.


But I haven't seen any release notifications on dot.kde.org

---

### Post by luna6 on 2005-10-18
I jumped the gun, by looking for a ftp that had it ...

I added this to my apt sources.list :

deb [ftp://ftp.kde.org/pub/kde/unstable/3.5-beta2/kubuntu/](ftp://ftp.kde.org/pub/kde/unstable/3.5-beta2/kubuntu/) breezy main

and did the sudo apt-get update, apt-get upgrade ...and voila~....

the official release is the 18th so after they finish syncing up the mirrors should see a notice sometime today....Im liking 3.5 beta 2.....!

---

### Post by piquadrat on 2005-10-18
The KDE server's getting very slow already (no wonder, with all the mirrors syncing). Here's a faster one:

```
deb http://ftp.funet.fi/pub/mirrors/ftp.kde.org/pub/kde/unstable/3.5-beta2/kubuntu/ breezy main

```

[edit]That one's getting hammered, too, apparently. Here's another one:
```
deb http://spout.ussg.indiana.edu/kde/unstable/3.5-beta2/kubuntu/ breezy main
```[/edit]

---

### Post by Manny C on 2005-10-18
Hehe...OK folks...you heard it first here! :)

---

### Post by Manny C on 2005-10-18
Incidentally luna6, did you notice any of [these]("https://wiki.ubuntu.com/KubuntuKDE35BetaKnownProblems") bugs?

---

### Post by MartinG on 2005-10-18
I had the artsd and Akregator bugs, the artsd one making it almost unusable.  Still, one of the joys of Synaptic is the ease with which you can downgrade dodgy packages (libarts1c2 and akregator).

--
MartinG

---

### Post by luna6 on 2005-10-18
I didnt have the bugs ...though I have not tried adding a new user or locking the kde session (those two I cant say yet), but the other ones were not applicable to me. hope that helps...cheers

---

### Post by getaceres on 2005-10-18
I get both of the bugs. Too bad.
Also, the panel corruption when using a transparent kicker is not solved. I only upgraded for that. 
I didn't know it was worse than the beta1. I hope the RC will be better.

---

### Post by debutgland on 2005-10-18
numlockx doesnt launch at startup for me, bug on akregator too, I have compiled the version 1.02

---

### Post by debutgland on 2005-10-18
lost notification for gaim...

---

### Post by Rumo on 2005-10-18
If have the artsd bug, too. It's really annoying, but minimizing the error message helps (not nice, but at least a solution till 3.5 stable arrives)

---

### Post by getaceres on 2005-10-19
[QUOTE=Rumo]If have the artsd bug, too. It's really annoying, but minimizing the error message helps (not nice, but at least a solution till 3.5 stable arrives)[/QUOTE]
Disable the sound system. Anyway you can't have it while this bug remains. That should get rid of the message.

---

### Post by MartinG on 2005-10-19
Alternatively, downgrade libarts1c2. This also affects the arts metapackage, but no other libraries/programs are affected AFAIK.

--
MartinG

---

### Post by shenmue on 2005-10-19
When I run sudo apt-get update, it showed "GPG error......NO_PUBKEY.", how to solve this?

Thanks a lot.

---

### Post by Manny C on 2005-10-19
Install Jonathan Riddell's key:
[quote=http://www.kubuntu.org/announcements/kde-35beta1.php]These packages have been digitally signed using [Jonathan Riddell's key]("http://www.kubuntu.org/announcements/kubuntu-packages-jriddell-key.gpg"). You can import the key into apt using *sudo apt-key add kubuntu-packages-jriddell-key.gpg*.[/quote]

---

### Post by Zinoc on 2005-10-19
Is the kopete version with webcam support in this beta ? I don't saw any information about this.

---

### Post by z_pod on 2005-10-19
Hi all,

just ugraded KDE from 3.4.3 to 3.5-B2 (and koffice to 1.4.2 aswell).
All is working fast & smooth (veeery, veery fast !!) but for some kicker little issues such which I'm sure will be solved b4 1.5 will be out.

I attach a little screenshot for your viewing pleasure.


PS.: Of course konqueror is the 1st browser to pass the acid2 test...:smile:

---

### Post by asimon on 2005-10-19
[QUOTE=z_pod]PS.: Of course konqueror is the 1st browser to pass the acid2 test...:smile:[/QUOTE]
Safari did it before.

---

### Post by z_pod on 2005-10-19
[QUOTE=asimon]Safari did it before.[/QUOTE]


I'm afraid not... I'm currently running OSX 10.3.x on my powerbook and Safari is very far from render correctly the mad yellow guy ;) .I know it works with latest (beta) safari under 10.4... but I don't feel like upgrading to 10.4 yet.

Cheers

---

### Post by AndersAA on 2005-10-19
anyone seen any amd64 repos / scripts for auto building and installing it into /opt or something?

---

### Post by shenmue on 2005-10-19
I upgraded to 3.5 Beta2, and suffered the "soundserver (artsd) crashed" problems which was mentiond in [https://wiki.ubuntu.com/KubuntuKDE35BetaKnownProblems](https://wiki.ubuntu.com/KubuntuKDE35BetaKnownProblems). 

And I got my Menu a little messed up, too.

---

### Post by escobar on 2005-11-04
Is upgrading to 3.5 beta 2 using the earlier mentioned repo ok for Hoary?

---

### Post by DimaIL on 2005-11-05
[QUOTE=luna6]Just installed KDE 3.5 beta 2....which is pretty damn slick. Nothing drastically new, but everything just looks nicer from first impressions.[/QUOTE]
Can you paste here some 3.5 pictures ?

Thanks.
Dima

---

### Post by luna6 on 2005-11-05
per request heres some screen shots of 3.5 beta2 after using it for a few weeks - I get the arts sound crash on boot up but no big deal for me because the alsa engine works fine, feels quicker + konqueror loads file directories much faster, and has been running stable + kopete can do video as well now (even got my logitech messenger working via spca5xx driver). 

Desktop
[http://img494.imageshack.us/img494/1216/kde35b20so.jpg](http://img494.imageshack.us/img494/1216/kde35b20so.jpg)

Kopete + Amarok
[[img=http://img498.imageshack.us/img498/7969/kde35kopeteamarok3dw.th.jpg]](http://img498.imageshack.us/my.php?image=kde35kopeteamarok3dw.jpg)

Vmware running Windows XP
[[img=http://img95.imageshack.us/img95/1171/kde35vmwarewindowsxp1jy.th.jpg]](http://img95.imageshack.us/my.php?image=kde35vmwarewindowsxp1jy.jpg)

Konqueror + Yakuake
[[img=http://img497.imageshack.us/img497/5996/kde35yakuakekonqueror7ng.th.jpg]](http://img497.imageshack.us/my.php?image=kde35yakuakekonqueror7ng.jpg)

---

### Post by sal on 2005-11-05
[QUOTE=luna6]per request heres some screen shots of 3.5 beta2 after using it for a few weeks - I get the arts sound crash on boot up but no big deal for me because the alsa engine works fine, feels quicker + konqueror loads file directories much faster, and has been running stable + kopete can do video as well now (even got my logitech messenger working via spca5xx driver). 

Desktop
[http://img494.imageshack.us/img494/1216/kde35b20so.jpg](http://img494.imageshack.us/img494/1216/kde35b20so.jpg)

Kopete + Amarok
[[img=http://img498.imageshack.us/img498/7969/kde35kopeteamarok3dw.th.jpg]](http://img498.imageshack.us/my.php?image=kde35kopeteamarok3dw.jpg)

Vmware running Windows XP
[[img=http://img95.imageshack.us/img95/1171/kde35vmwarewindowsxp1jy.th.jpg]](http://img95.imageshack.us/my.php?image=kde35vmwarewindowsxp1jy.jpg)

Konqueror + Yakuake
[[img=http://img497.imageshack.us/img497/5996/kde35yakuakekonqueror7ng.th.jpg]](http://img497.imageshack.us/my.php?image=kde35yakuakekonqueror7ng.jpg)[/QUOTE]

re:kopete can do video

will it also do audio chat as well is it it just text chat with cam?
tia

---

### Post by luna6 on 2005-11-05
can't say for sure about the audio part (I dont have a mic to check)....but I dont see an option for voice, unless the option appears only for computers with mics, which i doubt. havent used kopete in awhile, and did see "send nudge" option for MSN in Kopete as well as send Video option.

---

### Post by joakim2 on 2005-11-07
I tried the betas but I was disappointed to see the same funky Konqueror behavior that was there somewhere along the way in 3.4 as well where images take aaaaaages to load and hitting a link on the page while the page you are looking at hasn't finished loading will lead to a "can't find server" error. Annoying enough to launch Firefox after 10 minutes of using Konqueror and leave it that way :(

Also, the betas don't seem to be compiled with zeroconf and/or DAAP as neither of those are recognized as kio_slaves (daap:/ zeroconf:/). Not sure if the plan is to enable them before release or not.

---

### Post by ounas on 2005-11-07
[QUOTE=piquadrat]The KDE server's getting very slow already (no wonder, with all the mirrors syncing). Here's a faster one:

```
deb http://ftp.funet.fi/pub/mirrors/ftp.kde.org/pub/kde/unstable/3.5-beta2/kubuntu/ breezy main

```

[edit]That one's getting hammered, too, apparently. Here's another one:
```
deb http://spout.ussg.indiana.edu/kde/unstable/3.5-beta2/kubuntu/ breezy main
```[/edit][/QUOTE]

Thanks funet works fine for me...

-Ounas :D

---

### Post by skyboy on 2005-11-08
hi, 
upgraded to beta2, suffered from arts, couldnt fix it, removed kde, installed beta1, then beta2, now everything workes great. No sound bug, just kopete show the offline user when new user comes online, but i can live with it :)
kopete webcam can only send at the moment right ???

because amsn (svn) receive and send already. there are some bugs but it basically work. But kopete is nicer I think. :)

---

### Post by Zinoc on 2005-11-08
[QUOTE=skyboy]
kopete webcam can only send at the moment right ???
[/QUOTE]

Did'nt try sending, but receiving works in kopete.

---

### Post by joakim2 on 2005-11-10
[QUOTE=joakim2]I tried the betas but I was disappointed to see the same funky Konqueror behavior that was there somewhere along the way in 3.4 as well where images take aaaaaages to load and hitting a link on the page while the page you are looking at hasn't finished loading will lead to a "can't find server" error. Annoying enough to launch Firefox after 10 minutes of using Konqueror and leave it that way :([/QUOTE]

OK, so I couldn't leave this alone :) I believe the solution, if like me, you are plagued by the "unknown host" errors in Konqueror is to turn off ipv6. You can do this by modifying /etc/modprobe.d/aliases like so:

alias net-pf-10 ipv6 off
alias net-pf-10 off
alias ipv6 off
#alias net-pf-10 ipv6

and (optionally?) commenting out all the ipv6 stuff from /etc/hosts

Konqueror is cruising now and everything is happy place happy place!

---

