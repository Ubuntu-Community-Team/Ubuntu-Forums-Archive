---
title: "Skype"
date: 2005-03-20
forum: General Help
---

### Post by rmn30 on 2005-03-20
Hi,

Just installed hoary preview and result is very pleasing :-). Only thing which took me some time to get working is the Skype voip client. Thought I might post the steps that (almost) worked here for the benefit of others:

1. Download debian package:

[http://www.skype.com/go/getskype-linux-deb](http://www.skype.com/go/getskype-linux-deb)

2. Install qt and old xft version from universe:

```
sudo apt-get install libqt3c102 libqt3c102-mt libqt3c102-ibase
sudo apt-get install libxft1
```

(Optionally install qt-config so we can get qt looking OK)

```
sudo apt-get install qt-config
```

3. Install skype .deb

```
sudo dpkg -i skype_1.0.0.20-1_i386.deb
```

Only problem is that it hangs when making a call. I discovered on skype forums that this is due to something else using /dev/dsp so I ran:

```
killall esd
```

Which worked except now I have no sound in gnome :-( Does anyone know of a way to get gnome and skype to cooperate?

Cheers,

Robert

---

### Post by mflash on 2005-03-21
[QUOTE=rmn30]
...
Only problem is that it hangs when making a call. I discovered on skype forums that this is due to something else using /dev/dsp so I ran:

```
killall esd
```

Which worked except now I have no sound in gnome :-( Does anyone know of a way to get gnome and skype to cooperate?

Cheers,

Robert[/QUOTE]
I also have to kill esd to get skype to work.
But you may want to try esddsp, part of esound-clients package:
```

esddsp skype

```
This is a wrapper script, so skype will use the sound device through esd.
It MAY work for you. For me, it did on Warty, but not on Hoary - no idea why.

---

### Post by rmn30 on 2005-03-21
> 
```

esddsp skype

```
This is a wrapper script, so skype will use the sound device through esd.
It MAY work for you. For me, it did on Warty, but not on Hoary - no idea why.

Unfortunately doesn't seem to work for me either, although it does prevent it from hanging - all i get is silence during a call.

I changed the following line in /etc/esound/esd.conf:

default_options=

to read

default_options=-as 5
 
This will cause the sound daemon to relinquish /dev/dsp after 5 seconds of inactivity allowing skype to get it, providing nothing else is playing any sounds...

Not perfect but some improvement. Any other recommendations would be appreciated - especially an explanation of why esddsp doesn't work any more?

Bob

---

### Post by rykel on 2005-06-10
Hi, 

I have exactly the same problem too, and hope to find an answer.

No microphone sound input in Skype, although I can hear the other party... outside of Skype, there is absolutely no sound problem.


Best Regards,

Rykel

---

### Post by Servus on 2005-10-10
I habe the same problem: in skype I can hear sounds but the microphone does not work. In other applications like audacity the microphone works perfectly... please HELP!!
servus

---

### Post by PatrickMay16 on 2005-10-10
After killing esd, you can bring it back to life again by typing the command

```

esd

```

At least, that worked for me.

---

