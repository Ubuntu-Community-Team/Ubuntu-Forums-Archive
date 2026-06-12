---
title: "Intel Driver problem - No more 3D acceleration !"
date: 2013-04-20
forum: General Help
---

### Post by GameX2 on 2013-04-20
EDIT: I got it! :O
I had the exact same problem.  Altought I remember reinstalling Xorg, I probably forgot to reconfigure it (Didn't knew how).

[http://askubuntu.com/questions/86465/switch-from-nvidia-to-internal-intel-hd-graphics-opengl-does-not-work](http://askubuntu.com/questions/86465/switch-from-nvidia-to-internal-intel-hd-graphics-opengl-does-not-work)

Hi,

I have removed the experimental NVidia driver I installed on my laptop.  It seem to have succeeded.  Plymouth used to flicker a little with the NVidia driver, now that it's uninstalled, it does not flicker anymore.

But now, my Intel driver is not working as it should. :( 
Running this probably uninstalled a lot of dependencies:

```
sudo ppa-purge ppa:glasen/intel-driver
```

It ended up with a black screen, and I had to boot from a LiveCD, use chroot, to install the package "xserver-xorg-video-intel".  That fixed the black, I can login, but only in Unity 2D.  I have no more 3D acceleration!
How do I re-enable it ?

Here's the output of the command " lspci | grep VGA " :


```
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
```

Also, the graphic cards is not found.  It should be mentionned, but the line is just blank.
[http://i.imgur.com/CUwXgNP.png[COLOR=#FFFFFF ! important][FONT=arial]**377**[/FONT][/COLOR]]("http://i.imgur.com/CUwXgNP.png")

Installing " mesa-utils " didn't help.


Please help. :(  I have no clue of what to do next.

Thank you very much!

---

