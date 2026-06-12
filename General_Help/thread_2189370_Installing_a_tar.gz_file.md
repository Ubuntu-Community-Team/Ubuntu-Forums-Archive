---
title: "Installing a tar.gz file?"
date: 2013-11-22
forum: General Help
---

### Post by grier-devon on 2013-11-22
Hello everyone,
I am wanting to install Linux Tycoon in Ubuntu 13.10, I noticed it is not in the software centre so I went and downloaded the game directly. The file is called  lt-1-linux.tar.gz and I have never installed a tar.gz before. Can anyone help me with this.

---

### Post by sanderj on 2013-11-22
Open a terminal, go to the directory containing the tar.gz, and type "tar xvzf ...tar.gz"

Or use Nautilus, and click on the tar.gz to unpack it

---

### Post by jamesisin on 2013-11-22
So, a tarball (a .tar.gz file) is a compressed archive much like a .zip or .7z file.  Unpacking it will merely take the containing files and uncompress them.  You will likely have to do more than that.  If you search for instructions for installing that game in the version of Ubuntu you are running, you may well find a nice HowTo to assist you.

I usually try to locate a repository for software I add (rather than downloading installation packages or tarballs) as this makes keeping it up to date and managing dependencies a lot easier.  Adding a repository to your current list of repositories is pretty easy if you are able to locate one.

---

### Post by vasa1 on 2013-11-22
Also check that you have the right version; you wouldn't want to try installing a 32-bit program on a 64-bit OS. It may have been trivial previously but I and a couple of other people have not found it possible to install 32-bit software on 64-bit *buntu 13.10.

---

### Post by heir4c on 2013-11-22
Linux Tycoon is only available in the SoftwareCenter in 12.04 and 12.10 (see in the link on the left side):
[https://apps.ubuntu.com/cat/applications/linux-tycoon/](https://apps.ubuntu.com/cat/applications/linux-tycoon/)
Just for testing and to help I downloaded the tar.gz from this link:
[http://lunduke.com/linux-tycoon/](http://lunduke.com/linux-tycoon/)
and choose to save it and unpack it in the Download folder. 
After that I open the folder he created and click on the executable file but it will not start.
Than I go back to the downloadsite to download it again and choose now to open with the archiefmanager to unpack directly. 
Than I double click on the second file I saw and he say he can't find any program to open. 
So I use the option to search via internet for something for that and I get a pop up with say that I must install PyPar2 and so I click OK.
After all install that it will still not start up.
I use 14.04 (but that is still 13.10).

So if you will play that game, than you must install 12.04 on a other partition or computer and installing and playing it there.

---

### Post by grier-devon on 2013-11-22
> **heir4c said:**
> Linux Tycoon is only available in the SoftwareCenter in 12.04 and 12.10 (see in the link on the left side):
[https://apps.ubuntu.com/cat/applications/linux-tycoon/](https://apps.ubuntu.com/cat/applications/linux-tycoon/)
Just for testing and to help I downloaded the tar.gz from this link:
[http://lunduke.com/linux-tycoon/](http://lunduke.com/linux-tycoon/)
and choose to save it and unpack it in the Download folder. 
After that I open the folder he created and click on the executable file but it will not start.
Than I go back to the downloadsite to download it again and choose now to open with the archiefmanager to unpack directly. 
Than I double click on the second file I saw and he say he can't find any program to open. 
So I use the option to search via internet for something for that and I get a pop up with say that I must install PyPar2 and so I click OK.
After all install that it will still not start up.
I use 14.04 (but that is still 13.10).

So if you will play that game, than you must install 12.04 on a other partition or computer and installing and playing it there.

Thank you so much, I spent about two hours on google and could not find a way to get that thing installed. Also thanks to everyone for giving me a general direction of how to install tar.gz since I have never used one of these files. I will just install XUbuntu 32 Bit in a VM to play, thanks to everyone!

---

### Post by CatKiller on 2013-11-23
If it was in the repositories for earlier Ubuntu versions you can probably just download the older .deb file from there and install that. Much easier than managing a VM installation.

---

