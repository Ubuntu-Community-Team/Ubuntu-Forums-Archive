---
title: "understanding file locations/installing programs"
date: 2006-10-09
forum: General Help
---

### Post by T-Bone55 on 2006-10-09
Hi folks.
I'm new to Linux and Ubuntu.  I have installed Dapper and added automatix and wine.  So far so good.  I'm quite impressed and like certain things about linux (like using synaptic to download multiple programs at once).  I'm currently trying to get more comfortable with the terminal feature since I'm much more used to the GUI environment (and will likely always be).
I'm comfortable with windows and understand the drives and folders.  IT's a bit different with linux where everything seems to be a sub folder of "/"...even cd rom drives. So here are my questions.  :
1. When I install programs from synaptic, where are they installed? which folder?
2. I installed a program called guitar pro 5 using Wine and accepted the default location (of course now I have no idea where that was, but it started with "C:"... Where is that going, seeing as there is no C: drive per se.
3. if I install linux programs in the future, should I install them into my "home" folder or another folder?
4. After installing a few programs from automatrix, my desktop now has a few new icons on it.  Can I delete those without buggering up my system? (ie, are they like "shortcuts" in Windows equivalent terms?) 
5. If you could direct me to reading material on this subject I would be appreciative too

Thanks.  I'm really enjoying my foray into linux and hope to learn more about operating systems in general by doing this.  As a casual computer user It's a steep learning curve...
T-bone

---

### Post by bswilson on 2006-10-09
T-bone, it sounds like you have a lot to learn about Linux filesystems, so I recommend you start with [this article]("http://www.linux.org/lessons/beginner/index.html"), which I think will help you a lot.

Regarding installing programs with **wine**, there's something that new Linux users usually miss.  The wine program gives you a *virtual* C:\ drive that is stored in your home directory in a hidden subdirectory.  Open **nautilus** and type **Ctrl-H** to show hidden directories and files.  You should see a folder called **.wine**.  Go into that folder, and you should see a subfolder called **drive_c**.  That is essentially your C:\ drive.  Inside it, you'll start seeing folders you recognize, including the programs you installed.

As for installing other programs, there's no *foolproof* rule that dictates where something will be installed.  Usually, components are installed in different places (libraries in /usr/share/lib, etc., etc.)...  I came across a document that will help you, though.  It is called [How to install ANYTHING in Ubuntu]("http://monkeyblog.org/ubuntu/installing/").  Check that out.

---

### Post by aysiu on 2006-10-09
You don't really need to know where programs install to. They install to many places, just as they do in Windows.

Yes, the bulk of the files in Windows appear to install to C:\Program Files\*programname*, but, as we all know, you can't properly uninstall a Windows program by simply deleting its directory from C:\Program Files. There are libraries everywhere, registry keys, etc.

Same thing in Ubuntu. The launcher for the program is most likely in /usr/bin, but there are also libraries in /usr/lib and maybe some other documents in /usr/share. You don't need to know where all the files go to. You just need to know how to start the program.

For almost all programs, you start the program with the name of the program. For example, to start Firefox, you use the command ```
firefox
``` You don't need to type out the whole path ```
/usr/bin/firefox
``` just as in Windows you can also launch it by typing ```
firefox
``` instead of ```
C:\Program Files\Mozilla Firefox\Firefox.exe
```

The Wine directory path is as follows:
/home/*username*/.wine/drive_c/Program Files

When you launch a Wine program, though, you have to use backslashes: ```
wine "z:\home\*username*\.wine\drive_c\Program Files\*programname*\*programname*.exe"
``` Since Wine programs are using a hack to launch non-native programs, you do have to specify the entire path--you can't just type the program name.

---

### Post by T-Bone55 on 2006-10-09
Thanks to both of you for responding.  In particular, thanks for the link to the beginner article.  Very appropriate for my level.

---

