---
title: "Remote Asisstance Ubuntu to Ubuntu?"
date: 2007-11-01
forum: General Help
---

### Post by Githlar on 2007-11-01
I convinced a friend of mine to install Ubuntu on a Toshiba Satellite that he owns. However, he has recently had problems with his sound failing among other things. He has not worked a lot with the back-end of Linux and lots of the tutorials given usually require some from of knowledge of commands/terminal. The person of which I am speaking has none of that knowledge. I tried troubleshooting it with him over an instant messenger, but that's quite frustrating because he doesn't know what information he needs to tell me.

So, I figured the best way to go about it would be through some kind of remote assistance. I've had some experience with Remote Assistance in Windows. However, using some kind of remote assistance from an Ubuntu machine to an Ubuntu machine seems to be quite a bit more difficult. I've already run him through the process of setting up his machine to accept remote assistance (I think...), yet when I try to send him a request, nothing happens.

Could some body step me through the process of getting remote assistance working over the internet (that is, not within the same network) using either the RDP or VNC protocols?

---

### Post by Pumalite on 2007-11-01
[http://ubuntuforums.org/showthread.php?t=472998](http://ubuntuforums.org/showthread.php?t=472998)

---

### Post by bingoUV on 2007-11-01
You will somehow have to get him to install ssh server. (ubuntu should really install it out of the box). He can search for openssh-server in synaptic.

Then you can remotely help him using this. (an old but useful how-to) [http://ubuntuforums.org/showthread.php?t=266981](http://ubuntuforums.org/showthread.php?t=266981)

---

### Post by Githlar on 2007-11-02
Yeah. I don't know why I didn't think of SSH first. But, I want him to know what I'm doing.

I did what this tutorial said. I enabled the right settings on both computers. I opened the Terminal Server Client and tried to connect, but nothing happened on the other end.

---

### Post by hikaricore on 2007-11-02
Correct me if I'm wrong, but doesn't Gnome have a built-in Remote Desktop function that you simply need to enable?

Been using KDE so long I forget.

---

### Post by Githlar on 2007-11-03
Theoretically, yes. But, for some reason it's not working like it should.

---

