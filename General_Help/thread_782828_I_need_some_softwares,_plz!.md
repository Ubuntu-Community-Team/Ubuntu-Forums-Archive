---
title: "I need some softwares, plz!"
date: 2008-05-05
forum: General Help
---

### Post by favadi on 2008-05-05
Hi everybody!
I've just used Ubuntu but I can't find some softwares that I need  to use.
1. I want a software can display corectly .prc files. I've tried FBreader but it can display some files that contain Unicode Composite characters.
2. I want a software can Sync my BlackBerry 7290 to archive my email and sms. I've searched but I can't find any software.
3. Some thing when I listen music with RhythmBox, the sound is so bad. I think I can have a better sound if I install a orginal Drivers but I don't know the way to install it. I find out my drivers for my main board in this page:
> [http://www.gigabyte.com.tw/Support/Motherboard/Driver_Model.aspx?ProductID=1880](http://www.gigabyte.com.tw/Support/Motherboard/Driver_Model.aspx?ProductID=1880)
I've download it but I can't install it. Somebody help me?
4. I use FireFox 3 beta 5 and I want to display some site that contain many flash, I've install Adobe Flash but it make FireFox "die" unexpectly with some site like [www.dantri.com](www.dantri.com) . I have to use FlashBlock to can read news from this page, but it's very  painful.
Thanks everybody and specially thanks for who can fix that problem for me :D!
P/S: My english is very bad because I don't come form a English Speaking Country, if I got some spelling mistakes, please correct them for me!

---

### Post by favadi on 2008-05-05
Help me, plz :(!

---

### Post by favadi on 2008-05-08
Silent...

---

### Post by p_quarles on 2008-05-08
Blackberry:
[http://ubuntuforums.org/showthread.php?t=190938](http://ubuntuforums.org/showthread.php?t=190938)

For your sound card, you cannot use Windows drivers in Linux. If you describe a bit more what is wrong with the sound, someone may be able to help you.

For Firefox, you may want to disable desktop effects while browsing the web. On some hardware, Flash creates problems for Compiz. This may not help, but it's worth a try. The basic problem is that the Flash player that Adobe released for Linux is a bit of a shoddy product.

---

### Post by favadi on 2008-05-08
Thanks very much, but I've seen that page has a link to download driver for my sound card, and it's a linux driver ,but the problem is the way to install it. 
And at this time, I still can't read my .prc ebooks, FBreader isn't a good software...

---

### Post by jocko on 2008-05-08
If you read the information on the gigabyte download page you can see that the linux driver they offer is **VERY** old and outdated. It was released in 2004 and according to the release notes it only supports kernels up to 2.6.7 (the kernel in Hardy is 2.6.24) and alsa 1.0.5 (1.0.16 is in hardy).
The reason they don't offer any newer driver is simply because **[COLOR=Black]the driver is already included[/COLOR]** in every linux distro released after 2004.

---

### Post by favadi on 2008-05-09
> **jocko said:**
> If you read the information on the gigabyte download page you can see that the linux driver they offer is **VERY** old and outdated. It was released in 2004 and according to the release notes it only supports kernels up to 2.6.7 (the kernel in Hardy is 2.6.24) and alsa 1.0.5 (1.0.16 is in hardy).
The reason they don't offer any newer driver is simply because **[COLOR=Black]the driver is already included[/COLOR]** in every linux distro released after 2004.

Thank you! But I think that listening music in Ubuntu isn't as good as WindowsXp. RhythmBox doesn't support skins and the playlist maker feature is quite bad. In some music sites, I can't play music online, totem doesn't work. I heard that, Mplayer can but when I install Mplayer it doesn't play music in FireFox.
FireFox is very good browser but I prefer Opera. When I install Opera (download from opera.com), if Opera is running, my keyboard can't be use, can't type any character in address bar.
Many problems when I started to use Ubuntu. :(

---

### Post by Tomatz on 2008-05-09
Sound's fine here :confused:

If you want a skinable media player you could try:

**Audacious** (install it from the synaptic package manager *system, administration*)

Banshee (synaptic)

Mplayer (synaptic)

My personal faviroute is **amarok** also just install via synaptic.

Trust me stick with linux, iron out your problems and you wont go back to m$.

;)

As for the sound problem **r-click on the volume applet** in the **systray**, open **volume control** then **file** and **change device** then try playback again and post results.

---

### Post by ryanhaigh on 2008-05-09
> **favadi said:**
> Thank you! But I think that listening music in Ubuntu isn't as good as WindowsXp. RhythmBox doesn't support skins and the playlist maker feature is quite bad. In some music sites, I can't play music online, totem doesn't work. I heard that, Mplayer can but when I install Mplayer it doesn't play music in FireFox.
FireFox is very good browser but I prefer Opera. When I install Opera (download from opera.com), if Opera is running, my keyboard can't be use, can't type any character in address bar.
Many problems when I started to use Ubuntu. :(


At a minimum to get mplayer to play the content on sites you will probably need to install mozilla-mplayer - MPlayer-Plugin for Mozilla, search for it in synaptic/add-remove or click this link [mozilla-mplayer](apt://mozilla-mplayer) < probably won't work with opera. 

That opera problem sounds strange, have you tried disabling desktop effects and then using it. Have you tried using the version that is available in the ubuntu repositories [opera](apt://opera)? You should probably read this:

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by housam on 2008-05-09
for the .prc file reader check [[COLOR="Red"]_this link _[/COLOR]]("http://www.thehaus.net/AltOS/PalmOS/ht-prctoolslinux.shtml")it may help. Also [[COLOR="Red"]_this thread _[/COLOR]]("http://ubuntuforums.org/showthread.php?t=333001")can help.

---

### Post by favadi on 2008-05-09
> **ryanhaigh said:**
> At a minimum to get mplayer to play the content on sites you will probably need to install mozilla-mplayer - MPlayer-Plugin for Mozilla, search for it in synaptic/add-remove or click this link [mozilla-mplayer](apt://mozilla-mplayer) < probably won't work with opera. 

That opera problem sounds strange, have you tried disabling desktop effects and then using it. Have you tried using the version that is available in the ubuntu repositories [opera](apt://opera)? You should probably read this:

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

I've download this version of Opera for Hardy in Opera.com, and I think it's the right version. MPlayer is very good software, it's play almost media files in my computer and skinable. 
> Sound's fine here

If you want a skinable media player you could try:

Audacious (install it from the synaptic package manager system, administration)

Banshee (synaptic)

Mplayer (synaptic)

My personal faviroute is amarok also just install via synaptic.

Trust me stick with linux, iron out your problems and you wont go back to m$.



As for the sound problem r-click on the volume applet in the systray, open volume control then file and change device then try playback again and post results. 
I think the best music player in linux is Amarok, but it's a kde app, when I install it's also install many things  in my computer. 
Okie, the sound is acceptable. A friend told me that have a Winamp version work in linux, but I can't find out it from Winamp.com. Where I can get it? 
Thanks everybody!

---

### Post by Tomatz on 2008-05-09
> **favadi said:**
> I've download this version of Opera for Hardy in Opera.com, and I think it's the right version. MPlayer is very good software, it's play almost media files in my computer and skinable. 

I think the best music player in linux is Amarok, but it's a kde app, when I install it's also install many things  in my computer. 
Okie, the sound is acceptable. A friend told me that have a Winamp version work in linux, but I can't find out it from Winamp.com. Where I can get it? 
Thanks everybody!

Audacious supports winamp skins. But i think the problem is your audio output is dodgy. Try switching it in volume control as i said earlier.

---

### Post by ubuntu-freak on 2008-05-09
Try Exaile instead of Amarok. What was wrong with your sound quality though? If you still have problems with Flash, execute this command:

**sudo apt-get purge flashplugin-nonfree gnash gnash-common mozilla-plugin-gnash swfdec-mozilla && sudo apt-get install flashplugin-nonfree libflashsupport**
 
Then restart Firefox. Take a look at my [sticky](http://ubuntuforums.org/showthread.php?t=766683) also.
 
Nathan

---

### Post by Th3Professor on 2008-05-09
> **favadi said:**
> Thank you! But I think that listening music in Ubuntu isn't as good as WindowsXp. RhythmBox doesn't support skins and the playlist maker feature is quite bad. In some music sites, I can't play music online, totem doesn't work. I heard that, Mplayer can but when I install Mplayer it doesn't play music in FireFox.
FireFox is very good browser but I prefer Opera. When I install Opera (download from opera.com), if Opera is running, my keyboard can't be use, can't type any character in address bar.
Many problems when I started to use Ubuntu. :(

You might consider trying Ubuntu Studio.
Then get into the applications that come with it, explore, experiment, and discover new and cool programs.

Saying music on WinXP is "better" than music on a *nix system is a misnomer. It's not better - it's simply "different" and, even then, only different because of the actual operating system and physical appearance of the program you're using. And physical appearance has no effect on sound.

Regarding specific complaints in your post...

1. There are multimedia applications that allow for skins, try others out.

2. Different apps also provide different approaches toward playlists.

3. Music sites will play music (or video) if you have the proper programs and set-up, most of which is operable by default anyway.

4. If Totem doesn't work, chances are there's something wrong with the settings or how it was installed. Consider uninstalling it and reinstalling from an Ubuntu repo.

5. If you want Firefox multimedia support and don't already (default) have it, then when trying to access music (or similar) online, Firefox prompts you to install the necessary apps to get it to work. Just do what it says.

6. Opera is in an Ubuntu repo. You can install it with "sudo apt-get install opera" and it'll work fine.

7. If you have a problem with the keyboard locking up, and if you're running SCIM then make sure SCIM is set-up correctly (no conflicting key assignments) or simply close the program; alternately, reboot - especially if your mouse is also locked up; though if the problem is only in Opera, then uninstall it and do a fresh install from a repository, this will solve many headaches.

There is a thread, or threads - I'm not sure where - somewhere in the Ubuntu forums that have actual direct comparisons of programs from MS Windows to *nix. You might do a search for that/those thread(s).

Also, to just make everything a lot easier, you might consider Ubuntu Studio.

---

### Post by favadi on 2008-05-14
I've tried Exaile, it's very good music player. But about, reading .prc ebook in Ubuntu, I couldn't find a good solution. Perhaps, I have to wait Mobipocket.com make a version of Mobipocket reader for linux. I've sent them an email but they haven't replied.

---

### Post by Tomatz on 2008-05-14
> **favadi said:**
> I've tried Exaile, it's very good music player. But about, reading .prc ebook in Ubuntu, I couldn't find a good solution. Perhaps, I have to wait Mobipocket.com make a version of Mobipocket reader for linux. I've sent them an email but they haven't replied.

It may run in wine. Wine is kind of like a windows emulator.

You can install it in synaptic.

Then just run the mobipocket installer with wine to install it ;)

---

### Post by Th3Professor on 2008-05-15
> **Tomatz said:**
> It may run in wine. Wine is kind of like a windows emulator.

You can install it in synaptic.

Then just run the mobipocket installer with wine to install it ;)

Actually...

That'd be Wikolawe or Wikolwe.
("Wikolwe is kind of like [a] windows emulator")

Though if it was "Wie is [an] emulator", it'd be Wie... and we'd just ask Why. ;)

Wine is not [an] emulator. ;);) ...but it is... kind of like one.

:)

---

### Post by Tomatz on 2008-05-15
> **Th3Professor said:**
> Actually...

That'd be Wikolawe or Wikolwe.
("Wikolwe is kind of like [a] windows emulator")

Though if it was "Wie is [an] emulator", it'd be Wie... and we'd just ask Why. ;)

Wine is not [an] emulator. ;);) ...but it is... kind of like one.

:)


Actually

The phrase "Wine is not an emulator" is a joke.

Just like "Linux is not unix" (linux)

;)

But i see what you are saying.

---

### Post by Th3Professor on 2008-05-15
> **Tomatz said:**
> Actually

The phrase "Wine is not an emulator" is a joke.

Just like "Linux is not unix" (linux)

;)

But i see what you are saying.

Actually

I was joking. ;) hence putting wine is not an emulator in my post. :)

The "linux is not unix" thing... actually... it's not. ;)

And that it could be referred to as Unix _***is***_ a joke.

Anybody who whole-heartedly believes the Linux really *is* Unix is... well.. wrong.

It could be LINUXL...
linux is not unix-like.

:lolflag:


So, really, Linux is NOT Unix... it's just "kind of like" it.

But... we all already know that.

The point is: It's a joke.

---

### Post by favadi on 2008-05-16
okie. Thanks for your supports but Wine can't run Mobipocket reader.Impossible to reading .prc files!

---

### Post by Tomatz on 2008-05-16
> **favadi said:**
> okie. Thanks for your supports but Wine can't run Mobipocket reader.Impossible to reading .prc files!


You could use a virtual machine. This basically allows you to run xp (or any other os) in a window.

In a terminal:

```
sudo apt-get install virtualbox-ose
```

Then go to *applications, system tools, innotek virtualbox*

Then in the virtualbox main window click add, then setup your virtual machine make sure you set it up to use the drive with your xp install disc in so when you start the VM you can install xp on the VM. Its quite simple and straightforward.

Any probs just post back ;)

---

