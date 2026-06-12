---
title: "How to turn off all the bells and whistles/ basic mode/adjust for best perf."
date: 2021-09-30
forum: General Help
---

### Post by adambond on 2021-09-30
Ubuntu 20.04.3 LTS

I recall back when using windows, you could opt to lighten up/free up/speed up the system by clicking "Adjust for best performance". 
But anyways, how do I do that on this resource hungry ubuntu?  
I literally want to just turn off all the bells and whistles. And just run a basic mode. 

Thanks in advance.

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289218&stc=1[/IMG]

---

### Post by Impavidus on 2021-10-01
Best is not install the bells and whistles in the first place. Use a lighter desktop environment (like the one you get in Lubuntu) or install no desktop environment at all, just a window manager. Or even lighter than that, no GUI at all, but that will hurt usability. You could start with a minimal install and just add the things you want.

The light flavours are really light. Making it even lighter won't give a significant performance boost one somewhat modern hardware. Most of the load is in the applications you run, not in the OS or desktop environment, so if your computer gets sluggish when loading some particular website, the best place to complain it at the website designer. But rumour has it that they conspire with computer manufacturers, making websites heavier to boost sales of more powerful computers...

---

### Post by sudodus on 2021-10-01
If you still want a graphical desktop environment, you can select Lubuntu or Xubuntu instead of standard Ubuntu Desktop.

It is most efficient, if you make a fresh installation of one of those light-weight community flavours of Ubuntu. But if you have spend a lot of time to tweak your Ubuntu already, you can also install one of the meta packages

```

lubuntu-desktop

#or

xubuntu-desktop

```

into your Ubuntu. At the log-in screen you can select 'session': Lubuntu or Xubuntu instead of Ubuntu, and get a system that uses less RAM and is more responsive. Particularly in old computers there will be a significant difference.

If you don't want a graphical desktop environment you can make a fresh installation of Ubuntu Server (and avoid installing the optional services).

---

### Post by dragonfly41 on 2021-10-01
Another approach which I use is to [install Stacer]("https://oguzhaninan.github.io/Stacer-Web/#:~:text=Stacer%20is%20an%20open%20source,%2Drepository%20ppa%3Aoguzhaninan%2Fstacer") and use the Stacer GUI to shut down various installed apps.
It does add another GUI but does help with optimising performance.

---

### Post by grahammechanical on 2021-10-01
I understand "Integrated Graphics" to mean that graphic processing is done by the CPU and video memory is shared with system memory. On the other hand, "Discrete Graphics" means that there is an additional adapter with its own Graphic Processor Unit (GPU) and its own video memory chips.

I also have a dual core CPU. Your CPU is faster than my CPU. You have slightly more memory but I have a discrete graphic adapter with 1GB of video memory. That explains why I do not consider Ubuntu to be "bloated" as you claim.

The System Monitor utility will show real time use of CPU, memory and internet download and upload rates. And as stated above there are other desktop environments that use fewer system resources than the Gnome 3 shell that Ubuntu uses. There are also other web browsers than Firefox and Office suites than LibreOffice. How they compare as to resource usage I cannot say.

I really do not understand what you mean by "bells and whistles." This expression was used in the old days. I understood the phrase to mean that the application has a lot of features that users require. I also believe that Linux developers put a lot of time and energy into keeping their software "lean and mean." The reason is simple. They reject nearly all the practices and policies of certain distributors of rival operating systems.

Regards

---

### Post by T6&amp;sfpER35% on 2021-10-01
i have a slower CPU than yours ,with 3gig ram,don't know what ram you got 
anyway i'm on xubuntu and it's flying 
:D

---

### Post by adambond on 2021-10-01
My computer freezes up constantly.  I cant figure out what it is. And i  cant "Alt,Print/scrn,R". It simply does not work after it freezes.  It  will work all day long when comp is acting normal.  An example would be  watching a youtube video, and all the sudden everything will lock  up/freeze, and then the audio from the video will repeat skipping, like a  scratched CD would.   I have to force shut down.  

I thought maybe it was firefox. But rebooted my comp one day, and walked  away once the desktop loaded. I didnt open anything. When i come back,  it had frozen.  Had to force shut down.  Thats rare. Its mainly when i  am 
browsing via firefox. Chrome also. 
This is just with 1 tab open, and a music video on youtube playing. 

Thanks for the suggestions, i'll try some. 

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=289223&stc=1[/IMG]

---

