---
title: "Flash Player version 9"
date: 2006-07-20
forum: General Help
---

### Post by wizzkid on 2006-07-20
Hi Guys,

Is there a flash player version 9 for kubuntu 6.06? :)

I was trying to view this site [www.linese.com](www.linese.com) is a chinese site with flash. When I view on my firefox 1.5.0.4 with Flash player 7, other part of the flash wont load, specificaly the left menu. The site uses latest flash I think, as I tried to browse the site on my Windows box which the latest Firefox with the latest flash player (9) and it worked well. 

IF you have any suggestions, please let me know.

Thanks.

---

### Post by Malac on 2006-07-20
This will make most sites think you are running version 9 in Ubuntu even if you are not.
Don't forget to copy/backup the file before editing it.

 Open the file ~/.mozilla/firefox/pluginreg.dat
 change 
 Shockwave Flash 7.0 r63:$
 to
 Shockwave Flash 9.0 r63:$

I've just tried it on that site and it seems to work.
Hope this helps.

---

### Post by geco on 2006-07-20
> **wizzkid said:**
> Hi Guys,

Is there a flash player version 9 for kubuntu 6.06? :)

I was trying to view this site [www.linese.com](www.linese.com) is a chinese site with flash. When I view on my firefox 1.5.0.4 with Flash player 7, other part of the flash wont load, specificaly the left menu. The site uses latest flash I think, as I tried to browse the site on my Windows box which the latest Firefox with the latest flash player (9) and it worked well. 

IF you have any suggestions, please let me know.

Thanks.

You can install windows version of firefox using wine and install the latest flash plugins on it...
unfortunately adobe has not released flash 9 for linux...

to instal wine:
```

sudo apt-get install wine

```

I suggest you to download and install WineTools or Sidenet wine configuration utility (I use sidenet), [frank's corner]("http://frankscorner.org/index.php") is a good site to leard something about it

then go to [www.mozilla.com](www.mozilla.com) and download firefox 1.5.0.4 for windows
 now you have to install it with wine
```

wine Firefox\ Setup\ 1.5.0.4.exe

```
follow the instructions and you will have you "winefox" installed



run "winefox" and go to the [adobe flash player]("http://www.adobe.com/products/flashplayer/") site to download flash player 9 plugin (if you can't download it, here is the direct link: [install_flash_player.exe]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player.exe"))

run
```

wine install_flash_player.exe

```

if the installer doesn't recognize your browser you can manually set the installation directory to .wine/dosdevices/c\:/Program\ Files/Mozilla\ Firefox/plugins/


you can also "clone" you "linfox" to your "winefox" copying your local preferences .mozilla/firefox/"SOMETHING".default/* to .wine/dosdevices/c\:/windows/profiles/USERNAME/Application\ Data/Mozilla/Firefox/Profiles/"SOMETHING".default/

you will have all bookmarks, history, themes, extensions installed on your "winefox"... anyway it's better to check out if you have any extension with doesn't work on windows.

I tried it and it works fine

byebye

---

### Post by wizzkid on 2006-07-20
I tried to install windows version of firefox + flash player 9, however, when I tried to open a chinese website, its all in ??????? cant read it, I think there is not plugin in for chinese? how can I install it? i tried the character encoding and still no lack.

Also, It seems that the page is not as good as the default firefox of linux, or windows version in windows box, like now, on the upper conner of this page where the menu is there (Ubuntu,  cummunitu, support etc) theres a black space above those images/menu

I will try the suggestion of malac.


Any suggestion will be highly appreaciated.


Thanks guys, :)

---

### Post by geco on 2006-07-20
I can see it very well, I have been redirected to the english version of site [http://www.linese.com/model/english/pub/index.jsp](http://www.linese.com/model/english/pub/index.jsp) and the main page works fine
did you verify to have installed the right version of flash player?
open the page 
```

about:plugins

```
on firefox and verify that Flash Version says
```

    File name: NPSWF32.dll
    Shockwave Flash 9.0 r16

```

---

### Post by wizzkid on 2006-07-20
On Firefox Windows Version: 

    File name: NPSWF32.dll
    Shockwave Flash 9.0 r16

On Firefox Kubuntu verison:

    File name: libflashplayer.so
    Shockwave Flash 9.0 r63 
- I edited as per malac instruction (see above) but, still no lack. 

I tried visiting at [www.2advanced.com](www.2advanced.com) using firefox linux version, only shows me the splash screen/ intro, and doesnt load the website itself, however, when I tried using the firefox windows version with flash player 9 its load but "no sound"

The firefox windows version is okay with me, however, I had a few problems with it.
1. No Sound
2. The images are somewhat not in the position, or some images are mis-aligned, like in this ubuntuforums, theres a black line (20px hieght) on top menu (ubuntu, community, support etc)
3. Chinese characters doesnt show up..

if these 3 issue has been solve, I think Im okay with this setup.

On Linux version of firefox however, quite okay and been using it for months and just found out that:
1. other flash module doesnt work like in [www.linese.com](www.linese.com)
2. sounds doesnt came up, i think due to flash plugin


Hope you guys could help me here and suggest me which version should I use.

Thanks.

---

### Post by geco on 2006-07-20
for your "winfox" I just suggest you to try to install (with wine) also the ShockWave player [here](http://fpdownload.macromedia.com/get/shockwave/default/english/win95nt/10.1.3.018/Shockwave_Installer_Full.exe)
Maybe it helps you, otherwise I'm sorry but I have no idea of wath to do :(

---

### Post by Uncle Spellbinder on 2006-08-14
> **Malac said:**
> This will make most sites think you are running version 9 in Ubuntu even if you are not.
Don't forget to copy/backup the file before editing it.

 Open the file ~/.mozilla/firefox/pluginreg.dat
 change 
 Shockwave Flash 7.0 r63:$
 to
 Shockwave Flash 9.0 r63:$

I've just tried it on that site and it seems to work.
Hope this helps.

WOW!  It works!!  

**Installed Plugins:** (8)
- Adobe Reader 7.0
- Google VLC multimedia plugin 1.0
- Java(TM) Plug-in 1.5.0_06-b05
- mplayerplug-in 3.17
- QuickTime Plug-in 6.0
- RealPlayer 9
- [color=#990000]Shockwave Flash 9.0 r63[/color]
- Windows Media Player Plugin

---

### Post by Apotheosis on 2006-08-14
> **Malac said:**
> This will make most sites think you are running version 9 in Ubuntu even if you are not.
Don't forget to copy/backup the file before editing it.

 Open the file ~/.mozilla/firefox/pluginreg.dat
 change 
 Shockwave Flash 7.0 r63:$
 to
 Shockwave Flash 9.0 r63:$

I've just tried it on that site and it seems to work.
Hope this helps.

Sorry, but I am really a newb.  How does one open said file to edit it?

---

### Post by Malac on 2006-08-14
> **Apotheosis said:**
> Sorry, but I am really a newb.  How does one open said file to edit it?
```
gedit ~/.mozilla/firefox/pluginreg.dat
``` replace gedit with kate or whichever editor you have installed.

Hope this helps.

---

### Post by Apotheosis on 2006-08-14
> **Malac said:**
> ```
gedit ~/.mozilla/firefox/pluginreg.dat
``` replace gedit with kate or whichever editor you have installed.

Hope this helps.

That helped, and thanks for that, but it didn't do anything. :(

[[IMG]http://img113.imageshack.us/img113/6486/screenshoteq9.th.png[/IMG]](http://img113.imageshack.us/my.php?image=screenshoteq9.png)

---

### Post by Malac on 2006-08-14
> **Apotheosis said:**
> That helped, and thanks for that, but it didn't do anything. :(

[[IMG]http://img113.imageshack.us/img113/6486/screenshoteq9.th.png[/IMG]]("http://img113.imageshack.us/my.php?image=screenshoteq9.png")

That's odd because it did work for me on the site I was trying to get.
Can you post the site address or the .swf file then I can check on my machine.

---

### Post by Apotheosis on 2006-08-14
Well as I didn't have a site off hand to check it with, I just used the site posted earlier in this thread - [http://www.2advanced.com/](http://www.2advanced.com/).

The funny thing is, that when I went to the site to make sure it was the right one to direct you to, it worked.  I have no idea what I did to make it work, but hey, I'm not complaining.  :)

Edit to add* That said, I still can't view videos on spikedhumor.com.  [Here]("http://www.spikedhumor.com/articles/7879/Football_Skills_Ronaldinho.html") is one for an example.

---

### Post by bionnaki on 2006-09-01
hello. I am having the same problem. editing pluginreg.dat does nothing for me. any ideas?

---

### Post by cbudden on 2006-09-01
> **bionnaki said:**
> hello. I am having the same problem. editing pluginreg.dat does nothing for me. any ideas?


Changing pluginreg.dat only tricks the web site into thinking that you do have Flash 9 installed, and you only have flash 7.  Perhaps the website NEEDS flash 9 to work.

---

### Post by deanlinkous on 2006-09-03
Strange that sounds just like my trick that I posted here....
[http://www.ubuntuforums.org/showthread.php?t=210945](http://www.ubuntuforums.org/showthread.php?t=210945)

btw- make sure you close your browser and reopen
Also depending on where and how you installed firefox the pluginreg.dat file may be located somewhere else so you can look aroudn for it or search your system for it.

---

### Post by Malac on 2006-09-03
> **cbudden said:**
> Changing pluginreg.dat only tricks the web site into thinking that you do have Flash 9 installed, and you only have flash 7.  Perhaps the website NEEDS flash 9 to work.

Yes, I should have said this is only to fool sites which have just cut and pasted code in requiring version 9 to their pages even though the actual content is still playable by version 7.

---

### Post by deanlinkous on 2006-09-03
Also if you have a problem with no text in menus on some flash pages then I always install the msttcorefonts package and the gsfonts package and sometimes that helps.

I am currently working on another hack - actually trying to make the newer flash version work on linux but I am afraid adobe [http://blogs.adobe.com/penguin.swf](http://blogs.adobe.com/penguin.swf) will beat me on this one plus I do not have the legal rights to do it either. :)

---

### Post by deanlinkous on 2006-09-03
This of course works on other mozilla based browsers as well just need to find the appropriate file to edit.

It SHOULD work on opera but I have not been able (or devoted much time) to getting it to work on it.

---

### Post by annihilation on 2006-09-03
Hi, is this the same procedure with the 64 bit version of Ubuntu. I cant find the line in the file. Instead I find Shockwave 8.0 . I get the gnash player when I try to play youtube videos and the videos dont play. It directly goes to the last frame of the video i.e asks you if you want to rate the video or play again. Cant seem to play it.

HELP!

---

### Post by russelld on 2006-09-04
> **Uncle Spellbinder said:**
> WOW!  It works!!  

**Installed Plugins:** (8)
- Adobe Reader 7.0
- Google VLC multimedia plugin 1.0
- Java(TM) Plug-in 1.5.0_06-b05
- mplayerplug-in 3.17
- QuickTime Plug-in 6.0
- RealPlayer 9
- [color=#990000]Shockwave Flash 9.0 r63[/color]
- Windows Media Player Plugin


Please explain how you did this?
what OS Firefox are you using?
 FF in Linux doesn't have plugins for Quciktime, Media Player....
<mystified>  :confused:

---

### Post by jkwarras on 2006-09-04
> **annihilation said:**
> Hi, is this the same procedure with the 64 bit version of Ubuntu. I cant find the line in the file. Instead I find Shockwave 8.0 . I get the gnash player when I try to play youtube videos and the videos dont play. It directly goes to the last frame of the video i.e asks you if you want to rate the video or play again. Cant seem to play it.

HELP!
gnahs doesn't support yet FLV (flash video). I use nspluginwrapper on my 64bit system:
[http://ubuntuforums.org/showthread.php?t=193893&highlight=flash+wrapper](http://ubuntuforums.org/showthread.php?t=193893&highlight=flash+wrapper)

---

### Post by twowheeler on 2006-09-06
Yeah, some sites work and some don't with this trick.  Yahoo video still says I need to upgrade flash to version 8, even though I am telling it I have version 9.

---

### Post by Malac on 2006-09-07
> **twowheeler said:**
> Yeah, some sites work and some don't with this trick.  Yahoo video still says I need to upgrade flash to version 8, even though I am telling it I have version 9.
Yeah unfortunately all this trick does is fool some sites.
It depends how they are checking and also whether the content actually uses the version 9 features or whether it is still compatible with version 7.

The rest is in Adobe's hands, if everybody could take the time to e-mail them asking when they are going to upgrade the linux version it may help.

IMHO installing stuff like this under wine-firefox is a huge "get out" for companies who don't support linux properly. I don't wish to detract from wine which is great but it should be seen as a stopgap until linux stuff comes out. If all you do is install under wine-firefox then don't complain, then companies will just write Windows versions of stuff and leave it to the good people who put together wine to try to integrate it; not really the way forward for linux exceptance.[-X

---

### Post by jslmsca on 2006-09-07
> **Malac said:**
> The rest is in Adobe's hands, if everybody could take the time to e-mail them asking when they are going to upgrade the linux version it may help.[-X

That might not be enough.  [This ]("http://www.crn.com/sections/custom/custom.jhtml?articleId=192501179")article states that Flash Player 9 may not be available until 2007.  You can keep track of developments at [this blog.]("http://blogs.adobe.com/penguin.swf/")

---

