---
title: "Can't get dependencies in Synaptics"
date: 2008-02-25
forum: General Help
---

### Post by olavjunior on 2008-02-25
Trying to install build essential. Then I get an error saying there's some undeclared dependencies. 

It says: 
```
build-essential:
 Depends on: libc6-dev but won't be installed
```

I've never gotten these errors before!

---

### Post by Scheater5 on 2008-02-25
Sure you're connected to the internet, got the repos turned on?

---

### Post by olavjunior on 2008-02-25
yepp, I can install other things like ex screenlets..

I've got all the repos turned on. And they shouldn't even be listed in synaptics if not..

---

### Post by gpilkay on 2008-02-25
Just as a double-check, from 'software sources', under the 'ubuntu software' tab, make sure every thing's clicked by source code.  Then hit ok, it should re-load your options.  Then try Synaptic again.  I had an upgrade recently de-select a few of my repositories, it may cause your problem too.

After that you can try to re-install Build Essential, first to a 'mark for complete removal', restart just in case, and reload and see if that helps.  

Good luck!

---

### Post by olavjunior on 2008-02-25
Hm, nope everythings fine. (But source-code had a minus sign "-" instead of v. So I changed from Norwegian source to the main server. But it's still the same after reading the sources over again)

Pherhaps a plain old reboot will help...

---

### Post by gpilkay on 2008-02-25
Oops, I meant everything should be clicked EXCEPT source code (I'm going by mine which is working).  I have everythign enabled except the source as I don't use it.

My mis-type, sorry.

---

### Post by olavjunior on 2008-02-25
Still, it doesn't make any difference...

---

### Post by Scheater5 on 2008-02-25
Quite odd that something like build-essential would hang on a dependency when so many people use it.  Do you have any 3rd party repos on?
You could always pull g++ off packages.ubuntu.com.  I hesitate to suggest that, because it's sort of circumventing your problem, which may be the sign of some other problem (like contradicting repos, or even a bug in synaptic) but at least it will get the job and and let you install build-essential.

---

### Post by olavjunior on 2008-02-26
I have g++ in synaptic (not installed). So I've tried mark that for installation, but then I get the same error with some other dependencies. And in the end I end up in a dependency loop. 

:S

---

### Post by Yellow Pasque on 2008-02-26
Try installing from the terminal:
```
sudo apt-get install build-essential libc6-dev
```

What output do you get?

---

### Post by olavjunior on 2008-02-26
The same error!
And 
E: Destroyed packages

What's E?

---

### Post by Yellow Pasque on 2008-02-26
Ok, do this for me:
```
cat /etc/apt/sources.list
```
Paste output here

Also, try:
```
sudo apt-get clean
sudo apt-get update
sudo apt-get install build-essential
```

---

### Post by olavjunior on 2008-02-26
```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ gutsy universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://archive.ubuntu.com/ubuntu/ gutsy-security main restricted multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-security universe

#awn
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator

# Google testing repository
deb http://dl.google.com/linux/deb/ testing non-free

#test av siste tracker
deb http://ppa.launchpad.net/pochu/ubuntu gutsy main
deb-src http://ppa.launchpad.net/pochu/ubuntu gutsy main

deb http://apt.emesene.org/ ./
deb-src http://apt.emesene.org/ ./

```

And still the same error after your last tip

---

### Post by julian67 on 2008-02-26
You don't have the Ubuntu source repository either listed or enabled. This is why you're having this problem. Add the following line to your sources list ```
deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted
``` and save it. 

and then use this command in a terminal ```
sudo apt-get update && sudo apt-get install build-essential
```

You could alternatively now install build-essential using synaptic

It should all work fine now

---

### Post by olavjunior on 2008-02-26
Hehe, no. Still the same output! This is starting to be hilarious :D

Noticed one thing though: When I added your line, if I then go to software sources, the "source code" box has a minus ( - ) in it. If I mark it to a v, and update, your line is removed from sources.list. But with or without your line, I just keep on getting the same error.. :(```
Reading state information ... Ferdig    
Noen pakker kunne ikke installeres. Dette kan bety at du har bedt om
en umulig tilstand eller, hvis du bruker den ustabile utgaven av Debian,
at visse kjernepakker ennå ikke er laget eller flyttet ut av «Incoming» for
distribusjonen.

Ettersom du bare bestilte et enkelt inngrep er det overveiende sannsynlig
at pakken helt enkelt ikke kan installeres, og du bør fylle ut en feilmelding.
Følgende informasjon kan være til hjelp med å løse problemet:

Følgende pakker har uinnfridde avhengighetsforhold:
  build-essential: Avhenger av: libc6-dev men skal ikke installeres eller
                                libc-dev
                   Avhenger av: g++ (>= 4:4.1.1) men skal ikke installeres
E: Ødelagte pakker

```

I know, it's in Norwegian, but you get the picture. It says I've asked for an impossible state, and that I might be using the unstable version of debian. Then it says that since I just asked for one simple operation, it is highly likely that the package can't be installed and that I should fill a bug report. ... ... ...  :(

---

### Post by julian67 on 2008-02-26
OK had another look at your sources.list. You also don't have source repos for updates, universe or multiverse, or backports. Also you have no security repos at all. 

again edit your sources.list and add these lines:

```
deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe

```

and again ```
sudo apt-get update && sudo apt-get install build-essential
```

---

### Post by olavjunior on 2008-02-26
nope... still the same..

And now my sources.list looks like this:
```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://no.archive.ubuntu.com/ubuntu/ gutsy main restricted multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://no.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted multiverse

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://no.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://no.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://no.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://no.archive.ubuntu.com/ubuntu/ gutsy-security main restricted multiverse
deb http://no.archive.ubuntu.com/ubuntu/ gutsy-security universe

#awn
deb http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42 gutsy avant-window-navigator

# Google testing repository
deb http://dl.google.com/linux/deb/ testing non-free

#test av siste tracker
deb http://ppa.launchpad.net/pochu/ubuntu gutsy main
deb-src http://ppa.launchpad.net/pochu/ubuntu gutsy main

deb http://apt.emesene.org/ ./
deb-src http://apt.emesene.org/ ./

deb-src http://archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe

```

---

### Post by julian67 on 2008-02-26
Mine looks like this and I have no problems (build-essential is installed). You can modify it to use your local (no) mirrors and add/remove the 3rd party repos as desired. 

```
# 
# deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release Candidate i386 (20071009.1)]/ gutsy main restricted

# deb cdrom:[Xubuntu 7.10 _Gutsy Gibbon_ - Release Candidate i386 (20071009.1)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://gb.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://gb.archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://download.tuxfamily.org/3v1deb feisty 3v1n0
deb http://archive.canonical.com/ubuntu feisty-commercial main
# deb http://packages.thinkgos.com/gos/ painful main
# deb-src http://packages.thinkgos.com/gos/ painful main

# deb http://morgoth.free.fr/ubuntu gutsy-backports main

```

Another possibility is that your  package list cache is corrupted, in which case you would need to delete *contents* of /var/lib/apt/lists and /var/lib/apt/lists/partial directories

---

### Post by olavjunior on 2008-02-26
ok, deleted the /var/liv/apt/list content. But how do i update it afterwards? An simple sudo apt-get update won't do..

---

### Post by julian67 on 2008-02-26
As long as you still have the directories /var/lib/apt/lists and /var/lib/apt/lists/partial then syanptic should update.

Did you try modifying and using my sources.list first? This was what I intended.  I suggested corruption of the package lists as a possibility....kind of surprised you seem to have gone to that first.

---

### Post by olavjunior on 2008-02-26
Well, I just wanted to try you last tip fist since I didn't believe there was something wrong with my sources.list.  But I shouldn't have deleted the parial folder. So with the partial folder in place, synaptic updated. But still no luck with my problem. 

So I copied your sources.list, but even this didn't help :(

Where can the bug be??? What is the "E: Destroyed packages" ????

---

### Post by julian67 on 2008-02-26
Perhaps your package cache is corrupted. 

```
sudo apt-get clean
``` which should remove all cached packages. Then try again with ```
sudo apt-get update && sudo apt-get install build-essential
```

---

### Post by olavjunior on 2008-02-26
nope, already tried that!

---

### Post by julian67 on 2008-02-26
Have you tried
```
sudo apt-get -f install build-essential
```

the -f option will try to fix broken dependencies. I wonder how your system got into this state?

---

### Post by olavjunior on 2008-02-26
I'll try that later when I get the time. But after using your list, I have 32 updates. I notice that some of them is about apt and update-manager. Am I safe to use your list unmodified?? Maby updating will fix the probs.

---

### Post by julian67 on 2008-02-26
> **olavjunior said:**
> I'll try that later when I get the time. But after using your list, I have 32 updates. I notice that some of them is about apt and update-manager. Am I safe to use your list unmodified?? Maby updating will fix the probs.

It's hard to say something is safe if your package-management is already broken....but that list is fine as far as I know. The only 3rd party repositories enabled in it are medibuntu and tuxfamily. You can easily uncheck them in Synaptic and then reload.

---

### Post by az on 2008-02-26
#awn
deb [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator
deb-src [http://download.tuxfamily.org/syzygy42](http://download.tuxfamily.org/syzygy42) gutsy avant-window-navigator

# Google testing repository
deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) testing non-free

#test av siste tracker
deb [http://ppa.launchpad.net/pochu/ubuntu](http://ppa.launchpad.net/pochu/ubuntu) gutsy main
deb-src [http://ppa.launchpad.net/pochu/ubuntu](http://ppa.launchpad.net/pochu/ubuntu) gutsy main

deb [http://apt.emesene.org/](http://apt.emesene.org/) ./
deb-src [http://apt.emesene.org/](http://apt.emesene.org/) ./

Perhaps one of these archive installed a version of libc6 that is not in the official repos.

What version of libc6 are you running?

---

### Post by olavjunior on 2008-02-26
My version of libc6 is 2.7-5ubuntu2

And by the way, sudo apt-get -f install build-essential doesn't help!

---

### Post by julian67 on 2008-02-26
> **olavjunior said:**
> My version of libc6 is 2.7-5ubuntu2

And by the way, sudo apt-get -f install build-essential doesn't help!

That's the version for Hardy.....have you been experimenting?

---

### Post by olavjunior on 2008-02-26
Oups! :D

No, not that I know of actually. Only installed Hardy on VirtualBox, but that shouldn't influence anything of course.. Is there any way of downgrading the hardy stuff? Damn, mabey it's easiest to just upgrade to Hardy?

The last thing I've installed is emesene...

Maybe the installation of tracker 0.6.4 changed some of my files to Hardy-versions? Do you think? I can't think of anything that can have done it..

---

### Post by julian67 on 2008-02-26
open synaptic, find libc6, click on it and then from the title bar menu item "package" select "force version" and choose version 2.6.1-1 which is the correct version for Gutsy.  At some point you've installed the Hardy version, possibly from an unofficial repo and possibly when downloading deb packages from websites and installing them. When you revert libc6 to correct version it's going to uninstall (and hopefully not simply break)  anything that depends on the Hardy version.

---

### Post by olavjunior on 2008-02-26
Searched through synaptics history, and nothing shows up for libc6 2.7
The 20th of Jan it updated libc6 to 2.6.1-1ubuntu10. That's all..

Argh!.. I've also installed Matlab & Maple not to long ago.. Something has messed my system up when they shouldn't have.

---

### Post by olavjunior on 2008-02-26
> **julian67 said:**
> open synaptic, find libc6, click on it and then from the title bar menu item "package" select "force version" and choose version 2.6.1-1 which is the correct version for Gutsy.  At some point you've installed the Hardy version, possibly from an unofficial repo and possibly when downloading deb packages from websites and installing them. When you revert libc6 to correct version it's going to uninstall (and hopefully not simply break)  anything that depends on the Hardy version.

Followed you advice here, and apparently only libc6 was affected. Now I'm back at libc6 2.6.1-1ubuntu10

AND now everything seems GOOD! Seems I finally can install everything :popcorn:

You're great! Thanks :)

---

### Post by julian67 on 2008-02-26
> **olavjunior said:**
> Followed you advice here, and apparently only libc6 was affected. Now I'm back at libc6 2.6.1-1ubuntu10

AND now everything seems GOOD! Seems I finally can install everything :popcorn:

You're great! Thanks :)

actually the thanks should go to az who pinned it down accurately.

---

### Post by olavjunior on 2008-02-26
I've given you both a thank! You're both great :) 
Thanks so much for your time !!

---

