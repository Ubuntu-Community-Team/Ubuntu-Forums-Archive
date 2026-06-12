---
title: "Kubuntu usplash problem"
date: 2007-01-04
forum: General Help
---

### Post by Rab22 on 2007-01-04
Okay, as I have dug deeper and deeper into my problem, I've decided to make it a new thread instead of taking over someone else's thread.

This is the thread I originally posted on, 

[http://ubuntuforums.org/showthread.php?t=331287](http://ubuntuforums.org/showthread.php?t=331287)

Basically, my problem is this. A couple weeks ago I installed Xubuntu and Kubuntu without any problems. I've never used Xfce and it's been a long time since I've used KDE, so I thought I'd take a look at what improvements have been made (although doesn't deal with the topic, I must say, they have a very nice look 'n feel to 'em!). Doing so changed my usplash to Kubuntu, which at the time didn't really bother me since I was using KDE. However, being the faithful GNOME follower I am, I decided to switch back. This is where the problems began.

I've known about the "update-alternatives" command, and used that to change the usplash screen. Given that I don't reboot too often, I assumed it worked and had no need to worry. I just installed some updates which required a reboot and oddly enough the Kubuntu splash came up again. Figuring I did something wrong, I went back and checked it. Nope, it was set to 'manual' with 'usplash-theme-ubuntu' properly set. So, I figured it was a fluke and restarted again to see. The shutdown screen showed the Ubuntu splash properly, but not the start up; once again it was Kubuntu.

Here is a screenshot of update-alternative for usplash-artwork.so
[IMG]http://www.rab22.ws/images/misc/console1.png[/IMG] 

So, as I posted on the other thread, I figured a quick resolution was to remove the kubuntu splash from the alternative's list and install it again with the same priority (I assumed the priority was the issue). Restarted and yet again, Kubuntu splash came up again.

Next, I decided to remove it completely from the alternatives list, restart, and yet again it came up.

[IMG]http://www.rab22.ws/images/misc/console2.png[/IMG]

Finally, being irritated by it, I decided to remove the kubuntu-artwork-usplash package (which required kubuntu-desktop to be removed too). After doing that I restarted, and **YET AGAIN** the kubuntu usplash comes up.

I don't know enough about splashes to really diagnosis this problem any further. It's not really all that big of a problem, just very annoying and frustrating since it should be a relatively easy thing to configure (the whole point of the alternatives list). 

Anyways, I would really appreciate any ideas/help on this. If you need any further info, let me know.

Thanks,

-Rab22

---

### Post by robgill on 2007-01-04
You seem to know more about it than I do, but try this...

[http://doc.gwos.org/index.php/Change_Usplash](http://doc.gwos.org/index.php/Change_Usplash)

---

### Post by Rab22 on 2007-01-05
> **robgill said:**
> You seem to know more about it than I do, but try this...

[http://doc.gwos.org/index.php/Change_Usplash](http://doc.gwos.org/index.php/Change_Usplash)


Well it appears that this command,

```
sudo dpkg-reconfigure linux-image-$(uname -r)
```

worked. It rebuilt the kernel image (which makes sense I guess). 

I'm debating about reinstalling kubuntu-desktop, selecting the other splash, and running this command to see if it works then as well.

Thanks for the info!

-Rab22

---

### Post by ricardovich on 2007-01-12
I had the same problem after a quick flirtation with kubuntu. Thanks for the quick fix.

---

