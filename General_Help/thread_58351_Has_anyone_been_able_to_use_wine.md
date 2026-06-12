---
title: "Has anyone been able to use wine?"
date: 2005-08-19
forum: General Help
---

### Post by easy_target on 2005-08-19
I install the official Ubuntu copy of wine but I can't even install internet explorer!!! What's the point???

---

### Post by kes on 2005-08-20
I also had some problems with old version of wine, so I've installed wineHQ from [http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)
now it's working almost for all windows application I have to use.
Hope it will help you.

But I'm quite surprised, why do you insist on using IE under Linux when there are many internet browsers which are much better: Firefox, Opera, Galeon, classical Mozilla in the end? Of couse it a matter of personal preferences, but why don't you try them to find a suitable one for your needs.

---

### Post by easy_target on 2005-08-21
As a matter of fact I wasn't trying to install explorer for any browsing purposes. I just wanted to do it for the fun of seeing linux "jump over the fence and graze in microsoft' s pastures."  :)
Any chance Rainbow Six would run under wine?

Cheers

---

### Post by Picklegnome on 2005-08-21
I downloaded wine, libwine, and wine-utils, and burned the .deb s to a cd, since I don't have an internet connection on the Linux computer. I was able to use dpkg successfully for all of them, and when I looked in the Synaptic Package Manager, wine-utils and wine were there (under "Cross Platform"). What steps do I need to take to be able to open .exe files now? When I try, it says there is nothing to open it with.

Thanks!

---

### Post by akseli on 2005-08-22
[QUOTE=easy_target]As a matter of fact I wasn't trying to install explorer for any browsing purposes. I just wanted to do it for the fun of seeing linux "jump over the fence and graze in microsoft' s pastures."  :)
Any chance Rainbow Six would run under wine?

Cheers[/QUOTE]

To run Rainbox Six and other games you'll have to download another program that emulated Windows DirecX APIs ... for example:

WineX/Cedega

(search google for either term)

---

### Post by akseli on 2005-08-22
[QUOTE=Picklegnome]I downloaded wine, libwine, and wine-utils, and burned the .deb s to a cd, since I don't have an internet connection on the Linux computer. I was able to use dpkg successfully for all of them, and when I looked in the Synaptic Package Manager, wine-utils and wine were there (under "Cross Platform"). What steps do I need to take to be able to open .exe files now? When I try, it says there is nothing to open it with.

Thanks![/QUOTE]

Ok, lets see if I can help you here...
1. When you did the dpkg you installed also, right? As in dpkg -i or dpkg install ?
if you didn't you should do so.
2. Since you say that you now see the packages in synaptic, I suppose you have done the process described above, so now you have wine installed.
3. If you look at wines manuals you'll notice that to run wine and set it up you'll have to open up a terminal and use the following code:
```
sudo wine
``` 
by using this command you will open up a window that will ask you whether you want to configure wine or not. You can accept most defaults.

After this and:
```
killall gnome-panel
```
```
killall nautilus
```
this should allow for all shortcuts and default applications to get updated. Once this is done you should be able to doubleclick on an exe file and wine should load up.

Good luck!
(I may be mistaken with the process as I'm not at my Linux machine at the moment and the instructions I'm giving you are completely from memory. If this doesn't work either reply in this thread or PM and I'll get back to you with better instructions based on my Ubuntu installation at home.

---

### Post by kes on 2005-08-22
2Picklegnome: On my notebook wineHQ was working perfectly  just with dpkg -i, so I'm quite astonished that you need some additional actions... :???: 

If you want to configure or see the defaults configuration of wine just type "winelauncher" in terminal (but on my opinion this is really doesn't necessary, the defaults are working).
To make some application run just type in terminal: 
winelauncher 'path-to-the-exe-you-wish-to-run' 

P.S. Since I'm quite lazy and don't like to use terminal a lot, I just created an additional starting button: winelauncher '/home/kes/.wine/drive_c/Program Files/WhereIsIt/WhereIsIt.exe'
It works both ways: from terminal and like that

P.P.S. A bit stupid remark, but did you try to put in the properties of exe-fichiers "open with wine"?

---

### Post by mikwig on 2005-08-22
Agreeing with KES

I am a cedega suscriber, which is a variation on wine -
after installing it, I simply right clicked an exe file and
selected {open with}/{open with other aplication}
and typed cedega in the box.

I am sure it would be the same with wine (though I am often wrong)

---

### Post by easy_target on 2005-08-22
I have seen in the forums here that there is a version of cedega that can be installed free of charge, How do I do that?

---

### Post by Picklegnome on 2005-08-22
Well, I got to the point where I was configuring it, and it said I don't have winesetuptk. I googled it and can't seem to find it. Anybody know where it's available?

---

### Post by akseli on 2005-08-23
[QUOTE=easy_target]I have seen in the forums here that there is a version of cedega that can be installed free of charge, How do I do that?[/QUOTE]
You can get Cedega/WineX for free if you compile it yourself. The process is described here:
[http://frankscorner.org/index.php?p=cedegacvs](http://frankscorner.org/index.php?p=cedegacvs)
As the page describes you'll need to install CVS which is not installed as a default in Ubuntu. 
Don't hesistate to task if you need more help!

---

### Post by akseli on 2005-08-23
[QUOTE=Picklegnome]Well, I got to the point where I was configuring it, and it said I don't have winesetuptk. I googled it and can't seem to find it. Anybody know where it's available?[/QUOTE]
I am not sure why you are getting this error, but you might want to follow the installation instructions available here. They worked perfectly for me and many others. Good luck!
[http://ubuntuforums.org/showthread.php?t=56892&highlight=wine](http://ubuntuforums.org/showthread.php?t=56892&highlight=wine)

---

### Post by Picklegnome on 2005-08-23
Well, I found and downloaded the .deb that it says I need. I burned it to cd, then tried to dpkg -i it, but it says there is an i/o error. I've tried doing the same thing with several discs, and with packages downloaded from several sources, but none works. Any ideas?

Thanks for helping,
Picklegnome

P.S. If I can't solve the problem in a few days, I'm going to attempt to create the config file manually. But I really hope it doesn't come to that.

---

### Post by Picklegnome on 2005-08-23
Ok. Problem solved. I was using an old release.

Last question (I hope):
I installed a windows app in C:\Windows\Program Files\[App]
Where can I find the .exe on my filesystem?

Thanks to all who helped!
Picklegnome

---

### Post by jobezone on 2005-08-23
[QUOTE=Picklegnome]
I installed a windows app in C:\Windows\Program Files\[App]
Where can I find the .exe on my filesystem?
[/QUOTE]
 Your wine C drive should be located at **~/.wine/drive_c**.

Notes:
- **~** is the same as your home directory, so the above is the same as **/home/yourusername/.wine/drive_c/**.
- **.wine** is a hidden directory, since it has a leading dot(**.**)

---

### Post by ongjacob on 2005-10-07
[QUOTE=Picklegnome]I downloaded wine, libwine, and wine-utils, and burned the .deb s to a cd, since I don't have an internet connection on the Linux computer. I was able to use dpkg successfully for all of them, and when I looked in the Synaptic Package Manager, wine-utils and wine were there (under "Cross Platform"). What steps do I need to take to be able to open .exe files now? When I try, it says there is nothing to open it with.

Thanks![/QUOTE]

Picklegnome, I'm also trying to install wine on a machine w/o internet connection.  I see from this thread that you have successfully done it.  Can you provide a list of the packages that needs to be downloaded?  Is there a specific order or sequence that the packages need to be installed?

Thanks.

---

