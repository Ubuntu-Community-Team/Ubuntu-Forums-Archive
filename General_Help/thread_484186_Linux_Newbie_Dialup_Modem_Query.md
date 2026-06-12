---
title: "Linux Newbie Dialup Modem Query"
date: 2007-06-25
forum: General Help
---

### Post by james4ad on 2007-06-25
Greetings Everybody

I have a Dell Dimension 4700 and this is my first introduction to Linux. I've researched all the different main distros and felt that Ubuntu was a really nice option to work with. I discovered that in general Linux works best with external serial dialup modems, so rather than use the winmodem I purchased a new zoom external dialup modem.

The modem dials up as it is supposed to perfectly, it seems to log into the ISP provider but then there is no "connection live" display of any kind but at the same time when I pick up the telephone (on the same line) it seemingly is connected and additionally the green led 56k light is displayed so I'm left with the feeling that somehow the modem is working fine and the system is  connecting as it should but perhaps there is some minor adjustment I have left out.

Has anybody got any suggestions they perhaps could offer?

Many Thanks
James

---

### Post by Shazaam on 2007-06-25
Open Synaptic> search for gnome-ppp and install it if you haven't already (or KPPP if you are using kde).
This should give you an icon in your panel when you are connected.

---

### Post by james4ad on 2007-06-25
Hi Shazaam,
Thanks for  your help. I read  somewhere on the forum that for a fresh install you need to download gnome ppp? I'll log back onto ubuntu and see if I can find it.
Thanks again
James

---

### Post by bill45 on 2007-08-30
Hello Shazaam;
I'm in same state with my 2nd install Ubu on an old Dell GX150 w serial Zoom.   In 6.06 the modem was balky but connected.  In 7.04 the modem dials, sounds like connecting but does not allow any apps or browser to connect.  

I cannot use synaptic to acquire WVdial or other utils or update my reposits.  

Both 6.06 and 7.04 modem reverts to pulse dial will not stick on tones. 

Bill
[email]mozsugg@isp.com[/email]

---

### Post by bill45 on 2007-08-30
Solved modem problem (I think). I  inserted OpenDNS IPs into network config and retried and this time it connected.  Perhaps dial up needs some DNS addresses to connect.  Did not do this in 6.06

How do I get Gnome PPP dialer up on the desktop?

---

