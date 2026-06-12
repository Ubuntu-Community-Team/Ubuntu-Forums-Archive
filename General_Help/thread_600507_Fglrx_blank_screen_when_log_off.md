---
title: "Fglrx blank screen when log off"
date: 2007-11-02
forum: General Help
---

### Post by pssturges on 2007-11-02
Hi,

 I have installed the fgrlx drivers for my ATI radeon 9600 in gutsy. It all works well except for when I try to log out or switch users. I get a blank screen & the only way I can get it started again is to hit the reset button! I've done some searching around & found a solution that some people have been using in Fiesty. This was go to System > Administration > Login window and on the "General" tab make sure "Restart the Xserver with each login" is ticked. Problem is, Gutsy doesn't seem to have this option.

Are there any other ways to get around this? Any other solutions?

Thanks in advance,
Phil

---

### Post by Stemp on 2007-11-02
It will probably work by changing the line :

```
#AlwaysRestartServer=
```
into
```
AlwaysRestartServer=true
```

in your /etc/gdm/gdm.conf file

---

### Post by pssturges on 2007-11-02
Thanks Stemp,

I have no changed that, but unfortunately it didn't solve the problem.:(. When I log out or try to switch user, I get the blank screen & the machine locks up. Ctl+Alt+Backspace doesn't even get me out of it!

Thanks again
Phil

---

### Post by Stemp on 2007-11-02
I just noticed you have an ati 9600.
Why are you using the fglrx drivers ? 
The free open source ati/radeon drivers work really fine and without xserver-xgl ;)

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by pssturges on 2007-11-02
Thanks for that link. I was using them mainly because I thought it was the only way I could get Compiz working well:confused:. The other reason is that I want machine to serve part-time as a Mythtv frontend, connected to a TV via S-video or preferably component. Is this possible with the open source drivers?


Thanks again
Phil

---

### Post by Stemp on 2007-11-02
Sorry Phil but I don't know about ati free driver and tv.
Never tried that.

---

