---
title: "mozilla firefox flash player no sound"
date: 2005-04-05
forum: General Help
---

### Post by Gandalf on 2005-04-05
Hello, :D
flash player mozilla plugin can't output any sound, i don't know why but i see animations but without sound!! is there any tweaking to be done to it (to use esd??)

---

### Post by honeywelljr on 2005-04-10
[Sound problems in hoary](http://www.ubuntulinux.org/wiki/SoundProblemsHoary) 

follow the instructions under "firefox", this fixed me  :grin:

---

### Post by Josh M on 2005-04-12
Followed the instructions, sound is now working.

---

### Post by fazer on 2005-04-19
[QUOTE=honeywelljr][Sound problems in hoary](http://www.ubuntulinux.org/wiki/SoundProblemsHoary) 

follow the instructions under "firefox", this fixed me  :grin:[/QUOTE]
 I followed this instruction and it still doesn't really work for me =(

---

### Post by mrtaber on 2005-04-19
It worked for me--but only after a reboot.  Now I wish someone could explain *why* it works...

Mark :)

---

### Post by honeywelljr on 2005-04-20
Sorry, I don't really now why it works.  I am very new to linux and even newer to Ubuntu.  I managed to stumble across it when I had the problem.  It has been the only thing I have been able to help anyone with.


fazer, when you typed it in did it give you some kind of message or anything?  Is your other sound working just not sound for flash in firefox?  I don't know a whole lot but maybe I can help you search the documentation.  Alot of finding the answer is knowing what to search for

---

### Post by fazer on 2005-05-01
[QUOTE=honeywelljr]Sorry, I don't really now why it works.  I am very new to linux and even newer to Ubuntu.  I managed to stumble across it when I had the problem.  It has been the only thing I have been able to help anyone with.


fazer, when you typed it in did it give you some kind of message or anything?  Is your other sound working just not sound for flash in firefox?  I don't know a whole lot but maybe I can help you search the documentation.  Alot of finding the answer is knowing what to search for[/QUOTE]
Urgh! Sorry about the delay, I forgot about this thread.  I still dont have sound.  When I ran that above command, I didn't get back any output.  For my sound needs, I am using ALSA, perhaps I have to tell the flash player to use ALSA?

Any help would be appreciated.  Thanks.

---

### Post by wazoo on 2005-05-05
Well, the listed thread did not resolve my issue. 

First, I had everything up and running in Warty, and did the apt-get dist-upgrade. 

Second, then I had sound only for the CD player. xmms didn't work, mplayer didn't work. So I reset xmms to esd, and it came up. 

Third, I found another thread that said pkill esd would get mplayer to work again. It worked -- but then none of the other sound things did. If I restart esd, then everything works -- except firefox

I do have esd chosen as System>Preferences>Multimedia Systems Selector. No other choice tests out in that window. How do I make Firefox/mplayer use esd?

So I'm stumped. Other tips?

---

### Post by fazer on 2005-05-20
Hmm, so I guess no one else has problems with this?

---

