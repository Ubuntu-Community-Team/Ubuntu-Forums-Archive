---
title: "Flash equivalent plugin for Firefox and/or Palemoon?"
date: 2017-06-23
forum: General Help
---

### Post by Jorhel on 2017-06-23
Hi,
I did a clean install of xubuntu 16.04 LTS, at the begining firefox wasn't working anymore because of my processor not being supported (AMD Athlon XP) so I followed advice elsewhere on the forum and installed Palemoon.[https://ubuntuforums.org/showthread.php?t=2359242&page=2](https://ubuntuforums.org/showthread.php?t=2359242&page=2)
Palemoon actually works fine but I haven't suceeded in installing it properly and making it my browser by default I run it from the exec file (Plonked a shortcut on my desktop).
Nevertheless when trying to run sites like Friv.com or Scratch.mit.edu the message come that I need a plug in.
On my previous install in 14.04 I had the same problem in firefox and was solved with SenjiSensei help installing pipelight. [https://ubuntuforums.org/showthread.php?t=2315476](https://ubuntuforums.org/showthread.php?t=2315476)
So I tryed the same code again but no plug in appeared in Palemoon. wich seems logical because palemoon is not mozilla if I understand well.
I the main time Firefox suddendly started working again, so I tried again the pipelight but the add on does not appear there either.


I tried installing flashplugin-installer via the repositories. It did install the plug in, I could see it in usr/lib/Mozilla/plugins but firefox started crashing on start up again. (And worked again as soon as I removed the offensive plugin) cf [https://ubuntuforums.org/showthread.php?t=2349018](https://ubuntuforums.org/showthread.php?t=2349018)


So to make a long story short, which plugin do I need and where do I find it? and if it could work for Palemoon too would be great!!

---

### Post by monkeybrain20122 on 2017-06-24
Pipelight has discontinued.See [http://pipelight.net](http://pipelight.net)


You can use Chrome which comes bundled with its own flash.

Palemoon is a Firefox fork, it should work with most firefox plugins, so I think it is just a matter of linking and path problems when you have a local version of palemoon.  There should be a .palemoon folder or something like that in your $HOME ( or in $HOME/.config) to store its configurations and settings You can create in it a folder called plugins if not exists already. If you install flash from system, you will find something called libflash.so for similar, copy it and put it in ~/.palemoon/plugins and it should work. You may need to run a chown on libflash.so first. I have never tried it, just a guess.


P.S 

In your previous thread someone said Firefox has stopped supporting flash on Linux. It is completely false. All Mozilla did was to set flash to "ask to activate" and that was for all platforms.

Not sure why pipelight would have made a difference if it is hardware related. Anyway, to help with diagnostic, install flash from repo (adobe-flashplugin) and start firefox from the terminal (open a terminal and type firefox) then visit a flash site, when it crashes copy the error message from the terminal and post it here,


On the other hand if you need flash for DRM content, there is a more complicated [workaround]("https://ubuntuforums.org/showthread.php?t=2363550") even though pipelight is  no more.

---

### Post by Jorhel on 2017-06-26
Thanks,
Chrome unfortunately does not support 32 bit computers unless that has changed recently. 
Palemoon is at the moment sitting in /home/<my user> I have been trying to move it to /opt but without success I think I don't use the mv command properly.
I have created a plugin folder in Palemoon and copied the "libflashplayer.so" file in it (from /flash_player_npapi_linux.i386 folder sitting in my download folder at the moment.)
but it does not make any difference.
Regarding Firefox it just crash on start up if the flash plugin is activated. I have removed pipelight now.

---

### Post by monkeybrain20122 on 2017-06-27
Hi, I tested with the palemoon tarball (just untarred in /home/monkeybrain, no installation) and flash works out of the box without me doing anything.

It seems that it is using Firefox's plugins folders somehow if Firefox is already installed.  I use a peculiar drm capable version of flash in Firefox (ver 25.0 from ChromeOS image [https://ubuntuforums.org/showthread.php?t=2363550](https://ubuntuforums.org/showthread.php?t=2363550)) and palemoon picks that up instead of system's flash (ver 26), so now palemoon can play drmed stream as well even though neither adobe-flashplugin from repon nor pepper flash from Chrome on Linux can play such streams!  Meanwhile I can't find any plugins folder in palemoon's config directory (.moonchild productions)

I don't have a 32 bit installation to test so it is a 64 bit tarball. But I think 32 bit should work similarly too. So install flash and install Firefox then just start palemoon by clicking "palemoon" (instead of "palemoon.bin") and visit a flash site to see if it works.

---

### Post by Jorhel on 2017-06-27
Hi again,
Sorry my level of linux langage is not enough to make sense of the link you're referring to. Should I try to reinstall palemoon? I always came with an error message when I tried to untar it via the terminal and ended up using the archive manager. Would that make a difference?
Very willing to learn more but not trained in IT, just what I picked up trying to make my PC work...

---

### Post by monkeybrain20122 on 2017-06-27
OK according to this [https://linux.palemoon.org/help/faq/#flash](https://linux.palemoon.org/help/faq/#flash) 
> Pale Moon reads the standard Firefox directories for global extensions, thus extensions may be globally installed

So if you install flash from the repo, palemoon should automatically pick it up. You don't need to install palemoon, the tarball is fine (not sure what error message, but it doesn't matter as long as you can open it, you probably get an error because you are in the wrong directory and it tells you no such file)

So it should work out of the box. The reason that it may not work is that system flash is not installed in /usr/lib/mozilla/plugins, in my system it is  in /usr/lib/adobe-flashplugin/, so you need to make a symbolic link to /usr/lib/mozilla/plugins for palemoon to find it.

In my case the command would be
 
```
sudo ln -s /usr/lib/adobe-flashplugin/libflashplayer.so  /usr/lib/mozilla/plugins/libflashplayer.so
```

It works out of the box for me because apparently a symlink was already created at some point, possibly due to me fooling around with different versions of flash before.

So check if /usr/lib/mozilla/plugins/libflashplayer.so  already exists. If no, find out where it is. You can either check synaptic (find flash package you installed, then right click, check properties > installed files) or in the terminal
```

sudo updatedb

locate libflashplayer.so
```

Once you have located libflashplayer.so, make a symbolic link to /usr/lib/mozilla/plugins as above and restart palemoon.

---

### Post by Jorhel on 2017-06-28
OK I tried 
First I moved the  palemoon  and flash_player_npapi_linux.i386 in usr/lib.
then I created the sym link > snukies@LN-PN067AA-ABE-SR1259ES-ES441:~$ sudo ln -s /usr/lib/flash_player_npapi_linux.i386/libflashplayer.so /usr/lib/firefox/browser/plugins 

I do not have a mozilla folder but there is a firefox one and a firefox add-on file, they both have a plugin folder and the
 > libflashplayer.so
is now in it.
As a result palemoon still tell me that I need a plug in and firefox crash on start up. Also I thought that moving palemoon in the usr/lib will make it appear in the list of program but it still doesn't.

---

### Post by Jorhel on 2017-06-28
and in palemoon there is also an executable file called palemoon plugin-container

---

### Post by monkeybrain20122 on 2017-06-28
> **Jorhel said:**
> OK I tried 
First I moved the  palemoon  and flash_player_npapi_linux.i386 in usr/lib.
then I created the sym link  

I do not have a mozilla folder but there is a firefox one and a firefox add-on file, they both have a plugin folder and the
 
is now in it.
As a result palemoon still tell me that I need a plug in and firefox crash on start up. Also I thought that moving palemoon in the usr/lib will make it appear in the list of program but it still doesn't.


Can you create a mozilla folder? It appears that you don't really need firefox to be installed at all, palemoon only needs to find flash in where it thinks is firefox's plugin folder, the path is probably hard coded in palemoon.

```
sudo mkdir /usr/lib/mozilla
sudo ln -s  /path/to/whereever_libflashplayer.so_is_installed  /usr/lib/mozilla/libflasplayer.so
```

---

### Post by gsahli on 2017-06-28
> **Jorhel said:**
> then I created the sym link  
snukies@LN-PN067AA-ABE-SR1259ES-ES441:~$ sudo ln -s /usr/lib/flash_player_npapi_linux.i386/libflashplayer.so /usr/lib/firefox/browser/plugins


I just want to point out that you created a symlink named "plugins," not libflashplayer.so
Is that what you want?

---

### Post by deadflowr on 2017-06-28
Can the cpu run sse2?
```
grep sse2 /proc/cpuinfo
```
if it runs an empty response, then you cannot run current version of flash.
Not sure what workarounds there are, if any.

---

### Post by monkeybrain20122 on 2017-06-28
> **deadflowr said:**
> Can the cpu run sse2?
```
grep sse2 /proc/cpuinfo
```
if it runs an empty response, then you cannot run current version of flash.
Not sure what workarounds there are, if any.


Yeah that possibility somehow escaped me. In that case OP can either use an older version of flash from Linux Mint's archive at his own risk (and wouldn't work for some sites)[https://community.linuxmint.com/tutorial/view/1491](https://community.linuxmint.com/tutorial/view/1491)

Or. since Windows' version of flash works, run Firefox in wine.

---

### Post by Jorhel on 2017-06-28
I suspect its a typo when I copied the code on the forum because libflashplayer.so appear as a symlink in the folder plugins.

---

### Post by Jorhel on 2017-06-28
> **gsahli said:**
> I just want to point out that you created a symlink named "plugins," not libflashplayer.so
Is that what you want?

That's just a typo libflashplayer link is in the plugin folder.

> **deadflowr said:**
> Can the cpu run sse2? 

No it can't I thought I had mentioned it. that's the reason I moved to Palemoon.
I'll try the old version from mint and see how it goes.

Also any idea why palemoon does not appear in my list of programs, I guess it is not installed where it should? Would be neater to be able to run it from the web browser link instead of a shortcut to the exec file on the desktop.

---

### Post by monkeybrain20122 on 2017-06-28
> **Jorhel said:**
> 
Also any idea why palemoon does not appear in my list of programs, I guess it is not installed where it should? Would be neater to be able to run it from the web browser link instead of a shortcut to the exec file on the desktop.

That is because you downloaded a version of palemoon that doesn't need installation (the bzipped file) To install it you need to download the palemoon for Linux installer or the Debian/Ubuntu package or install from the Debian/Ubuntu repository instead.[https://linux.palemoon.org](https://linux.palemoon.org)

---

### Post by Jorhel on 2017-07-02
Thanks for your help.
I installed the older version of flash and it works, with a warning that I should not use it and use a more recent version. but well its that or nothing so will have to do.

---

