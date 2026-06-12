---
title: "Xubuntu crashes after booting"
date: 2007-01-03
forum: General Help
---

### Post by blueyelabs on 2007-01-03
I have a huge problem with Xubuntu, it won't boot properly; I get to the login screen, and if I'm not fast enough to login, it crashes, and then if I manage to login, it crashes at the splash screen! ](*,)  :mad:  :-k  :evil: 
Ok: a history:
I was trying to revive my old computer, with a combo of win98 and Linux.
(Win98 cos my sister wanted to play older games on it!)
I installed windows, and got the usual frustration setting it up, but it worked pretty darn well in the end.
I then installed Ubuntu, which I ditched, because it was too slow for this machine, and used Xubuntu which also worked really well.
So then Xubuntu wouldn't work with wireless internet, so after much frustration, I finally managed to get ndiswrapper, and had hooked it up to a wired network to get internet (so I could get ndiswrapper) anyway, I also tried to get hold of the nvidia drivers for the Linux kernel, which I did following the instructions here: [http://www.ubuntuforums.org/showthread.php?t=263851&highlight=nvidia+geforce+4](http://www.ubuntuforums.org/showthread.php?t=263851&highlight=nvidia+geforce+4)
now this may have been the wrong thing to do, I don't know, I am completely (well not COPMLETELY) new to Linux, but anyway, rebooted and this crash thing happened.
Recovery mode also crashes, but only affter a while, so I managed to uninstall the nvidia driver to see if that worked, but then I have no video driver or something... damn, and now I have been quite unable to do anything with Xubuntu...
Any help would be much appreciated... oh and here are the specs:
AMD K6 400MHz
256MB Ram
Nvidia GeForce 4400 (i think - I'm not sure how to check)
Thank you again (in advance - there's a prompt for ya!:p )

---

### Post by goatflyer on 2007-01-04
After uninstalling the nvidia driver, try

sudo dpkg-reconfigure xserver-xorg

to get the standard video settings back for your hardware.  It will take you through a lot of questions about your hardware, and offer default choices that work well.

---

### Post by blueyelabs on 2007-01-04
it didn't work, now it just tells me that my xserver no longer works because its not configured properly, but I'm sure I got it right, I don't really want to have to reinstall xubuntu but I probs will have to... I wouldn't mind an alternative, I mean, the kernel still crashes without the Nvidia drivers, is there any way of repairing the original installation...?

---

### Post by goatflyer on 2007-01-04
You say your kernel crashes even if nvidia driver isn't loaded?!?

Can you boot into recovery mode (its just text, no X server)?  Is it stable?
If not stable at this point you are better off reinstalling.

If recovery mode seems stable (and you want to try to fix your normal boot),  take a peek at:

```

cd /etc/X11
ls -l xorg.conf*

```

this will show all versions of your previous (working?) xorg.conf files.

Since you don't trust your current xorg.conf there's no sense in keeping it.  To overwrite it with some previous version type:
```

cp xorg.conf.ssssss xorg.conf

```

(replace the ssssss to whatever suffix the file you want to try has)
Then reboot and see if it comes up normally.

Keep trying progressively older versions until you find one that works, or until you give up and reinstall.

---

### Post by blueyelabs on 2007-01-04
ok - well, I got it to semi work by doing this in recover mode (working quickly to avoid it crashing, which even recovery mode does after a while...:
```
sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-xconfig
```

however, what now happens is that I can login for a while (it changes) but eventually it always crashes, even in failsafe (well, it won't start failsafe Gnome so...)

I actually thought I'd fixed it, but no such luck, I'll try this:
> **goatflyer said:**
> If recovery mode seems stable (and you want to try to fix your normal boot),  take a peek at:

```

cd /etc/X11
ls -l xorg.conf*

```

this will show all versions of your previous (working?) xorg.conf files.

Since you don't trust your current xorg.conf there's no sense in keeping it.  To overwrite it with some previous version type:
```

cp xorg.conf.ssssss xorg.conf

```

(replace the ssssss to whatever suffix the file you want to try has)
Then reboot and see if it comes up normally.

Keep trying progressively older versions until you find one that works, or until you give up and reinstall.
otherwise I'll reinstall
:( 
I'm confuzzled

---

### Post by blueyelabs on 2007-01-04
> **goatflyer said:**
> You say your kernel crashes even if nvidia driver isn't loaded?!?

Can you boot into recovery mode (its just text, no X server)?  Is it stable?
If not stable at this point you are better off reinstalling.

If recovery mode seems stable (and you want to try to fix your normal boot),  take a peek at:

```

cd /etc/X11
ls -l xorg.conf*

```

this will show all versions of your previous (working?) xorg.conf files.

Since you don't trust your current xorg.conf there's no sense in keeping it.  To overwrite it with some previous version type:
```

cp xorg.conf.ssssss xorg.conf

```

(replace the ssssss to whatever suffix the file you want to try has)
Then reboot and see if it comes up normally.

Keep trying progressively older versions until you find one that works, or until you give up and reinstall.
there's no early enough version of the xorg.config file, since this all went wrong yesterday night, and the only ones are from today... :(
I guess I'll just reinstall...
is there any other way... PLEASE?

---

### Post by blueyelabs on 2007-01-04
But if I do reinstall, I'll have the same problems no? Either no nVidia driver, or a rubbished system, not that the driver made much difference, although it just so happened at the time that I installed ndiswrapper aswell, with the drivers for my wg111v2 usb key thing... i don't know which might be causing the problems, maybe if i uninstall ndis wrapper and try again?
I'll try that and post results, if any...:-k

---

### Post by blueyelabs on 2007-01-04
well - uninstalling ndiswrapper did absoloutely nothing, although for some obscure reason, ndiswrapper wouldn't uninstall the driver i installed with it, it said it didn't exist, but then, if I tried to install it, it said it already existed, in the list it said > installed drivers: driver invalid driver!" or something similar...
oh well, ndiswrapper is gone, and still it crashes, once on firefox, once on synaptic... hmm... stuck, badly...
I think I'll now reinstall, and install ndiswrapper, but not the nvidia drivers, they've done too much to the last stretch of hols already... :(

---

### Post by blueyelabs on 2007-01-07
I discovered the problem to be in updating edgy... I think the X update is what crashes it
I've now reinstalled twice, and this time, I haven't updated and everything looks fine!

---

