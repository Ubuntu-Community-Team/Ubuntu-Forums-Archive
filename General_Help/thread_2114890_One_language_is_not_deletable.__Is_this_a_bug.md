---
title: "One language is not deletable.  Is this a bug?"
date: 2013-02-11
forum: General Help
---

### Post by GameX2 on 2013-02-11
Hi,


I have this issue since a while.  I don't know why this happen, that's not annoying, just curious.
Anyone have this problem?  Is this a bug or what?
That's just weird.

[https://dl.dropbox.com/u/67605655/language.png](https://dl.dropbox.com/u/67605655/language.png)

I've installed the French language, and deleted all other languages.  However, for some reason, this other language (Chinese?) is not deleted.  When I press the buttons "Install / Delete languages", only French is selected.

...Weird.

Is this normal ??
Thanks

---

### Post by U202E on 2013-02-11
maybe you need root to delete this, like most important settings.
try to: open a terminal -> sudo gnome-control-center -> give your password
and configure your language settings.

be aware that when you open a program/file/something as root - by typing su/sudo - you'll have full access to the system so be careful!

---

### Post by GameX2 on 2013-02-11
> **U202E said:**
> maybe you need root to delete this, like most important settings.
try to: open a terminal -> sudo gnome-control-center -> give your password
and configure your language settings.

be aware that when you open a program/file/something as root - by typing su/sudo - you'll have full access to the system so be careful!

Good suggestion;
Unfortunately, even when ran as Root, French still remain the only checked language in the windows, that's all:

[https://dl.dropbox.com/u/67605655/Language2.png](https://dl.dropbox.com/u/67605655/Language2.png)

Remove others languages is always the first I do on a Ubuntu installation.  For some reason, this language would not delete, even on a freshly installed system.

---

### Post by Bufeu on 2013-02-11
Should work:> sudo apt-get purge -y language-pack-zh

---

### Post by GameX2 on 2013-02-11
It's not working;
I installed English, so you won't read a message in French (The Chinese language is still there):

```
gamex@Portable-Ubuntu:~$ sudo apt-get purge -y language-pack-zh 
[sudo] password for carl: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'language-pack-zh' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```

---

### Post by Bufeu on 2013-02-11
> **GameX2 said:**
> It's not working;
I installed English, so you won't read a message in French (The Chinese language is still there):

```
gamex@Portable-Ubuntu:~$ sudo apt-get purge -y language-pack-zh 
[sudo] password for carl: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Virtual packages like 'language-pack-zh' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
```Ah, read here: [http://askubuntu.com/questions/207505/how-to-completely-remove-virtual-packages](http://askubuntu.com/questions/207505/how-to-completely-remove-virtual-packages).

---

### Post by GameX2 on 2013-02-11
> **Bufeu said:**
> Ah, read here: [http://askubuntu.com/questions/207505/how-to-completely-remove-virtual-packages](http://askubuntu.com/questions/207505/how-to-completely-remove-virtual-packages).

So that was installed, because of another package?

> Therefore you cannot remove virtual packages, you need to remove the **real** packages from which the 'virtual' ones was referenced or created from.

What is the real package I should remove?  French language (Since Engligh is now installed..?), then reinstall it ?

---

### Post by bantuvez on 2013-02-11
> **GameX2 said:**
> 
Remove others languages is always the first I do on a Ubuntu installation.

When I install Ubuntu it only installs the language what I chose. At default it shouldn't install all the languages, I think. That would make no sense.

---

### Post by GameX2 on 2013-02-11
> **bantuvez said:**
> When I install Ubuntu it only installs the language what I chose. At default it shouldn't install all the languages, I think. That would make no sense.
I'm not sure, I don't quietly remember.  It sure would be logical to install only one language, thought.
I never managed to delete Chinese, for some reason..

---

### Post by bantuvez on 2013-02-11
Try removing:

language-pack-zh-hans
language-pack-zh-hans-base
language-pack-zh-hant
language-pack-zh-hant-base

If those present on your system. Thats my only guess.

---

### Post by Bufeu on 2013-02-11
> **GameX2 said:**
> So that was installed, because of another package?



What is the real package I should remove?  French language (Since Engligh is now installed..?), then reinstall it ?
Maybe some program needs it?

---

### Post by GameX2 on 2013-02-11
I've tried this, it say the packages aren't installed.

```
language-pack-zh-hans
language-pack-zh-hans-base
language-pack-zh-hant
language-pack-zh-hant-base
```In Synaptic, these packages also aren't installed, apparently.  I've tried cleaning the configuration and useless packages using Synaptic, cleaning them using Ubuntu-Tweak, and also from the Terminal doing:

```
sudo apt-get autoremove
sudo apt-get purge
```I've rebooted, and these languages are still there.  I also installed "language-pack-zh-hans", "language-pack-zh-hant", "language-pack-zh-hans-base", "language-pack-zh-hant-base", "language-pack-gnome-zh-hans" and "language-pack-gnome-zh-hant", "language-pack-gnome-zh-hans-base" from Synaptic.  I rebooted, The languages installed correctly, then I've removed them from Synaptic (Complete removal.  I've also clean what's remaining and the APT-Cache as usual).

After another reboot, I've now have 3 remaining "ghost" Chinese languages in the list.. O__o

I've recorded a video (Thanks RecordMyDesktop!):
[https://dl.dropbox.com/u/67605655/Language_Error.ogv](https://dl.dropbox.com/u/67605655/Language_Error.ogv)

Should I file a bug report?  Never actually did that, I rarely jump to conclusion of "THIS IS A BUG".

I was wondering if this happen because of "iBus".  From what I read, it's used to read/write latin languages, and it's installed on my system.  Notice that when I put the Chinese language on top of the list, the keyboard typing method automaticly switch to "iBus".

Should I delete it?  Never used this.  I'm not sure if it's safe, it came with Ubuntu.
Also tried something else, when I've installed the chinese pack, I setted the Chinese as default language, then rebooted.  I realised that only a very few windows/text was in Chinese.  The rest was all in French.

---

### Post by GameX2 on 2013-02-22
Allright, so I've followed the post #3 here, and I've managed to get rid of the chinese language:

[http://ubuntuforums.org/showthread.php?t=2050993](http://ubuntuforums.org/showthread.php?t=2050993)

But now the problem I have, I already tried different ways to remove the chinese, like this here:
[https://help.ubuntu.com/community/LocaleConf](https://help.ubuntu.com/community/LocaleConf)

I probably messed up something, I don't know.  Now, in the languages, I have French (France) (How do I get French Canada?) and English, that won't delete the normal way.

What's much more annoying now, is that a few applications that were originally in French display in English! :S

How can I fix this?

Here are my language files:

/etc/environment:

```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANGUAGE="fr_CA.UTF-8"
LANG="fr_FR.CA.UTF-8"
LC_NUMERIC="fr_CA.UTF-8"
LC_TIME="fr_CA.UTF-8"
LC_MONETARY="fr_CA.UTF-8"
LC_PAPER="fr_CA.UTF-8"
LC_IDENTIFICATION="fr_CA.UTF-8"
LC_NAME="fr_CA.UTF-8"
LC_ADDRESS="fr_CA.UTF-8"
LC_TELEPHONE="fr_CA.UTF-8"
LC_MEASUREMENT="fr_CA.UTF-8"
```

/etc/default/locale :
```

LANG="fr_CA.UTF-8"
LANGUAGE="fr_CA.UTF-8"
LC_NUMERIC="fr_CA.UTF-8"
LC_TIME="fr_CA.UTF-8"
LC_MONETARY="fr_CA.UTF-8"
LC_PAPER="fr_CA.UTF-8"
LC_IDENTIFICATION="fr_CA.UTF-8"
LC_NAME="fr_CA.UTF-8"
LC_ADDRESS="fr_CA.UTF-8"
LC_TELEPHONE="fr_CA.UTF-8"
LC_MEASUREMENT="fr_CA.UTF-8"
```

/home/gamex/.pam_environment : 

```
LANGUAGE=fr_CA.UTF-8
LANG=fr_CA.UTF-8
LC_NUMERIC=fr_CA.UTF-8
LC_TIME=fr_CA.UTF-8
LC_MONETARY=fr_CA.UTF-8
LC_PAPER=fr_CA.UTF-8
LC_NAME=fr_CA.UTF-8
LC_ADDRESS=fr_CA.UTF-8
LC_TELEPHONE=fr_CA.UTF-8
LC_MEASUREMENT=fr_CA.UTF-8
LC_IDENTIFICATION=fr_CA.UTF-8
```

Thank you!

---

