---
title: "Skype - installation problems"
date: 2005-09-30
forum: General Help
---

### Post by megamania on 2005-09-30
Hi everybody,

being an absolute beginner with Linux, I've been a silent reader for a while. I have many questions to ask, but try to search the ubuntu forums as much as possible before asking.

Now I'm having trouble installing Skype and I need help.

- I first tried to install the DEB package from the skype website. Skype was installed but the package was marked as defective, and in uninstalled everytime I launch the Synaptic Package Manager.
The strange thing is that Skype works (the sound quality is terribly bad, but that one will be my next question!)

- on these forums I read that a solution was to download the RPM and Alien it. I did it and this is what I came up with when installing:

-----------------------------------------
sudo dpkg -i skype_1.2.0.17-1_i386.deb
Password:
(Lettura del database ... 63274 file e directory attualmente installati.)
Mi preparo a sostituire skype 1.2.0.17-1 (con skype_1.2.0.17-1_i386.deb) ...
Spacchetto il rimpiazzo di skype ...
Configuro skype (1.2.0.17-1) ...

translation:
reading database... 63274 files and dirs currently installed
Preparing to substitute skype... (with ...)
Unpacking the skype replacement
Configuring Skype
------------------------------------------

That's all! The Skype icon which was created when I installed the DEB package (not the "Alien" RPM package) disappeared from the gnome applications menu and I don't know what to do.

Any help will be appreciated!

Gianfranco

---

### Post by bugi on 2005-09-30
There is some problem with recently published version of Skype for Ubuntu. I would suggest to install static binary version until new version will be available. You can go to the Skype/Linux forum [http://forum.skype.com/viewforum.php?f=18](http://forum.skype.com/viewforum.php?f=18) for more info.

---

### Post by megamania on 2005-10-01
Thanks for the advice. Unfortunately, when I double-click on the icon of the static version I get:

bzip2: (stdin) is not a bzip2 file.
tar: Child returned status 2
tar: Uscita per errore ritardata dall'errore precedente (exit delayed by previous error)

Any ideas?

---

### Post by jeremy on 2005-10-02
get the previous version and follow instructions from;
[http://ubuntuguide.org/#skype](http://ubuntuguide.org/#skype)

---

### Post by megamania on 2005-10-02
thanks. I managed to install the previous version.

The sound quality appears to be worse than the newer release, but I guess I'll just have to be patient until a new "working" version is released.

Thanks again,
gianfranco

---

