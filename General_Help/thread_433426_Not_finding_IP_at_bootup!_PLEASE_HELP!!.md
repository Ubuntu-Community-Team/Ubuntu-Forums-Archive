---
title: "Not finding IP at bootup! PLEASE HELP!!"
date: 2007-05-05
forum: General Help
---

### Post by VolvoPunch on 2007-05-05
I installed Ubuntu and was surfing the net in no time... But i am trying to setup the box as a game server and i will be logging in via ssh. Well i opened up the network program and selected my network card to be activated and i selected dhcp which me router is running. But when ubuntu boots the the login screen it still has not grabbed an ip. This box will be sitting in the corner with nothing attached to it exect a network cable and power cable so when it boots i need it to grab an ip. 

I am starting to hate this stupid linux **** because it just does not work!!! [http://ubuntuforums.org/images/smilies/icon_mad.gif](http://ubuntuforums.org/images/smilies/icon_mad.gif)
:mad:

---

### Post by VolvoPunch on 2007-05-05
Bump :( I kind of want to put this to bed before i got to bed. :)

---

### Post by VolvoPunch on 2007-05-05
Bump. This can't be that hard of a question to answer.

---

### Post by Wiebelhaus on 2007-05-05
> **VolvoPunch said:**
> I installed Ubuntu and was surfing the net in no time... But i am trying to setup the box as a game server and i will be logging in via ssh. Well i opened up the network program and selected my network card to be activated and i selected dhcp which me router is running. But when ubuntu boots the the login screen it still has not grabbed an ip. This box will be sitting in the corner with nothing attached to it exect a network cable and power cable so when it boots i need it to grab an ip. 

I am starting to hate this stupid linux **** because it just does not work!!! [http://ubuntuforums.org/images/smilies/icon_mad.gif](http://ubuntuforums.org/images/smilies/icon_mad.gif)
:mad:

all this yelling and hating "...." stuff is not cool , i suggest you install winblows.

---

### Post by VolvoPunch on 2007-05-06
Sorry for yelling but i have been working on this problem for awhile and i would just like some help. I posted that message at 1:00am and i was very tiered.

---

### Post by fragos on 2007-05-06
For DCHP to work you may need to completely power down your system at the powerstrip.  Sutdown isn't fully off on many mobo's.  If not started from cold DCHP may use the last IP and DNS data it used.

---

### Post by VolvoPunch on 2007-05-09
Ok i have still not resolved this problem. I have setup my network controller eth0 to a static ip which is 192.168.0.105 subnet of 255.255.255.0 (If i can remember correctly) and then my gateway is 192.168.0.1.
When i log into the computer i have no problem firing up Firefox and getting online but when the system is at the login screen id does not have an ip. It only seems to get an ip when i login.

---

### Post by strixy on 2007-05-09
Have you configured port forwarding on your router?

---

### Post by strixy on 2007-05-09
> **fragos said:**
> For DCHP to work you may need to completely power down your system at the powerstrip.  Sutdown isn't fully off on many mobo's.  If not started from cold DCHP may use the last IP and DNS data it used.

Thanks Fragos! That helped my problem from this post : [http://ubuntuforums.org/showthread.php?t=436499](http://ubuntuforums.org/showthread.php?t=436499)

---

