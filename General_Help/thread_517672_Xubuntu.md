---
title: "Xubuntu"
date: 2007-08-04
forum: General Help
---

### Post by stewy.23 on 2007-08-04
Hi 
I don't know where to download applications for xubuntu is it possible to download applications for it. I cant get dguitar and mupen64. How do i get them on, also is there another media player i can get for xubuntu that plays wmv. Thanks.

---

### Post by tbroderick on 2007-08-04
[mupen64]("http://ubuntuforums.org/showthread.php?t=464165")

dguitar install [java]("https://help.ubuntu.com/community/Java") and then follow these [directions]("http://dguitar.sourceforge.net/en/inst-run.html").

For a media player, try installing gxine or mplayer. You will also need the w32codecs. I'd use [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") to get the codecs.

---

### Post by wolfen69 on 2007-08-04
use synaptic package manager to download programs. go to- system>administration>software sources make sure all boxes are checked. you may as well add the medibuntu repositories while you're at it. [http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/)  but i dont know offhand if those programs you mentioned are in there.

---

### Post by bettlebrox on 2007-08-04
xmms with the xmms-wma plugin might do what you want.

See the [Ubuntu Guide ]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") for various tips and tricks including how to install programs.

---

### Post by strabes on 2007-08-05
Use VLC for videos.

---

### Post by stewy.23 on 2007-08-05
thanks how do i install flashplayer so i can watch youtube videos. and with mupen64 when i open the script it just goes into notepad.

---

### Post by bettlebrox on 2007-08-05
> **stewy.23 said:**
> thanks how do i install flashplayer so i can watch youtube videos. and with mupen64 when i open the script it just goes into notepad.
See the Ubuntu Guide on how to install the flash player:, 
[(http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)"][http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)]("[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)
Seriously, it's the first place you look if your a newbie.

---

### Post by niceguy123 on 2007-09-20
> **tbroderick said:**
> [mupen64]("http://ubuntuforums.org/showthread.php?t=464165")

dguitar install [java]("https://help.ubuntu.com/community/Java") and then follow these [directions]("http://dguitar.sourceforge.net/en/inst-run.html").

For a media player, try installing gxine or mplayer. You will also need the w32codecs. I'd use [Medibuntu]("https://help.ubuntu.com/community/Medibuntu") to get the codecs.

Just did that after about two hours of trying all kinds of tricks that weren't just right for xubuntu. Now gxine is working just fine. 

- wait - its working fine with .avi and .mpeg but still having a problem with DVD. What should I do now?

---

### Post by HOLOGRAPHICpizza on 2007-09-20
In Xubuntu you can go to Applications > System > Add/Remove Programs.
That is the first place I look for software. I don't know about the DVD though. Try it in VLC, it rocks.

---

### Post by niceguy123 on 2007-09-21
> **HOLOGRAPHICpizza said:**
> In Xubuntu you can go to Applications > System > Add/Remove Programs.
That is the first place I look for software. I don't know about the DVD though. Try it in VLC, it rocks.

I used VLC on Xp and it was great, But I'd rather not load up on multiple programs that do the same thing.  I've got Gxine preinstalled and added codecs needed to run some videos. If I can get it to run all types of media that I need then I don't see any reason to install something else.

---

### Post by mali2297 on 2007-09-21
> **niceguy123 said:**
> Just did that after about two hours of trying all kinds of tricks that weren't just right for xubuntu. Now gxine is working just fine. 

- wait - its working fine with .avi and .mpeg but still having a problem with DVD. What should I do now?

Have you installed the libdvdcss2 package?
```

sudo apt-get install libdvdcss2

```

---

### Post by erfahren on 2007-12-28
so does the entire subforum dedicated to Xubuntu here consist of this one thread? -lol !

-- just kidding, but since trying it out I've noticed that there's not a heck of a lot of documentation specifically for it. (the entire [http://www.xubuntuguide.org/](http://www.xubuntuguide.org/) wiki is non-existent for it).

Anyway, does anyone know if the Medibuntu Gutsy repository works for Xubuntu? I'm mainly just interested in a couple packages right now (googleearth and acroread, maybe realplay) and want to know if they'll work in Xubuntu without problems.

---

### Post by mali2297 on 2007-12-29
> **erfahren said:**
> Anyway, does anyone know if the Medibuntu Gutsy repository works for Xubuntu? I'm mainly just interested in a couple packages right now (googleearth and acroread, maybe realplay) and want to know if they'll work in Xubuntu without problems.

Xubuntu uses the same repositories as Ubuntu, so yes.

Most of the guides that concerns Ubuntu are also valid for Xubuntu, it is just the desktop environment and some of the applications that differ. For example, Xubuntu uses the editor Mousepad instead of Gedit, so an instruction like
```

gksudo gedit

```
is translated to
```

gksudo mousepad

```

---

