---
title: "Question about Bluez"
date: 2013-04-04
forum: General Help
---

### Post by nicolamenicacci on 2013-04-04
Hi everyone,

I am happily running my Ubuntu 12.10 and am quite satisfied about it.
There is one thing I am consierding these days. Wanting to further improve my bluetooth performance, I was wondering if installing the latest Bluez version could be of any help. Any ideas/suggestions/comments?
Last but not least, should the game be worth the candle, shall I install it directly and it will overwrite the old version or shall I uninstall the current one first and then proceed?
Thanks everybody in advance,

Nicola

---

### Post by MsMeteorrock on 2013-04-04
Any update with your software for ubuntu should give you added benefits IMHO. You will not need to uninstall your bluetooth driver, it should update and upgrade fine over the driver you  have on your ubuntu build already. The code is just redefined for those drivers to work better. 

You can update also in the teminal with this code here. Remember you will need administrator rights to update. 

```
sudo apt-get update && sudo apt-get upgrade
```

---

### Post by nicolamenicacci on 2013-04-04
> **MsMeteorrock said:**
> Any update with your software for ubuntu should give you added benefits IMHO. You will not need to uninstall your bluetooth driver, it should update and upgrade fine over the driver you  have on your ubuntu build already. The code is just redefined for those drivers to work better. 

You can update also in the teminal with this code here. Remember you will need administrator rights to update. 

```
sudo apt-get update && sudo apt-get upgrade
```

Thanks for your reply.
So I could use the code to upgrade bluez, using such code?
```
sudo apt-get update bluez && sudo apt-get upgrade bluez
```
or is it meant to be a general command?
The Bluez package comes in a compressed folder. After extracting it and creating a folder, I have an "install" file which, double clocking on it, I can run on my prompt. Would it suffice, in your opinion, or would it be better to carefully read the readme file?
Sorry for the silly question, but the only time I had a similar situation was to install drivers for a printer, therefore I had no previous versions installed.
Thanks in advance for your time and kindness.

---

### Post by Elfy on 2013-04-04
If you wanted to just update bluez you could

```
sudo apt-get update
```

which updates the information on your system to match the repos.

Then see if there is an upgraded package available

```
sudo apt-get upgrade
```

apt-get update and upgrade are general commands - not specific.
You can abort that with N or let system upgrade the packages that are available for upgrade. 

You can check here to see if the version has changed.

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

You can find which version you have installed on your system from a terminal

```
apt-cache policy bluez
```

Currently I believe the 12.10 version is 4.101-0ubuntu6

You could reinstall bluez to see if there is an update - which would update it on it's own.

```
sudo apt-get install bluez --reinstall
```

```
sudo apt-get install bluez --reinstall
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 0 not upgraded.
```



or 

```
sudo apt-get install bluez
```

will tell you if the version is not upgradable.

```
sudo apt-get install bluez
Reading package lists... Done
Building dependency tree       
Reading state information... Done
bluez is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
```

---

### Post by nicolamenicacci on 2013-04-04
Wow this was a fantastic reply with a lot of interesting specific things, a great tutorial.
I already knew about the unspecific nature of the sudo apt-get update or upgrade commands, but it's great to have ti confirmed.
Following you last code, namely

```
sudo apt-get install bluez
```

I had the confirmation bluez is at its latest version. If I wanted the 5.3 one, I should probably add a repository.
The code gave the following outcome

```
Lettura elenco dei pacchetti... Fatto
Generazione albero delle dipendenze       
Lettura informazioni sullo stato... Fatto
bluez è già alla versione più recente.
I seguenti pacchetti sono stati installati automaticamente e non sono più richiesti:
  calligra-l10n-engb calligra-l10n-it kde-l10n-engb kde-l10n-it kde-l10n-zhcn
  kdevelop-l10n kdevelop-php-docs-l10n kdevelop-php-l10n language-pack-kde-en
  language-pack-kde-it libasprintf0c2:i386 libcroco3:i386 libgettextpo0:i386
  libgomp1:i386 libunistring0:i386
Usare "apt-get autoremove" per rimuoverli.
0 aggiornati, 0 installati, 0 da rimuovere e 0 non aggiornati.
```

I therefore used
```
sudo apt-get autoremove
```
and had them removed. then proceeded with the usual pat-get update. All works fine.

I just wonder if I should keep this bluez version or force the new one, maybe adding new repositories. All things considered, I may leave this one, since bluetooth works and the issue I want to fix (get a headset with micropohne to work on Skype) seems impossible right now, as far as I have checked.

Thanks for your contribution and in advance if you could answer my last doubt.

---

### Post by Elfy on 2013-04-04
I've never used a microphone and unfortunately only use a real phone so I can't help with skype issues :)

You could '*possibly*' find a ppa with updated bluez. 

As far as skype is concerned try searching for similar issues, if not start a new thread for that.

[www.googlubuntu.com](www.googlubuntu.com) for searching works quite well.

---

