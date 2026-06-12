---
title: "Help Am Getting Furstrated"
date: 2007-09-20
forum: General Help
---

### Post by bigbrovar on 2007-09-20
Please could some one help me i been having a reoccurring problem of Duplicated source list any time i run sudo apt-get update....  [PHP]W: Duplicate sources.list entry http://ng.archive.ubuntu.com feisty/multiverse Packages (/var/lib/apt/lists/ng.archive.ubuntu.com_ubuntu_dists_feisty_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://ng.archive.ubuntu.com feisty/universe Packages (/var/lib/apt/lists/ng.archive.ubuntu.com_ubuntu_dists_feisty_universe_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com feisty-security/multiverse Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_multiverse_binary-i386_Packages)
W: Duplicate sources.list entry http://security.ubuntu.com feisty-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_feisty-security_universe_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
bigbrovar@bigbrovar-laptop:~$ 
[/PHP]


i have tried checkin my source list to see any source list that look exactly the same..but i found nothing..everything seem ok...i have tried everything i know but ..nothing seem to be working ..and the problem si so so frustrating..and i dont want to have to reinstall Feisty..please is there anything i can do or change or is there any command that would correct the problem...am really desperate...

here is my sourece list maybe u could help see what is not in the right place there..



[PHP]# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ng.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://ng.archive.ubuntu.com/ubuntu/ feisty restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ng.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://ng.archive.ubuntu.com/ubuntu/ feisty-updates main restricted #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ng.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ng.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ng.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://ng.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security restricted main multiverse universe #Added by software-properties
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse

deb http://deb.opera.com/opera/ stable non-free
deb http://www.virtualbox.org/debian feisty non-free
deb http://elisa.fluendo.com/packages feisty main
deb http://archive.ubuntustudio.org/ubuntustudio feisty main
# deb http://ppa.dogfood.launchpad.net/amaranth/ubuntu feisty main restricted universe multiverse
deb http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigator
deb-src http://download.tuxfamily.org/syzygy42/ feisty avant-window-navigator
deb http://hendrik.kaju.pri.ee/ubuntu feisty all
deb-src http://hendrik.kaju.pri.ee/ubuntu feisty all
# deb cdrom:[APTonCD for ubuntu feisty - i386 (2007-09-18 10:18) DVD1]/ /
deb http://ubuntusoftware.info/ edgy all
# deb cdrom:[APTonCD for ubuntu feisty - i386 (2007-09-18 10:18) DVD1]/ /[/PHP]


thanks in advance  :)

---

### Post by lisati on 2007-09-20
Did running ```
apt-get update
``` (you might need to use "sudo") make any difference?

---

### Post by bigbrovar on 2007-09-21
> 19 Hours Ago 10:58 AM
lisati 	
Re: Help Am Getting Furstrated
Did running
Code:

apt-get update

(you might need to use "sudo") make any difference?
 
Am sorry for not replying u on time i have been really sick and in the hospital ...am still there..anyway.i have tried and the problem usually come up when i do...please is there anything i can do to corect this...pleas any one

---

### Post by bigbrovar on 2007-09-21
is it that my problem is so peculiar that no body has a solution to it..is maybe they is no solution to it..so does this means that the only solution is formating..Damn! my Ubuntu experience as stopped being fun..as i have had to format and reinstalled ubuntu on my system than i ever remembered ever doing on windows.. the sad fact is that u are on ur own body cares or body gives a ****...its really sad :(

---

### Post by Soarer on 2007-09-21
You have a lot of repositories I don't recognise at the end of your listing. It may be that they duplicate some of the others.

Try commenting out each of them in turn until you no longer get the message when you update. It is also not a good idea to mix releases in repositories - you have Edgy & Feisty ones enabled.

And really, 2 hours is not long to wait for a reply - I hope you are feeling better now. :)

---

### Post by bigbrovar on 2007-09-21
well i guess i have to reinstall feisty ..as everything i have tried nothing seem to working...

---

### Post by Soarer on 2007-09-21
Do you even *read* the replies to your question?

---

### Post by Kingsley on 2007-09-23
Open up your sources list with this command.
```
sudo gedit /etc/apt/sources.list
```Then delete the contents and paste this.
```

[COLOR=#000000][COLOR=Black]## Major bug fix updates produced after the final release of the 
## distribution. 
[/COLOR][COLOR=Black]deb http[/COLOR][COLOR=Black]:[/COLOR][COLOR=Black]//ng.archive.ubuntu.com/ubuntu/ feisty-updates main restricted 
[/COLOR][COLOR=Black]deb[/COLOR][COLOR=Black]-[/COLOR][COLOR=Black]src http[/COLOR][COLOR=Black]:[/COLOR][COLOR=Black]//ng.archive.ubuntu.com/ubuntu/ feisty-updates main restricted #Added by software-properties 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## universe WILL NOT receive any review or updates from the Ubuntu security 
## team. 
[/COLOR][COLOR=Black]deb http[/COLOR][COLOR=Black]:[/COLOR][COLOR=Black]//ng.archive.ubuntu.com/ubuntu/ feisty universe 

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu  
## team, and may not be under a free licence. Please satisfy yourself as to  
## your rights to use the software. Also, please note that software in  
## multiverse WILL NOT receive any review or updates from the Ubuntu 
## security team. 
[/COLOR][COLOR=Black]deb http[/COLOR][COLOR=Black]:[/COLOR][COLOR=Black]//ng.archive.ubuntu.com/ubuntu/ feisty multiverse 

## Uncomment the following two lines to add software from the 'backports' 
## repository. 
## N.B. software from this repository may not have been tested as 
## extensively as that contained in the main release, although it includes 
## newer versions of some applications which may provide useful features. 
## Also, please note that software in backports WILL NOT receive any review 
## or updates from the Ubuntu security team. 
# deb http://ng.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse 
# deb-src http://ng.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse 

[/COLOR][COLOR=Black]deb http[/COLOR][COLOR=Black]:[/COLOR][COLOR=Black]//security.ubuntu.com/ubuntu feisty-security main restricted 
[/COLOR][COLOR=Black]deb[/COLOR][COLOR=Black]-[/COLOR][COLOR=Black]src http[/COLOR][COLOR=Black]:[/COLOR][COLOR=Black]//security.ubuntu.com/ubuntu feisty-security restricted main multiverse universe #Added by software-properties 
[/COLOR][COLOR=Black]deb http[/COLOR][COLOR=Black]:[/COLOR][COLOR=Black]//security.ubuntu.com/ubuntu feisty-security universe 
[/COLOR][COLOR=Black]deb http[/COLOR][COLOR=Black]:[/COLOR][COLOR=Black]//security.ubuntu.com/ubuntu feisty-security multiverse 

[/COLOR][COLOR=Black]deb http[/COLOR][COLOR=Black]:[/COLOR][COLOR=Black]//deb.opera.com/opera/ stable non-free 
[/COLOR][COLOR=Black]deb http[/COLOR][COLOR=Black]:[/COLOR][COLOR=Black]//www.virtualbox.org/debian feisty non-free 
[/COLOR][COLOR=Black]deb http[/COLOR][COLOR=Black]:[/COLOR][COLOR=Black]//elisa.fluendo.com/packages feisty main 
[/COLOR][COLOR=Black]deb http[/COLOR][COLOR=Black]:[/COLOR][COLOR=Black]//archive.ubuntustudio.org/ubuntustudio feisty main 
# deb http://ppa.dogfood.launchpad.net/amaranth/ubuntu feisty main restricted universe multiverse 
[/COLOR][COLOR=Black]deb http[/COLOR][COLOR=Black]:[/COLOR][COLOR=Black]//download.tuxfamily.org/syzygy42/ feisty avant-window-navigator 
[/COLOR][COLOR=Black]deb[/COLOR][COLOR=Black]-[/COLOR][COLOR=Black]src http[/COLOR][COLOR=Black]:[/COLOR][COLOR=Black]//download.tuxfamily.org/syzygy42/ feisty avant-window-navigator 
[/COLOR][COLOR=Black]deb http[/COLOR][COLOR=Black]:[/COLOR][COLOR=Black]//hendrik.kaju.pri.ee/ubuntu feisty all 
[/COLOR][COLOR=Black]deb[/COLOR][COLOR=Black]-[/COLOR][COLOR=Black]src http[/COLOR][COLOR=Black]:[/COLOR][COLOR=Black]//hendrik.kaju.pri.ee/ubuntu feisty all 
# deb cdrom:[APTonCD for ubuntu feisty - i386 (2007-09-18 10:18) DVD1]/ / 
[/COLOR][COLOR=Black]deb http[/COLOR][COLOR=Black]:[/COLOR][COLOR=#ff8000][COLOR=Black]//ubuntusoftware.info/ edgy all 
# deb cdrom:[APTonCD for ubuntu feisty - i386 (2007-09-18 10:18) DVD1]/ /  [/COLOR]
[/COLOR][/COLOR]
```[COLOR=#000000][/COLOR]

---

