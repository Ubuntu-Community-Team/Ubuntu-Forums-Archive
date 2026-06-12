---
title: "Flash not working on Opera..."
date: 2008-01-05
forum: General Help
---

### Post by Moonfrost on 2008-01-05
Ok, I have the flash plugin installed and both Firefox and Epiphany recognize it without any problems at all...but Opera doesn't, I heard you had to manually copy the libflash.so (or something like that) to the plugins folder in Opera for it to work with flash...I tried that and flash still doesn't work on Opera, in the pages where there's supposed to be flash everything appears black...so I heard by going into preferences, content, plug-in options that I could make Opera find new plugins...the problem is that Opera doesn't find anything! I checked again to see if the files were there and they're all there! does anybody know what's the problem? because I want to use Opera more often because Firefox is crashing on me at least 10 times a day!

---

### Post by oldb0y on 2008-01-05
Try using the .deb-file at the bottom of the first post in [this](http://ubuntuforums.org/showthread.php?t=636397) thread, it worked for me.

---

### Post by Madvil on 2008-01-05
Tried because I have the same problem as the OP and all I managed to do is see a gray box wherever a content should be displayed...

Any more help? :(

---

### Post by oldb0y on 2008-01-05
Did you follow the thread in my first post?

---

### Post by -grubby on 2008-01-05
look [here]("http://www.mediafire.com/?3tlmzxeofzu")

---

### Post by Moonfrost on 2008-01-06
> **oldb0y said:**
> Try using the .deb-file at the bottom of the first post in [this](http://ubuntuforums.org/showthread.php?t=636397) thread, it worked for me.

I can't install that because it's an older version and even if I wanted to install it Ubuntu won't let me...

---

### Post by Elegorod on 2008-01-06
Try to download flash plugin from [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz) , unpack the archive and copy libflashplayer.so to /usr/lib/opera/plugins/ 
To copy a file, open file manager as root (for example, with command sudo nautilus )
Then restart Opera and check if plugins are enabled (press F12 and menu shows)
It worked for me. Do you use Opera 9 or older?

---

### Post by Comhra on 2008-01-06
You may have to use the 9.50 Beta version of Opera to get it to work.

---

### Post by Moonfrost on 2008-01-06
> **Elegorod said:**
> Try to download flash plugin from [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz) , unpack the archive and copy libflashplayer.so to /usr/lib/opera/plugins/ 
To copy a file, open file manager as root (for example, with command sudo nautilus )
Then restart Opera and check if plugins are enabled (press F12 and menu shows)
It worked for me. Do you use Opera 9 or older?

Yeah, I'm using Opera 9.25, there was an update yesterday so I have the latest version...

EDIT: Well, I already had that file on Opera from before because I had copied it there and flash still wouldn't work (even though it's enabled), I also replaced it with the one from the tarball you linked to and still the same. Flash is enabled on Opera but it still won't work, it just displays a black box where there's supposed to be the flash playing...

---

### Post by vahnx on 2008-01-11
I'm having the exact same problem. Any fixes yet? Opera 9.25 downloaded from their website, Ubuntu 7.10, same libflashplayer.so file. I see a grey box and in the status bar it says 'click to activate control' or whatever, and I click it and it does nothing. Edit: Updated to 9.5 beta and it fixed itself.

---

### Post by sekinto on 2008-01-11
Try these things:
-Download the beta version of Opera (9.5, named Kastrel).
-Download the .tar.gz file from the Adobe website, and run the installer.
-When the installer gets to the part where it asks for a destination put /usr/lib/opera (make sure you are running this a root).

---

### Post by Moonfrost on 2008-01-11
> **vahnx said:**
> I'm having the exact same problem. Any fixes yet? Opera 9.25 downloaded from their website, Ubuntu 7.10, same libflashplayer.so file. I see a grey box and in the status bar it says 'click to activate control' or whatever, and I click it and it does nothing. Edit: Updated to 9.5 beta and it fixed itself.

I heard about the 9.5 beta, is it stable? I think I might just download it anyway...today Firefox crashed 15 times...I don't get it, this is LInux not Windows and I never had these problems with the Windows version of Firefox or with other distros that already come with Firefox...

---

### Post by vahnx on 2008-01-12
I am now suggesting Opera to all Linux users. I hate to admit this but Firefox blows on Linux. But I hate Opera on Windows and love Firefox. Weird.

---

### Post by bharadwaj on 2008-01-12
Command line instructions to locate the Flash plug-in if it is installed:

    *>  locate libflashplayer.so, or
    * find / -name libflashplayer.so 2> /dev/null

If Flash plug-in is not installed, or you wish to upgrade, proceed as follows:

   1. Download the plug-in from Adobe's Web site.
   2. Follow the instructions on the download page. The installer will offer to install the plug-in, and for Opera you should choose /usr/lib/opera/plugins/ as the installation path.
   3. Restart Opera.
   4. Verify that the plug-in is working by going to Adobe's test page.

For additional information on Flash Player for Linux, see Adobe's blog.

MIME types:
    application/futuresplash:spl:FutureSplash Player
    application/x-shockwave-flash:swf:Shockwave Flash

---

### Post by Moonfrost on 2008-01-12
> **bharadwaj said:**
> Command line instructions to locate the Flash plug-in if it is installed:

    *

If Flash plug-in is not installed, or you wish to upgrade, proceed as follows:

   1. Download the plug-in from Adobe's Web site.
   2. Follow the instructions on the download page. The installer will offer to install the plug-in, and for Opera you should choose /usr/lib/opera/plugins/ as the installation path.
   3. Restart Opera.
   4. Verify that the plug-in is working by going to Adobe's test page.

For additional information on Flash Player for Linux, see Adobe's blog.

MIME types:
    application/futuresplash:spl:FutureSplash Player
    application/x-shockwave-flash:swf:Shockwave Flash

I tried that and it finds it with no problem, also Opera "does" find it but still does nothing whenever there's flash like for example a youtube video...

---

### Post by bernardfrancois on 2008-01-12
I have the same problem. I just installed gutsy. After installing opera (9.25) and flash, flash didn't work in opera.

I will just wait until opera 9.50 is available in the repositories. Like that, I'll always have the latest opera and flash versions automatically.

Until that time, I'll manage using firefox for flash-enabled webpages.

---

### Post by Sef on 2008-01-12
> I heard about the 9.5 beta, is it stable

I have not had any problems with it nor heard of anyone having problems with it due to instability.   It is very stable.

---

### Post by Moonfrost on 2008-01-12
> **Sef said:**
> I have not had any problems with it nor heard of anyone having problems with it due to instability.   It is very stable.

I'm using it now and flash works perfectly but it "does" show that it's a beta sometimes, it has some issues but 90% of the time it's pretty stable...

---

### Post by miceagol on 2008-01-13
Flash doesn't work here, even after doing the obvious. What is the underlying problem with Opera and Flash? Does anybody have a decent answer to this? Anyway, here's what I did.

Just did a reinstall of Ubuntu, downloaded and installed the latest Opera .deb package (9.25) and installed flash from the repositories (flashplugin-nonfree).  For Firefox, flash now works.

To begin with Opera didn't find any flash player, so I went to Tools > Preferences > Advanced > Content > Plug-in options..., where I clicked "change path..." and added /usr/lib/firefox/plugins. Now I get a grayed box where the flash content is supposed to be (see image).

EDIT: Downloaded and installed [Opera 9.5b]("http://www.opera.com/download/?ver=9.50b") like you guys did, and Flash now works better than ever. :D Before the reinstallation of Ubuntu I had stability issues with flash. It used to somtimes "gray out" unexpectedly while playing.

---

### Post by Moonfrost on 2008-01-13
> **miceagol said:**
> Flash doesn't work here, even after doing the obvious. What is the underlying problem with Opera and Flash? Does anybody have a decent answer to this? Anyway, here's what I did.

Just did a reinstall of Ubuntu, downloaded and installed the latest Opera .deb package (9.25) and installed flash from the repositories (flashplugin-nonfree).  For Firefox, flash now works.

To begin with Opera didn't find any flash player, so I went to Tools > Preferences > Advanced > Content > Plug-in options..., where I clicked "change path..." and added /usr/lib/firefox/plugins. Now I get a grayed box where the flash content is supposed to be (see image).

EDIT: Downloaded and installed [Opera 9.5b]("http://www.opera.com/download/?ver=9.50b") like you guys did, and Flash now works better than ever. :D Before the reinstallation of Ubuntu I had stability issues with flash. It used to somtimes "gray out" unexpectedly while playing.

That "grey out" thing happens to me with every single browser I have (Opera, Firefox and Epiphany) usually on youtube but also on other websites which use flash...I think Adobe are having issues with the LInux versions of flash...

---

### Post by miceagol on 2008-01-13
What did you guys do to get video content to play? The Totem plugin doesn't work. I've read that gecko is needed to play video. What is the easiest way to implement it into Opera?

---

### Post by Moonfrost on 2008-01-13
> **miceagol said:**
> What did you guys do to get video content to play? The Totem plugin doesn't work. I've read that gecko is needed to play video. What is the easiest way to implement it into Opera?

I have the Mplayer plugin which you can find anywhere...mine came with Ubuntu Ultimate 1.6 but you can find it. Do a google search and it usually works perfectly with Firefox and Opera...specially Firefox since it was made primarily for the gecko engine...

---

