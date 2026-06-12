---
title: "Commands for ubuntu - How to use - List/Tutorials?"
date: 2007-11-03
forum: General Help
---

### Post by foolios on 2007-11-03
I was hoping there was a list of how to use commands for ubuntu. There are some thngs that I've downloaded that require them to use. I don't have a clue how to use these packages and was hoping there was a list of what they are and what they do.

Also, this superuser and terminal usage. If there's a tut on that I'd appreciate a link.

Thanks in advance.

---

### Post by Thyme on 2007-11-03
Hi foolios,

You can check out the following links I've just picked out from Google:

1) [http://www.linuxcommand.org/]("http://www.linuxcommand.org/")
2) [http://www.unixguide.net/linux/linuxshortcuts.shtml]("http://www.unixguide.net/linux/linuxshortcuts.shtml")

Hope this helps and have fun :)

---

### Post by scorp123 on 2007-11-03
What packages? For what? And from where? Chances are that the software in question is already available via Ubuntu's online software repositories, e.g. you should be able to install anything you want via beginner-friendly tools such as "Synaptic". There are over 20'000 packages available there.

 Even if certain apps are not (yet) available, there are places such as "getdeb.net" which offer pre-packaged software for download. You download the *.deb package in question, you click on it and tell it to install, voila done.

Installing packages from other sources (e.g. tar.gz files, compile things from source, etc.) is not something you should do as a beginner ... If you still insist: Chances are that the web page you downloaded this stuff from has a section which explains how to install their package.

---

### Post by Zorael on 2007-11-03
Google is your friend. :>

I don't know how much they say about root and superusers, but they do cover the terminal. The latter one is more of a command guide.

[http://linux.org.mt/article/terminal](http://linux.org.mt/article/terminal)
[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)


edit-- As for "you probably don't need to know that stuff" - there's nothing wrong in wanting to know. Gogo OP, learn your way to the top!

---

### Post by aysiu on 2007-11-03
> **scorp123 said:**
> What packages? For what? And from where? Chances are that the software in question is already available via Ubuntu's online software repositories, e.g. you should be able to install anything you want via beginner-friendly tools such as "Synaptic". There are over 20'000 packages available there. I agree with scorp123.

For most software needs, you do not need to know some command to install the application. It can all be done point-and-click.

Name the software you're trying to install.

---

### Post by foolios on 2007-11-09
Thanks for the help guys.
Well, for one, I can't get Flash installed in firefox because the directions ask me to change to the directory where I extracted the files that were downloaded. I don't know how to change directories in the terminal. 
I am going to look at the links provided and see if I can figure it out.

Thanks so much.

---

### Post by Maestro23 on 2007-11-09
> **foolios said:**
> Thanks for the help guys.
Well, for one, I can't get Flash installed in firefox because the directions ask me to change to the directory where I extracted the files that were downloaded. I don't know how to change directories in the terminal. 
I am going to look at the links provided and see if I can figure it out.

Thanks so much.

Flash plugin is in the Repositories.

> sudo apt-get install flashplugin-nonfree

Intro to Terminal: [https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=HowToUseTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal?action=show&redirect=HowToUseTheTerminal)

Good luck man.

---

### Post by aysiu on 2007-11-09
> **foolios said:**
> 
Well, for one, I can't get Flash installed in firefox because the directions ask me to change to the directory where I extracted the files that were downloaded. Try these directions instead, then:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by foolios on 2007-11-09
Ok, this is what's happening now that I've learned some commands. I found out how to change directory. =)
And Casing matters, capital letters and lower case letters make a difference. ;o

foo@foo-desktop:~/Documents$ ./flashplayer-installer
bash: ./flashplayer-installer: No such file or directory

According to these directions:
.tar.gz installation

   1. Click the "Download .tar.gz" link. A dialog box will appear asking you where to save the file.
   2. Save the .tar.gz file to your desktop and wait for the file to download completely.
   3. Unpackage the file. A directory called install_flash_player_9_linux will be created.
   4. In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).
   5. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

at the page:
[http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/index.cgi?P1_Prod_Version=ShockwaveFlash)

---

### Post by foolios on 2007-11-09
Oops, you guys replied while I was replying.

Ok, lemme read your posts and I'll post back with progress, thanks all.

---

### Post by foolios on 2007-11-09
Download done.
Flash Plugin installed.


This community rocks. You're the best. Thank you so much!

---

### Post by Maestro23 on 2007-11-09
> **foolios said:**
> Download done.
Flash Plugin installed.


This community rocks. You're the best. Thank you so much!

Good deal man.:guitar:

---

