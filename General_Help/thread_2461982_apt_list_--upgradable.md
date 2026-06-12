---
title: "apt list --upgradable"
date: 2021-05-11
forum: General Help
---

### Post by Old Jimma on 2021-05-11
Ubuntuers:

I  did a sudo apt update this morning and got a few messages that i thought I don't understand and thought should pay heed to.

Here is one of the messages:

> 
[COLOR="#FF0000"][COLOR="#FF0000"]8 packages can be upgraded. Run 'apt list --upgradable' to see them.[/COLOR][/COLOR]
 

So I ran that command and got the following response:

> 
$ sudo apt list --upgradable
Listing... Done
firefox-locale-en/focal-updates,focal-security 88.0.1+build1-0ubuntu0.20.04.2 amd64 [upgradable from: 88.0+build2-0ubuntu0.20.04.1]
firefox/focal-updates,focal-security 88.0.1+build1-0ubuntu0.20.04.2 amd64 [upgradable from: 88.0+build2-0ubuntu0.20.04.1]
gir1.2-javascriptcoregtk-4.0/focal-updates,focal-security 2.32.0-0ubuntu0.20.04.1 amd64 [upgradable from: 2.30.6-0ubuntu0.20.04.1]
gir1.2-webkit2-4.0/focal-updates,focal-security 2.32.0-0ubuntu0.20.04.1 amd64 [upgradable from: 2.30.6-0ubuntu0.20.04.1]
libexiv2-27/focal-updates,focal-security 0.27.2-8ubuntu2.2 amd64 [upgradable from: 0.27.2-8ubuntu2]
libjavascriptcoregtk-4.0-18/focal-updates,focal-security 2.32.0-0ubuntu0.20.04.1 amd64 [upgradable from: 2.30.6-0ubuntu0.20.04.1]
libwebkit2gtk-4.0-37/focal-updates,focal-security 2.32.0-0ubuntu0.20.04.1 amd64 [upgradable from: 2.30.6-0ubuntu0.20.04.1]
python3-yaml/focal-updates,focal-security 5.3.1-1ubuntu0.1 amd64 [upgradable from: 5.3.1-1]



What does this mean? And what action should I take with this information??

Stumped, again, on the day of his [COLOR="#FF0000"]**1000110th (binary) hexidecimal**[/COLOR] birthday,
Old JImma from the Old Country

---

### Post by schragge on 2021-05-11
```
sudo apt upgrade
```
will upgrade the listed packages. As all upgrades listed seem to come from the focal-security repository this is what you should do.

> **Old Jimma said:**
> Stumped, again, on the day of his [COLOR=#FF0000]**1000110th (binary) hexidecimal**[/COLOR] birthday
1000110 binary is only 46 hexadecimal
```
echo 16o 2i 1000110p|dc
```
Congratulations!

---

### Post by ActionParsnip on 2021-05-11
The output shows the current version and the version that is available in your sources

---

### Post by ajgreeny on 2021-05-11
I use two aliases to run upgrades in terminal as follows, saving a lot of typing.
[B][I]alias ud='sudo apt update ; apt list --upgradable'
alias ug='sudo apt upgrade'[/I][/B]
Both of those two lines are in the hidden **.bash_aliases** file in my home, along with a huge number of other aliases, so I type just four characters to update the repos, list the upgradable packages then install all those packages listed for upgrade.
Very quick, very simple and wonderfully effective.

---

### Post by Old Jimma on 2021-05-17
HI ajgreeny,

Thank you for your reply. Wish I understood it fully so that I could use it.

Are you recommending creating a .bash_aliases file in my home directory and adding the lines you typed in bold face?

What four characters do you type? 

I typed those apt commands and got :

> 
ubuntu-advantage-tools/focal-updates 27.0.2~20.04.1 amd64 [upgradable from: 20.3]
ubuntu-advantage-tools/focal,now 20.3 amd64 [installed,upgradable to: 27.0.2~20.04.1]


I tried to add these lines into synaptic > settings > respositories > other software

.... however, I couldn't add them. Do I add "

What do I do with those lines? I tried to add them in but coudn't. Do I add "http://ppa." at the beginning of each of those lines?

Old Jimma

---

### Post by VMC on 2021-05-17
aliases just make input easier. For example mine is upd, and upd8. Therefore I type "upd && upd8" to inquire for updates, then update if there is any.

[alias upd='sudo apt update', alias upd8='sudo apt upgrade']

---

### Post by ajgreeny on 2021-05-17
Those two lines in bold in my last post
[B][I]alias ud='sudo apt update ; apt list --upgradable'
alias ug='sudo apt upgrade'[/I][/B]
are the exact lines in my .bash_aliases file, along with many others (over 100) and what I type is the characters before the = sign.  They are simply shortcuts for much longer commands.

So I open a terminal, type ***ud*** and the terminal runs the command ***sudo apt update ; apt list --upgradable***.
Then if any packages are listed as upgradable I type ***ug*** and terminal runs the command ***sudo apt upgrade***.

As I said, it's quick, very simple and effective.

---

### Post by Old Jimma on 2021-05-17
Thank you!

---

### Post by GhX6GZMB on 2021-05-17
[COLOR=#FF0000][I]"8 packages can be upgraded. Run 'apt list --upgradable' to see them."

[/I][/COLOR]Completely normal and harnless. It's just an informational message. I ignore it and just run:

```
sudo apt update
sudo apt upgrade
sudo apt autoremove
```

Autoremove is the one you need to watch. If there's a high number of entries to be removed, you have a real problem somewhere else (disconnected depencies).

---

### Post by schragge on 2021-05-20
It seems everybody has their aliases, so here are mine:
```
alias ac='apt-cache show'
alias acd='apt-cache depends'
alias acn='apt-cache pkgnames'
alias acp='apt-cache policy'
alias acr='apt-cache rdepends'
alias acs='apt-cache search'
alias af='apt-file search'
alias afl='apt-file list'
alias ag='sudo apt-get upgrade'
alias aga='sudo apt-get autoremove'
alias agb='sudo apt-get build-dep'
alias agc='sudo apt-get clean'
alias agg='sudo apt-get dist-upgrade'
alias agi='sudo apt-get install'
alias agl='apt-get changelog'
alias agp='sudo apt-get purge'
alias agr='sudo apt-get remove'
alias ags='apt-get source'
alias agu='sudo apt-get update'
alias am='apt-mark showmanual'
alias ama='sudo apt-mark auto'
alias amh='sudo apt-mark hold'
alias amm='sudo apt-mark manual'
alias amu='sudo apt-mark unhold'
alias ati='sudo aptitude install'
alias ats='aptitude search'
alias atv='aptitude versions'
alias atw='aptitude why'
alias ax='axi-cache search'
alias axa='axi-cache again'
alias axl='axi-cache last'
alias axm='axi-cache more'
```

---

### Post by ajgreeny on 2021-05-20
I'm not sure I would ever remember all those apt-get or apt aliases without mixing them up completely as they are all a bit too similar, but nevertheless, it does show just how very useful they can be for long complicated commands.

---

