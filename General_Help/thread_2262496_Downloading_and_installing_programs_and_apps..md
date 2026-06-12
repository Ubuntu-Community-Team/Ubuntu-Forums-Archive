---
title: "Downloading and installing programs and apps."
date: 2015-01-25
forum: General Help
---

### Post by Morten_Fjellheim on 2015-01-25
I have a problem that seems to be incovered in the guides. There is some programs and apps i need to downlaod and install. The guiudes i have read explains that this should be done in the software center. Its just one thing, the softwarecenter doesnt have the apps or proggrams i need to install.  So i am back to finding things on the web and install it from there. This is very easy  in windows, most rpograms starts by itselfs and if it doesnt you just need to find the install file which is pretty easy to find.

I ubuntu however you just download alot of files that doesnt have an obvious way to install. Amongst the 20-30 diferent downlaods i have dowloaded, only 2-3 of them has been installed. Do anyone know how to, or is there a guide covering this subject?

I know one posible way described in the guide i have used, its about adding additional sources to the software center. Can a website be added as a source, and if so how do i do it? It is explained but i don not understand all of it. It says i have to add the apt line, i am guessing that is the addres to the web site but i am not sure.

This is the guide i am using.

[https://help.ubuntu.com/stable/ubuntu-help/index.html](https://help.ubuntu.com/stable/ubuntu-help/index.html)

---

### Post by flaymond on 2015-01-25
You can try Wine to install 'some' Windows software. Linux is not Windows, don't expect that Linux will run every Windows software. You can read more about Wine at the terminal. Just type -

```
man wine
```

* make sure you installed wine first

When you use Linux, you need to learn. The developers try to make Linux more user-friendly as posibble to the user, but yeah, it's still require your time to learn..it's free, and very good for a particular reasons.

You can read more here - 

[https://help.ubuntu.com/community/CommunityHelpWiki](https://help.ubuntu.com/community/CommunityHelpWiki) (User Documentation)
[http://linux-training.be/files/books/LinuxFun.pdf](http://linux-training.be/files/books/LinuxFun.pdf)     -  Linux Fundamentals (I prefer here to learn some basic bash shell commands)
[https://en.wikipedia.org/wiki/Linux](https://en.wikipedia.org/wiki/Linux)           -   Linux Wikipedia (To know more about Linux)
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware) - How to install software


I just prefer you too Google it first, because there are lot of sources out there can help you..and I bet there are already solutions available for your question 


* If you don't like Ubuntu, try Xubuntu and Lubuntu or another DE

or

try any distro your like. Just find that suits you. 

Thanks

---

### Post by bapoumba on 2015-01-25
Well, it really depends on the application.
Some are available as .deb, you can install them with gedebi (available in the software center), some are already packaged for ubuntu but available from third party ppa (please install ppa-purge first to easily revert to the distribution packages or dependencies), or use dpkg from the command line.
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by Morten_Fjellheim on 2015-01-25
> **InterProg said:**
> You can try Wine to install 'some' Windows software. Linux is not Windows, don't expect that Linux will run every Windows software. You can read more about Wine at the terminal. Just type -

```
man wine
```

* make sure you installed wine first

When you use Linux, you need to learn. The developers try to make Linux more user-friendly as posibble to the user, but yeah, it's still require your time to learn..it's free, and very good for a particular reasons.

I do not wana sound ungrateful, i might find it useful something else another time. Its not what i was asking for though, but ty anyway:

The programs i am talking about is compatible with linux, teamspeak is one of them. There is no autoinstall and it doesnt show any obvious means of how to install.

---

### Post by Morten_Fjellheim on 2015-01-25
> **bapoumba said:**
> Well, it really depends on the application.
Some are available as .deb, you can install them with gdebi (available in the software center), some are already packaged for ubuntu but available from third party ppa (please install ppa-purge first to easily revert to the distribution packages or dependencies), or use dpkg from the command line.
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

Thank you, i will read the guide and see if it helps. I will set this thread as solved for now, i will set it unsolved later if it doesnt help.

---

### Post by Andrew_Lucas on 2015-01-25
I take it you've recently come across from Windows?

I remember when I first came across, the whole getting programs installed thing through me a bit. As a previous poster has said, Linux is most definitely not Windows, so you shouldn't expect all programs to work. Also, my experience of using Wine has never been good...Idk how common that is.

I'd advocate cutting ties as much as possible. Often, Linux has counterparts which actually surpass Windows software. I had to go back to using Windows for a while, and found myself installing Linux programs rather than the more popular 'built for Windows' ones because they just work BETTER and are more pleasurable to use. For instance, I went from using UTorrent to using first Deluge and then Transmission on Windows. Similarly, for multimedia, VLC and Audacious, and Gpodder for podcasts.

Also, don't be scared of the command line. Personally, I hate the software centre. I'm no Linux guru, and feel more comfortable using a GUI if it's available, but for installing software, the terminal is just so much easier. The program which manages installation of software (which comes in 'packages', hence, it's called a 'package manager') is apt. The syntax for using it is as follows:

permission level + apt tool +what you want it to do + package name

Permission level is set using 'sudo' (Super User DO - super user = administrator on Windows).
Apt tool: there are several components of the apt which have different functions. apt-get is the one you use for installing software.
What you want it to do: examples are 'install', 'remove', 'purge' (purge is remove and destruction of any configuration files that program has created)
Package name: you can find this by searching the online Ubuntu repository (google Ubuntu package search), or by finding the package name you want with one of those other apt tools I mentioned (the command would be 'apt-cache search XXXX' where XXX is the search term).

You need to have root (i.e. admin rights) to install software, so if you wanted to install Transmission for example, it would be:

```
sudo apt-get install transmission
```

You can put multiple package names one after the other (which makes install lots of software really easy). To install Transmission and then VLC too:

```
 sudo apt-get install transmission vlc 
```

Easy!

---

### Post by bapoumba on 2015-01-25
> **Morten_Fjellheim said:**
> teamspeak

May be here ?
[http://www.sysads.co.uk/2014/06/install-teamspeak-3-in-ubuntu-14-04/](http://www.sysads.co.uk/2014/06/install-teamspeak-3-in-ubuntu-14-04/)

---

### Post by flaymond on 2015-01-25
Firstly, add what type of software you want to install at the title and the description before you ask next time, so we can help you much further. ;)

---

### Post by Morten_Fjellheim on 2015-01-25
> **Andrew_Lucas said:**
> I take it you've recently come across from Windows?

I remember when I first came across, the whole getting programs installed thing through me a bit. As a previous poster has said, Linux is most definitely not Windows, so you shouldn't expect all programs to work. Also, my experience of using Wine has never been good...Idk how common that is.

I'd advocate cutting ties as much as possible. Often, Linux has counterparts which actually surpass Windows software. I had to go back to using Windows for a while, and found myself installing Linux programs rather than the more popular 'built for Windows' ones because they just work BETTER and are more pleasurable to use. For instance, I went from using UTorrent to using first Deluge and then Transmission on Windows. Similarly, for multimedia, VLC and Audacious, and Gpodder for podcasts.

Also, don't be scared of the command line. Personally, I hate the software centre. I'm no Linux guru, and feel more comfortable using a GUI if it's available, but for installing software, the terminal is just so much easier. The program which manages installation of software (which comes in 'packages', hence, it's called a 'package manager') is apt. The syntax for using it is as follows:

permission level + apt tool +what you want it to do + package name

Permission level is set using 'sudo' (Super User DO - super user = administrator on Windows).
Apt tool: there are several components of the apt which have different functions. apt-get is the one you use for installing software.
What you want it to do: examples are 'install', 'remove', 'purge' (purge is remove and destruction of any configuration files that program has created)
Package name: you can find this by searching the online Ubuntu repository (google Ubuntu package search), or by finding the package name you want with one of those other apt tools I mentioned (the command would be 'apt-cache search XXXX' where XXX is the search term).

You need to have root (i.e. admin rights) to install software, so if you wanted to install Transmission for example, it would be:

```
sudo apt-get install transmission
```

You can put multiple package names one after the other (which makes install lots of software really easy). To install Transmission and then VLC too:

```
 sudo apt-get install transmission vlc 
```

Easy!


Thanks. I am not afraid of the command line or anything else, its just that when i ask a question here on the forum, the answers i get opens up two new question.  For instance when i am told to use a spesific program. I open the program and i get ten new questions at once, about how to use that program. So it is abit frustrating. I might go back to using windows for abit, and dual boot which i wanted to in the first place. I had problems installing for dual booting however and chose a complete ubuntu installation and removal of windows to see if it worked which it did.

I do know that the files i am trying to get installed is linux compatible cause they were made for lotro. On eis teamspeak for linux, pylotro launcher that replaces the windows launcher for lotro and i few more that i am not working on ATM.

---

### Post by yancek on 2015-01-25
Have you seen the instructions at the link below or similar?  Skip the wget... in the instructions if you already have it downloaded.

[http://www.sysads.co.uk/2014/06/install-teamspeak-3-in-ubuntu-14-04/](http://www.sysads.co.uk/2014/06/install-teamspeak-3-in-ubuntu-14-04/)

---

### Post by Morten_Fjellheim on 2015-01-25
> **yancek said:**
> Have you seen the instructions at the link below or similar?  Skip the wget... in the instructions if you already have it downloaded.

[http://www.sysads.co.uk/2014/06/install-teamspeak-3-in-ubuntu-14-04/](http://www.sysads.co.uk/2014/06/install-teamspeak-3-in-ubuntu-14-04/)


I tried earlier but now i found out how to accept or not accept the terms. I have TS up and running now thank you very much, both you and the admin who liked it earlier. Now i need to get lord of the rings online up and running. So if anyone can provide information i would be in their debts:)

---

### Post by bapoumba on 2015-01-25
> **Morten_Fjellheim said:**
> I tried earlier but now i found out how to accept or not accept the terms. I have TS up and running now thank you very much, both you and the admin who liked it earlier. Now i need to get lord of the rings online up and running. So if anyone can provide information i would be in their debts:)
Welcome :)
You may want to have a look at the Gaming and Leisure forum. If you do not find your answers there, please post a new thread.
[http://ubuntuforums.org/forumdisplay.php?f=93](http://ubuntuforums.org/forumdisplay.php?f=93)

---

### Post by Morten_Fjellheim on 2015-01-25
> **bapoumba said:**
> Welcome :)
You may want to have a look at the Gaming and Leisure forum. If you do not find your answers there, please post a new thread.
[http://ubuntuforums.org/forumdisplay.php?f=93](http://ubuntuforums.org/forumdisplay.php?f=93)


I already have a thread there that i marked as resolved. I will ark it unresolved after i have marked this one resolved.

---

### Post by Morten_Fjellheim on 2015-01-31
Alright, i am opening this post again to ask for more advice on the subject. I have been reading this guide "https://help.ubuntu.com/community/InstallingSoftware". I talks about package installers, i have been using sybaptic and i am starting to get used to it. I have a few questions that the guide doesnt answer.
To install a package i need to download one or choose one from the list. I have downloaded something i thought was one of these "packages". A version of python from this website  "https://launchpad.net/ubuntu/+source/python-qt4". I downloaded it and extracted it to the desktop. I can not find it in synaptic though! 
I know i am not including detailed information but its the best i can do. I have been trying to open the desktop folder in synaptic but it is empty. 

Anyway, several questions is roaming my mind. Is the package i have downloaded uncompatible with synaptic, should i be using another one or isnt the file a package at all? Or is there another reason?

---

### Post by ian-weisser on 2015-02-01
You downloaded a SOURCE package from Launchpad. Those won't work.

Source packages are the ingredients. They need to be cooked. Deb packages are the finished meal.
Python-qt4 deb packages are available in Software Center for all supported releases of Ubuntu.

---

### Post by Morten_Fjellheim on 2015-02-01
> **ian-weisser said:**
> You downloaded a SOURCE package from Launchpad. Those won't work.

Source packages are the ingredients. They need to be cooked. Deb packages are the finished meal.
Python-qt4 deb packages are available in Software Center for all supported releases of Ubuntu.

Thank you. Just the kind of information i was looking for:) I have another question though. If i need a package that isnt in the downloadcenter por cannot be added with any ubuntu package installers, how can i make sure a download is a deb package?

---

### Post by ian-weisser on 2015-02-01
> **Morten_Fjellheim said:**
> If i need a package that isnt in the downloadcenter por cannot be added with any ubuntu package installers, how can i make sure a download is a deb package?

That's a bit moving from a great swimming pool to the open ocean. Suddenly you must care about temperature, currents, sharks, next landfall. It's more than just salt water.

The short answer to your question is that a deb package has a .deb suffix. It's an ar-compatible archive. The 'dpkg' application recognizes it.

I *strongly* advise you to drop the habit of wandering the internet looking for software. 
That is a very fast, easy way to thoroughly break your system.
Ubuntu is not Windows. Many long-developed Windows habits (like downloading software from the web) are counterproductive in Ubuntu.
For most new migrants from Windows or OSX, the Software Center really does have all they need.

If you need an application that isn't in the Software Center, ask here. We know a lot of alternatives.

---

