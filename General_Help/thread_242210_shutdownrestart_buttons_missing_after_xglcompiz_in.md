---
title: "shutdown/restart buttons missing after xgl/compiz install"
date: 2006-08-23
forum: General Help
---

### Post by cptjaben on 2006-08-23
I recently installed compiz/xgl following [this ]("http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper")guide. Everything seems to be working okay execpt that I no longer have a shutdown or restart button, instead I have 1 large hibernate button which takes up the space where the shutdown and restart buttons would normally be. Does anyone know how to fix this?

Thanks,
cptjaben

---

### Post by VosaxAlo on 2006-08-23
Hi,

same here, but alas no solution for now.

---

### Post by boban on 2006-08-23
Hi!

Same here... but I've made a luncher on my desktop with "sudo reboot" and "sudo poweroff"...

---

### Post by cptjaben on 2006-08-23
Good idea, thanks for the advice.

---

### Post by GoBieN on 2006-08-23
[http://www.ubuntuforums.org/search.php?searchid=7677217](http://www.ubuntuforums.org/search.php?searchid=7677217)

---

### Post by Ramses de Norre on 2006-08-23
I think this is like the issue where you can't use the reboot/halt buttons in KDE when loaded through GDM or in Gnome when loaded through KDM.. For probably the same reason you can't use those buttons in Compiz loaded through GDM (I don't know about KDM).
I guess there is a reason for this.. but I don't know it.

---

### Post by cptjaben on 2006-08-23
Thanks GoBieN, worked perfectly.

---

### Post by neuropsychguy on 2006-08-23
Thanks for the answers to this. I was wondering how to fix this.

---

### Post by calvinthomas on 2006-08-23
I can't go to Gobien's link, it doesn't work, was it a fix? If so can someone repost it please?

Calv

---

### Post by tribaal on 2006-08-25
Same problem here... cannot access the link target either...

- trib'

---

### Post by misosofos on 2006-08-26
I am wondering why that useful link is gone...

Can anyone post the solution?

---

### Post by deeek on 2006-08-27
Yes please, I am having this problem as well.  A working link would be wonderful.

---

### Post by Shaamaan on 2006-08-30
Exact same problem here... And the missing link is just... like... "Damn! I almost had it!" ](*,)

---

### Post by jharris on 2006-08-31
Bump

---

### Post by tribaal on 2006-08-31
Well I have my buttons back in XGL/Compiz.

To solve the problem I followed [this method]("http://ubuntuforums.org/showthread.php?t=245152") (both steps). Hope it helps...

- trib'

---

### Post by zas on 2006-08-31
I think [this]("http://www.ubuntuforums.org/showpost.php?p=1238311&postcount=12") post is what Gobien was referring to.  And more specifically was the link to this page - [How to shutdown, restart or logoff gnome via command/Launcher]("http://www.cyberciti.biz/nixcraft/vivek/blogger/2005/07/linux-desktop-how-to-shutdown-restart.html").

Works great for me-I now have a one click reboot launcher in place of the quit button on my panel (I don't really need the logout or shutdown buttons myself).  One thing I noticed is that the command he uses - "#visudo" - doesn't work for me. But "sudo visudo" works fine.

---

### Post by tribaal on 2006-09-01
Well from what I gathered form the link I submitted in my last post, the problem comes from the way we installed XGL:

When the system boots, it starts an Xorg server as usual, and then when we tell him to lauch an XGL session, the XGL server is just masking the Xorg server running in the background.

I guess only the default server has rights to commands like shutdown?

So by following the method I posted abouve you can solve the problem by making XGL you default server. :)

The only issue with this is that it makes you system boot slower (about +20 seconds... :( Yep, it's still alpha).

- trib'

---

### Post by jharris on 2006-09-01
Thanks tribaal,
I think what you have suggested is the most plausible explanation as to what has happened with the buttons dialogue. I'll modify my server list, make XGL the default setting and see what transpires.

-J

---

### Post by Shaamaan on 2006-09-05
After setting XGL as a default server...

It boots nicely, but I've got trouble starting compiz. :(

It says that a window decorator is already in place.... hold on, let me restart this thing and I'll tell you exactly.

---

