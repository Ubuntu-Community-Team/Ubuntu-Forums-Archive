---
title: "WINECFG: Sound tab causes WINE to crash"
date: 2006-07-07
forum: General Help
---

### Post by Shampyon on 2006-07-07
I'll start winecfg, and everything's fine. Unless, that is, I decide to press the AUDIO tab. As soon as I press it, WINE (v0.9.16) begins to crash. The GUI window will remain open until I close the terminal I launched it from, and I get this error readout:

> me@mycomputer:~$ sudo winecfg
err:winecfg:load_drives GetVolumeInformation() for 'G:\' failed, setting serial to 0
ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
*** glibc detected *** free(): invalid pointer: 0x7c037aa8 ***
wine: Assertion failed at address 0xffffe410 (thread 0009), starting debugger...

I've found two possible solutions, but given that they appear quite different I thought it best to seek advice before trying one or the other.

From [this thread]("http://ubuntuforums.org/showthread.php?t=153509&highlight=wine+crash+alsa"):
> I got the similar problem, the message is a bit different:
ALSA lib seq_hw.c:455snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory
*** glibc detected *** free(): invalid pointer: 0x7c069eb8 ***
wine: Assertion failed at address 0xffffe410 (thread 0009), starting debugger...

Winecfg crash when I select the audio folder.
============================================
Solved.

The problem is the crash of artd during the automatic audio detection of wine.
to solve it just rename /usr/lib/wine/winearts.drv.so to something like renaming /usr/lib/wine/winearts.drv.so.old

The solution is in:

Bye

And from [this one]("http://ubuntuforums.org/showthread.php?t=121682&highlight=wine+crash+alsa"):
> Old post to comment to, but I found a partial answer for this.

I had the winecfg crashing problem when going to the Audio tab, until I found my sound module wasn't loaded and ALSA compatible.

I mod-probed the correct one and it doesn't crash now.

I don't know where to go from here. I'd love to get WINE up and running so I can use that handy little trick of running apps installed in my local XP partition. I miss uTorrent :(

---

### Post by tsb on 2006-07-07
I have this issue in MEPIS but not in Ubuntu.  I hope someone figures it out.

---

### Post by doancm2003 on 2006-07-07
from different search


1. to avoid crash,  rename that file as suggest

2. the other error

in terminal code

sudo modprobe snd-seq

---

### Post by Miguel on 2006-07-07
OK, this sound tab thing also happens to me. Both in Dapper wine (0.9.9) and in 0.9.15 (I didn't activate winehq's repository). I will try now if renaming the file will work. 

Anyway... the weird thing is that this didn't happen to me a while ago. At least when I was running dapper flight whatever (around march). I don't know if installing KDE and XFce would override some setting somewhere (like usplash). 

BTW: Does anybody know why this happens?

EDIT: Modprobing snd_seq doesn't solve the crashes, but moving the winearts lib does (after removing all the snd_* modules, so I could isolate the cause of the crash). I don't know if wine will work now (it still complains about snd_seq), but at least I can configure it.

Thanks a lot! (even if I found this in a search)

---

### Post by Shampyon on 2006-07-07
I did the simple file rename fix, and everything seems fine.

---

### Post by DaveNF2G on 2006-07-15
mine keeps asking for libjack.so

I installed jack and jack-async and a search for libjack.so in particular in Synaptic turns up nothing.

---

### Post by adab on 2006-07-15
Try changing hardware acceleration in audio tab of winecfg to FULL.
Cya

---

### Post by DaveNF2G on 2006-07-17
It's already set to FULL.

Maybe I need to take a step backward.  In the driver window, it lists ALSA, EsoundD, OSS, and NAS drivers.  Which one should be selected?

Also, should the Driver Emulation box be checked or not?

---

### Post by hubacap on 2006-07-24
having similar problem - -  when audio tab is clicked GUI closes and the following appears in Terminal.... complete noob here (to Linux and Ubuntu) so talk to me like I'm 2

```
Creating link /home/hubcap/.kde/socket-username-desktop.
can't create mcop directory
```

I kept searching and found this for a resolution...

[http://www.ubuntuforums.org/showthread.php?t=196033&highlight=mcop+directory]("http://www.ubuntuforums.org/showthread.php?t=196033&highlight=mcop+directory")

---

### Post by !nkubus on 2006-07-24
Really cool now I can listend to sound properly in wine :)

thanks

---

### Post by Bonez56 on 2006-07-28
I fixed this exact problem simply by doing this:

```
 mkdir -p $HOME/.kde/socket-`hostname` 
```

Now I can get in and disable OSS and enable ALSA, I have got sound in Wine :)

YAY!:p

---

### Post by shasta on 2006-07-28
> **DaveNF2G said:**
> mine keeps asking for libjack.so

I installed jack and jack-async and a search for libjack.so in particular in Synaptic turns up nothing.


I had the same problem but installing libjack0.100.0-dev got rid of the message.

---

### Post by DaveNF2G on 2006-08-07
OK, I've installed just about everything connected to JACK and libjack via Synaptic.  I no longer get the libjack.s0 error and JACK just showed up for the first time in the winecfg audio driver list.  I have it selected and all others deselected - including ALSA - and now I get this:

ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory

Now what?

---

### Post by Fixxxer on 2006-08-18
> **DaveNF2G said:**
> OK, I've installed just about everything connected to JACK and libjack via Synaptic.  I no longer get the libjack.s0 error and JACK just showed up for the first time in the winecfg audio driver list.  I have it selected and all others deselected - including ALSA - and now I get this:

ALSA lib seq_hw.c:456:(snd_seq_hw_open) open /dev/snd/seq failed: No such file or directory

Now what?

Add the line "snd-seq" (without the quotes) to /etc/modules

---

### Post by DaveNF2G on 2006-08-18
I don't know whether this was exactly what you meant, but I backtracked in the thread and executed the command "sudo modprobe snd-seq" in terminal mode.  Problem solved!!!

Thanks to all.

---

### Post by dom02 on 2006-08-19
Is winecfg crashing? Or is it just freezing?  If it's just freezing give it a sec and ignore the messages coming up in terminal.  I thought mine was chrasing everytime I clicked the sounds tab as well but I just left it running once for a minutes or two and the tab opened.

---

### Post by DJRockoBobo on 2006-08-19
As someone already said - it's a common problem.....but I know how to deal with it. You have to install a pretty cool programme....WINE TOOLS - [http://www.ubuntuforums.org/showthread.php?t=149585](http://www.ubuntuforums.org/showthread.php?t=149585) - here it is and after you install it in the main menu you will find Wine Configuration or something like it....and if you open it.....it will the same thing as winecfg.....but you will be able to enter sound tab

---

### Post by stuart.crouch on 2006-09-07
I installed wine and winetools (followed the tutorial linked above), did the modprobe and renamed the .so file.  I get this message whenever I click the audio tab.

```

stuart@stuart-desktop:~/bin$ winecfg

*** glibc detected *** free(): invalid pointer: 0x7c073b58 ***
wine: Assertion failed at address 0xffffe410 (thread 0009), starting debugger...

```

And thats all it does, has anyone seen this before or know how to fix it?

---

### Post by Pettman on 2006-09-15
> **stuart.crouch said:**
> I installed wine and winetools (followed the tutorial linked above), did the modprobe and renamed the .so file.  I get this message whenever I click the audio tab.

```

stuart@stuart-desktop:~/bin$ winecfg

*** glibc detected *** free(): invalid pointer: 0x7c073b58 ***
wine: Assertion failed at address 0xffffe410 (thread 0009), starting debugger...

```

And thats all it does, has anyone seen this before or know how to fix it?

I get exactly the same, is there a way to edit the configuration as a textfile?

---

### Post by tscook on 2006-10-05
Even though I definately have JACK and libjack and have sucessfully used them with other programs (Omsynth, amsynth, etc) I now get in conjunction the errors:

With Wine

```

fixme:jack:JACK_drvLoad error loading the jack library libjack.so, please install this library to use jack
```

With JACK Control

```

loading driver ..
apparent rate = 44100
creating alsa driver ... hw:0|hw:0|1024|2|44100|0|0|nomon|swmeter|-|32bit
control device hw:0
the playback device "hw:0" is already in use. Please stop the application using it and run JACK again
cannot load driver module alsa
no message buffer overruns
```


Any ideas, as I don't see anything running that would be so hella conflicting, but then again I am a total noob.

---

### Post by ilushkin on 2006-10-28
I have the similar problem. Can someone help us?
> **stuart.crouch said:**
> I installed wine and winetools (followed the tutorial linked above), did the modprobe and renamed the .so file.  I get this message whenever I click the audio tab.

```

stuart@stuart-desktop:~/bin$ winecfg

*** glibc detected *** free(): invalid pointer: 0x7c073b58 ***
wine: Assertion failed at address 0xffffe410 (thread 0009), starting debugger...

```

And thats all it does, has anyone seen this before or know how to fix it?

---

### Post by ilushkin on 2006-10-28
[Wine 0.9.24]("http://www.linux-gamers.net/modules/news/article.php?storyid=1829") released, how soon it will be available for the update?

---

### Post by ilushkin on 2006-10-28
"What I did was go to the /usr/lib/wine    where all of the
library files for Wine are stored.   Wine would crash when trying to
click on the audio tab when winecfg was run.  The problem was related
to aRTs crashing it. had to go to this directory and change
winearts.drv.so to winearts.drv.so_bak and removed the original.  Reran
winecfg and was able to set up audio again."

---

### Post by Gomek on 2006-11-14
Got a similar error in 0.9.25.  Renaming the arts /usr/lib/wine/winearts.drv.so fixed it.  Thanks for the helpful thread.

---

