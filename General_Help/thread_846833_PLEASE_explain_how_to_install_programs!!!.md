---
title: "PLEASE explain how to install programs!!!"
date: 2008-07-01
forum: General Help
---

### Post by l0fls on 2008-07-01
i searched around and still i haven't found anything that successfully explains how to install programs in linux (just got linux 2 hrs ago)
from my understanding you type into the terminal code or some junk if an advanced linux user could just break this down and explain everything cause i literaly know nothing... so i downloaded ctorrent and extracted it i see these folders and files named install but when i double click it it opens as a text file


btw new to the forms so hi all.

---

### Post by soccerboy on 2008-07-01
most programs you are going to install at the beginning are going to be from the repositories.  they can be installed by typing ```
sudo apt-get install <programname>
``` for example to install mplayer I would type ```
sudo apt-get install mplayer
```  If you download a .deb file, you can just double click it to install it.  Stuff gets complicated and less uniform when you start to download source packages.

---

### Post by l0fls on 2008-07-01
what exacly is a repositorie?
also how do i know what programs i can install using > sudo apt-get install <programname>
 because i did sudo apt-get install ctorrent and it did some stuff i couldent really tell you what happend but there was lines of code in the terminal and i belive it installed i checked threw my applicantions tab on the top left  but couldent find it any tips?

---

### Post by steveneddy on 2008-07-01
Try looking at this link

[http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_packages_.28programs.29_and_libraries](http://ubuntuguide.org/wiki/Ubuntu:Hardy#Installing_packages_.28programs.29_and_libraries)

The repositories are a group of applications (programs) that have been approved and tweaked and ready to run on Ubuntu.

To look at the list of Ubuntu repositories, open up the Synaptic Package Manager:

System --> Administration --> Synaptic Package Manager

You can just browse throught the many titles, search by keyword or by category.

This is an easy way to DL stuff you want/need. Most of what you want/need are already here.

There are tons of torrent application in the repos (repositories), just search for torrent.

If you look in 

Applications --> Internet --> Transmission BitTorrent Client

you will see that there is already one installed for you, ready to go.

Remember, this is not Windows and you will have to learn to do some things differently, including installing applications (programs).

---

### Post by Doji on 2008-07-01
Hi, and welcome to the forums.

It isn't necessary to install programs by using the terminal, but many of us like to do it because it's often faster and makes it easier to give instructions.

The easiest way to install a program is to go to Applications > Add/Remove. Unlike in Windows, Add/Remove actually DOES add programs :lolflag:. Just search for what you want, check it, and hit apply. It should handle everything else for you.

Since not everything is available through Add/Remove there are a number of other ways to install programs. [This guide]("http://monkeyblog.org/ubuntu/installing/") covers most, if not all, of them. It's not necessary to learn all of them right now (there are some there I haven't even ever used), but rather keep it for reference. However, I recommend familiarizing yourself with Synaptic, at least.

And in case you're not aware, a torrent should already be available in Applications > Internet.

---

### Post by WeEatVista on 2008-07-01
For most things you would want to install in Ubuntu, simply go to Applications --> Add/Remove Applications. Make sure the **Show:** (near the top of the add/remove programs) displays All Available Applications, not anything else. Then search the add/remove programs for anything you want, from different games to programming software. 

> also how do i know what programs i can install using

```
sudo apt-get install <programname> 
```

doing this in terminal installs the application via the terminal, and showing the lines and codes is what should happen. This is another way to install applications found in Add/Remove Applications.

If something you want is not in add/remove programs, you may have to download it from a site. .deb are programs in an easy to install format, but other formats may not be as easy, such as .tar.gz and .tar.gz2. Those files are compressed files, just like .rar and .zip files in windows. You have to extract those and view the README for how to install.

Fore more information, check out this site [http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

Welcome to the Ubuntu side of life!

We Eat Vista

---

### Post by l0fls on 2008-07-01
Thanks Doji and Steveneddy the links were handy and i figured out how to use synaptic very helpfulposts
btw in my applications>internet there is softphone,mail,ffox,pidgen, and terminal server client nothing about torrents but its fine i found one using snyaptic
if it makes any diffrence i use ubuntu 7.10 gutsy whats the diffrence?

---

### Post by soccerboy on 2008-07-01
that is why the transmission bittorrent client is not installed.  transmission was included for the first time in 8.04 hardy heron.  Hardy heron is the latest release of ubuntu.  your version should have the older gnome bittorrent client but it is very bad and hardly works.  I don't think it was installed by default.

---

### Post by Rainstride on 2008-07-02
[http://monkeyblog.org/ubuntu/installing/#script](http://monkeyblog.org/ubuntu/installing/#script)

---

