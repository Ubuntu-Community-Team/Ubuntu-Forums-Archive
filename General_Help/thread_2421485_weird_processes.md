---
title: "weird processes"
date: 2019-06-22
forum: General Help
---

### Post by hmiersch on 2019-06-22
i recently noticed that there are 3 processes called tracker-store, tracker-miner-fs and tracker-miner-apps in system monitor. whats up with them? have i been infected with some malware? are they part of the OS? but then why can i kill them with zero consequences? needless to say, after the next restart theyre back :-(

---

### Post by HermanAB on 2019-06-22
The tracker-miner-apps is the useless desktop search function of Gnome.  It was originally invented by KDE and when the developer died, the code got a life of its own and spread to Gnome and even to Windows also. 

As far as I am concerned, it is completely useless, except for keeping your battery flat and your flat warm.  So you can uninstall/disable/nuke it without consequence.

---

### Post by yetimon_64 on 2019-06-22
> **hmiersch said:**
> ... have i been infected with some malware? are they part of the OS? but then why can i kill them with zero consequences? needless to say, after the next restart theyre back :-(

No, you haven't been infected with any malware. They are standard Ubuntu OS processes and are a usual part of any Ubuntu installation.

From [[COLOR=#0000ff]--this link--[/COLOR]]("https://askubuntu.com/questions/346211/tracker-store-and-tracker-miner-fs-eating-up-my-cpu-on-every-startup") on AskUbuntu; what the tracker processes do...
> What does these processes do?[INDENT]   Tracker is a synergy of technologies that are designed to provide a   highly sophisticated, innovative and integrated desktop.
      Tracker provides the following:
      
[LIST]
[*]Indexer for desktop search (for more details see this spec : [https://wiki.ubuntu.com/IntegratedDesktopSearch](https://wiki.ubuntu.com/IntegratedDesktopSearch)) 
[*]Tag database for doing keyword tagging of any object 
[*]Extensible metadata database for apps like gedit and rhythmbox which need to add custom metadata to files 
[*]Database for first class objects allows using tracker's database  for storage and implementation of First Class Objects and the Gnome 3.0   Model. 
[/LIST]
[/INDENT]

The first answer at the link above also gives information on how to stop the processes if needed (Note that link refers to 16.04 so I am not sure if it will work with newer releases).

Some Xenial manpages for them ...
[URL="http://manpages.ubuntu.com/manpages/xenial/man1/tracker-daemon.1.html"][COLOR=#0000ff]-- tracker-daemon --
[/COLOR][/URL][URL="http://manpages.ubuntu.com/manpages/trusty/man1/tracker-miner-fs.1.html"][COLOR=#0000ff]-- tracker-miner-fs --
[/COLOR][/URL]and 
[[COLOR=#0000ff]-- tracker-store --[/COLOR]]("http://manpages.ubuntu.com/manpages/xenial/man1/tracker-store.1.html")

All blue text above contains links to further information that may help you understand what those processes are for in Ubuntu.

Regards, yeti.

---

### Post by HermanAB on 2019-06-22
Yes, the halfwit indexing is part of Gnome and KDE and totally useless to me (and prolly most everybody).  Once in five years when I need to search for a file, I use the find command.  I don't need a badly designed indexing program to run my battery down all the time, in order to save me 2 milliseconds of searching once in five years.  Maybe I may need it more once Altzheimers sets in, but then I probably won't know what to search for either, so then it would still be useless.

---

### Post by TheFu on 2019-06-22
+1 for Herman's answers.
I use **locate** or **find** to find stuff 99% of the time.  Locate defaults to indexing once a day via **updatedb**.  It works on filenames.  find searchs on a file types, sizes, names, access/create/modification times, but it doesn't pre-index anything so it is slower as it traverses the directories at run time.

IF I want desktop search, I use **recoll**, which is a monster, but I control when the re-index runs.  Recoll is like having google for your desktop. Very fast, very thorough, but it deals with word roots, different endings, tense changes, and sound-a-likes. The results are extremely fast.  There's a GUI and CLI versions. 

 There are other desktop search tools like Beagle.  [https://www.linux.com/news/efficient-desktop-searching-beagle](https://www.linux.com/news/efficient-desktop-searching-beagle)

Found this description of tracker:> 
Tracker is a part of GNOME Project and it tries to adhere to various useless technologies, like DBus. Tracker introduces the concept of file tags, thus over complicating the task of file management.
```
sudo apt purge tracker
``` will make it go away.  I need to add that to my list of packages to remove when building a new system.

---

### Post by hmiersch on 2019-06-22
so where do i find those processes? can i just delete them, or is it more complicated?   and are there any more useless apps that i can get rid of?

---

### Post by HermanAB on 2019-06-23
There are lots of more of less useless things in Ubuntu: AppArmor, Cloud-init, Zeroconf networking, Snapd... the list goes on and on and on...

Google is your friend on how to remove these things.  

Otherwise, just give up and install OpenBSD or Slackware to get some speed.

---

### Post by Rubi1200 on 2019-06-23
> **HermanAB said:**
> There are lots of more of less useless things in Ubuntu: AppArmor

I can probably agree about most of the other processes you mentioned but could you please expand on why you consider AppArmor to fall into the category of useless things?

First time I have heard this and would be curious to understand why you think so.

Thanks.

---

### Post by HermanAB on 2019-06-23
Mandatory Access Controls like AppArmor and SELinux arguably have their use as another layer of the security onion on a server, which is exposed to the wild wild web.  On a personal machine, they are of limited utility and bog the machine down, as each and every file access is checked against a list of permissions.

Disabling AppArmor, SELinux or Tomoyo, will noticeably speed a machine up and Theo De Raadt of OpenBSD, as well as Patrick Volkerding of Slackware, both argue that the added complexity is not worth it in the end.  I happen to agree with them.

I tend to leave these energy sapping things running on a new machine, but eventually I need to do a computationally intensive simulation and then I end up hunting around for useless processes to kill and never bother to enable them again.

---

### Post by hmiersch on 2019-06-23
> **HermanAB said:**
> There are lots of more of less useless things in Ubuntu: AppArmor, Cloud-init, Zeroconf networking, Snapd... the list goes on and on and on...   none of those processes are running on my system, so i don't really care about them. but i did get rid of those tracker* things - i hope. the next restart will tell...

---

### Post by HermanAB on 2019-06-23
You sure? You probably do have zeroconf.  Look for avahi and dnsd.  It has never been of any use to me, except to give my machine an annoying 169 IP address when the router is unreachable.  

If you study the processes with ps -e, then you will likely find more fluff that aren't of any use to a single user machine.

---

### Post by again? on 2019-06-23
Be aware that some of the gnome core apps depend on tracker and will be removed as well if you have installed them.
Tracker is part of the GNOME desktop environment.
```
**[COLOR="#006400"]glen@Bionic:~$[/COLOR] apt rdepends tracker**
tracker
Reverse Depends:
  Depends: tracker-extract (>= 1.99.2)
  Depends: gnome-games-app
  Suggests: nautilus
  Depends: vanilla-gnome-desktop
  Depends: tracker-miner-fs (>= 1.99.2)
  Replaces: tracker-extract (<< 1.99.2)
  Breaks: tracker-extract (<< 1.99.2)
  Depends: gnome-documents (>= 1.99)
  Depends: rygel-tracker (>= 0.8)
  Suggests: kylin-burner
  Depends: gnome-photos
  Depends: gnome-music (>= 2.0)
  Depends: gnome-games-app
  Depends: gnome-boxes (>= 2.0)
  Depends: gnome-core
  Suggests: nautilus
  Suggests: brasero
  Depends: bijiben
```

**Note: in Disco 19.04 nautilus now depends on tracker.
```
**[COLOR="#006400"]glen@discotech:~$[/COLOR] sudo apt remove tracker**
[sudo] password for glen: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  gnome-shell-extension-desktop-icons nautilus nautilus-admin nautilus-share
  tracker tracker-extract tracker-miner-fs ubuntu-desktop
  ubuntu-desktop-minimal
0 to upgrade, 0 to newly install, 9 to remove and 0 not to upgrade.
After this operation, 5,127 kB disk space will be freed.
Do you want to continue? [Y/n]
```

---

### Post by hmiersch on 2019-06-26
i just noticed another problem: the files icon that should be at the top of the dock has disappeared. is that because i killed those tracker things? and how do i get it back?

---

### Post by again? on 2019-06-26
The files icon is Nautilus. See my previous post.
If you don't want tracker you will need to install a different file manager in 19.04 or search how to disable tracker.
I use and prefer Nemo.

---

### Post by HermanAB on 2019-06-26
Note that there is a very simple way to disable something without uninstalling it and wrecking other things: Rename the offending program to something else.  I usually do this:
whereis annoyingprogram
mv /path/annoyingprogram /path/annoyingprogram.bad

What then happens is that when the system wants to start the program, it can't find it and life goes on without it.

If you later find something essential is broken, rename it back.

---

