---
title: "Removing snap package makes the package uninstallable with apt"
date: 2024-06-05
forum: General Help
---

### Post by greigsteve on 2024-06-05
I seem to have installed Firefox originally using snap on my Ubuntu 22.04.4 desktop. Now I want to remove that installation and reinstall using apt.

I ran: ***sudo snap remove --purge firefox*** which did seem to remove firefox from my system. However when I run ***sudo apt install firefox, ***I get a message saying: "firefox is already the newest version (1:1snap1-0ubuntu2)".

It seems as if snap registered firefox as installed with the apt system but did not unregister when I removed firefox so now apt thinks firefox is installed when it is not.

I would like to know more about what is causing this behaviour and help in achieving my goal which is to install firefox on my system with apt.

---

### Post by howefield on 2024-06-05
The firefox deb package for Ubuntu 22.04 is a dummy package which installs the snap version.

You'd probably want to uninstall the snap version and add a firefox ppa. There are plenty of websites with instructions, [here is one]("https://www.omgubuntu.co.uk/2022/04/how-to-install-firefox-deb-apt-ubuntu-22-04").

---

### Post by greigsteve on 2024-06-05
If I have understood your first sentence correctly it raises a slightly different question to my original one which is: why, having removed firefox, does Ubuntu tell me it is already installed when I try and reinstall it? It still looks to me as if ***sudo snap remove --purge firefox ***did not do its job properly??

I have to admit that I agree with Linus Torvolds ([https://www.youtube.com/watch?v=Pzl1B7nB9Kc](https://www.youtube.com/watch?v=Pzl1B7nB9Kc)) that package management in Linux distros is "a major f...... pain in the ....". It has made users and developers lives miserable. Yes he and we should all behave like angels and not swear but it does help to illustrate the seriousness of the issue. I think Debian have got a terrible attitude towards applications because they inappropriately try and improve them and tweak them before packaging. They should leave that to the application developers and just concentrate on making it easy for the developers to get their applications installed on users' machines.

The really bad news is that dreadful though Debian is and its derivatives it is probably the best OS available. If they got packaging right they would have nothing much to do and it would be an even better system.

Sorry for the rant and thanks for the link!

---

### Post by Dennis N on 2024-06-05
> why, having removed firefox, does Ubuntu tell me it is already installed when I try and reinstall it? It still looks to me as if sudo snap remove --purge firefox did not do its job properly??
When you remove the snap package firefox, you do not remove the apt package named firefox. The apt package is not actually the firefox browser, but is a small package (77 Kb) that installs the firefox snap. 

Here it is:
```
dmn@Kayleigh:~$ apt show firefox
Package: firefox
Version: 1:1snap1-0ubuntu5
Priority: optional
Section: web
Origin: Ubuntu
Download-Size: 77.3 kB
```

If you don't want the snap version installed, your options are:
1) use a PPA to get a .deb verson
2) download a Firefox package from Mozilla and manually install it.
3) use the Flatpak version of Firefox.

---

### Post by grahammechanical on 2024-06-05
> I seem to have installed Firefox originally using snap on my Ubuntu 22.04.4 desktop.

If I remember correctly, a fresh install of 22.04 LTS will install Firefox as a snap package by default. An online upgrade from 20.04 LTS to 22.04 LTS will convert the Firefox deb packaged version with the Firefox snap packaged version. And a fresh install of 24.04 LTS will install both the Firefox snap version and the Thunderbird snap version.

And there we are.

Regards

---

### Post by ajgreeny on 2024-06-05
I have been using firefox downloaded as the firefox.tar.gz direct from Mozilla using this link [https://www.mozilla.org/en-GB/firefox/download/thanks/](https://www.mozilla.org/en-GB/firefox/download/thanks/)
Note this one is for the UK but I think your browser will go to the correct link for your location.

If you have a one user system you can extract the archive where it is in Downloads and then run Firefox from the executable file in that extracted archive.
Very simple, but it would normally be placed in /opt and run from there.

It will either update automatically or can be set to notify you when it needs updating.
Running it this way has been faultless for me since I started using it when Ubuntu replaced the apt version wiith the snap version.

I do not personally use any snaps on my systems and have removed the complete snap infrastructure from them all.

Incidentally, as I'm now on 24.04 I also use Thunderbird in the same manner and it is similarly successful

---

### Post by Tadaen_Sylvermane on 2024-06-05
If it's there I missed it. If you wish to put the snap package back in place you and either uninstall the apt firefox package or do ```
apt install --reinstall firefox
``` That will reactivate the script it contains to pull the snap. Just for future reference.

---

