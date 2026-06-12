---
title: "Problem using remote desktop with Windows Vista"
date: 2007-09-26
forum: General Help
---

### Post by Palpie on 2007-09-26
I've recently installed Ubuntu on my laptop and was glad to see it was possible to use remote desktop with Windows, which I run on my other computer. But know when I've used rdesktop for a while there are two main problems making it not so pleasant to use:

The worst is that it freezes from time to time. I've tried to wait it out but it seems the only way to fix it is to reconnect. Everything runs smoothly when it works. When running on my home LAN it don't happen as often as when I'm running it from somewhere else. Sometimes I can only run it for about 10-20 seconds. Still, it runs smoothly and just freezes suddenly. The only solution I've found for this is to upgrade rdesktop to versions later than 1.0. But I have 1.5.

The other issue is easier to avoid, but still irritating. Except the freezes, remote desktop works fine. Except when I run any Office application. I've tried with Word, Excel, Visio and Outlook, they all make my Windows machine crash. Only when using remote desktop that is. If your only comment is some negative remarks about Microsoft, don't bother to answer.

I've tried the rdesktop switches "-a 8 -x m -z", but it didn't solve anything.



Ubuntu 7.04
rdesktop 1.5.0.1-ubuntu
RDPv5
Windows Vista Business
Office 2007

---

### Post by veloce on 2007-09-26
I think we had to turn off some of the security settings in Vista for this to work properly.  I didn't do it, so I'm not sure what we did.

I tend to use either terminal server or gnome rdp to connect and their default settings work fine for me.

Veloce.

---

### Post by Palpie on 2007-09-27
Seems to work fine with gnome-rdp. Now I've been running it for 10 minutes without freezes. Also I've been running Word, Excel and Visio at the same time, without crashes. Very nice.

Thanks for the tip!


[EDIT]
I was wrong. Word just crashed the remote computer and the freezes has also occurred. It just took a while longer before it happened.

---

