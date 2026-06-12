---
title: "sound problems"
date: 2005-05-03
forum: General Help
---

### Post by Dave88 on 2005-05-03
Hi i was wondering if anyone could help me with sound problems using Hoary Hedgehog 5.04, Some things have sounf but ohers dont 

_things that do_
system
music player
_things that don't_
mplayer
vlc
xmms
Totem movie player


anyone know what I should do? ](*,) 
I think its a permission issue with /dev/rtc as mplayer seems to indicate.


thanks in advance for help!

---

### Post by rhys on 2005-05-03
[QUOTE=Dave88]Hi i was wondering if anyone could help me with sound problems using Hoary Hedgehog 5.04, Some things have sounf but ohers dont 

_things that do_
system
music player
_things that don't_
mplayer
vlc
xmms
Totem movie player


anyone know what I should do? ](*,) 
I think its a permission issue with /dev/rtc as mplayer seems to indicate.


thanks in advance for help![/QUOTE]
 Firstly go into System -> Preferences -> ?Multimedia Selection? (not sure on what this is called in the English version). The sound tab pops up. Check to see if you are using ESD, OSS or ALSA. Test the current settings. Now go into xmms for example, under configure, set the sound output device accordingly.

I found that I had to configure almost everything that I wanted to play sound with, since I use ESD... 

:) Best of luck.

---

### Post by Dave88 on 2005-05-03
ok so far got xmms to work :razz:  with your advice but i have no idea how to configure mplayer like that, any ideas?

thanks.

---

### Post by rhys on 2005-05-03
[QUOTE=Dave88]ok so far got xmms to work :razz:  with your advice but i have no idea how to configure mplayer like that, any ideas?

thanks.[/QUOTE]
 mplayer? I have never used it. Sorry, mate. There should be a configure thing somewhere in that bugger. Go into xChat and ask in #ubuntu on efnet (IRC). 

Aside: why do you need so many players anyway? Besides, XMMS is ugly, compared to BMP... :)

---

### Post by rhys on 2005-05-03
[QUOTE=rhys]mplayer? I have never used it. Sorry, mate. There should be a configure thing somewhere in that bugger. Go into xChat and ask in #ubuntu on efnet (IRC). 

Aside: why do you need so many players anyway? Besides, XMMS is ugly, compared to BMP... :)[/QUOTE]
 P.S. As for totem... which I could never get to work... I uninstalled it. LOLL.

It was another way to solve the problem, lolll

---

### Post by Dave88 on 2005-05-03
lol, good point!

I should delete some players but thats another set of problem's, I strugggle to play dvd's because of the libdvdcss and libdvdread but the sound thing is more of an issue right now. I'll delete some players once I find a player that does dvds and sound!

thanks alot rhys for all the help, Im starting to get this now.

---

### Post by Dave88 on 2005-05-03
I got it, I unstalled everything to do with ESD (killing firefox and half of my apps in the process) then installed ALSA sound things and Kaffeine Player and I can now play dvd's and apple *.mov files!!!


thanks alot, really helped me out there!

---

### Post by tedeskar on 2005-05-04
This might help with Totem: Check the Gstream packages. When I installed Hoary all necessary Gstram packages for viewing film were not installed. Check in synaptic the status of your packages and install if necessary.

/Tommy

---

### Post by doc_holiday on 2005-05-06
Great help, thanks

---

### Post by corepusher on 2005-08-01
Hi!!! I' ve been having some problems with sound too. Actually I can play mp3 files with beep but I dont have any other sound. Also, whenever music is not playing you can hear this background sound like if a pipe was hitted by a hammer several times and constantly (it wont stop, and you can bet that I've tried a lot of things!!!!! :mad: ) I know that it is a problem with OSS device. I went to the Multimedia System Selector and changed all for ALSA and whenever I try to start totem it would say "could not access ALSA device "default", check it's permissions." 
so, my questions are:
how could I get rid of the annoying sound I hear on the background?
how can I change ALSA permissions?

I will appreciate very much for any help!!!!
THANKS IN ADVANCE  :smile:  :wink:

---

