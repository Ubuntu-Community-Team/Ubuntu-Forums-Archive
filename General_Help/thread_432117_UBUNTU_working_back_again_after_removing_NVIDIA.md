---
title: "UBUNTU working back again after removing NVIDIA"
date: 2007-05-03
forum: General Help
---

### Post by mishranurag on 2007-05-03
As I mentioned in some of my posts, that my UBUNTU was not working at all. It would hang anytime or not even boot. I tried updating the computer through recovery mode and then rebooted it to no avail. Finally, I ditched nvidia today and computer is working perfectly fine.

My video card is NV18 [GeForce4 MX 440 AGP 8x] and I used to use nvidia-glx.

Anurag

---

### Post by DemonicKyle on 2007-05-03
I have the exact same card as you.

Yesterday I decided to try to upgrade my Nvidia drivers.

And now...total chaos.  I used Envy to try to upgrade, and then X wouldn't start (saying that there was an API mismatch between X server and client).  Finally, after a few hours of reading these forums and fiddling, I got X to start.  But after I'd boot into GNOME, I'd get a blank white screen.  Guessing Compiz was at fault, I removed it....but then I had no Window Manager.

And just half an hour ago, I started mucking about in my xorg.conf.  And now X won't start again.  I'm absolutely fried.

1)  What did YOU do to recover?
2)  In the event that I've totally boned my machine, what's the best way to recover?  Reinstall Feisty?

Any help would be appreciated.  I'd post my xorg.conf, but I'm on a library computer right now.  :(

Cheers,

-DK

---

### Post by mishranurag on 2007-05-03
Boot into recovery mode.

Type 
apt-get remove nvidia*
then
dpkg-reconfigure xserver-xorg
(Walk through the directions, to set up your monitor, you can accept default options for most)
type 
reboot

Let me know if it works or doesn't work.

As far as totally boning up the machine, you can reinstall Fiesty, but that is not required in this case at all.  When you will reconfigure xserver-xorg, your xorg.conf will be set up again.

Anurag

---

### Post by DemonicKyle on 2007-05-03
Ok, did as you said - now X Crashes and gives me the following error message:

"libGL.so.1 cannot open shared object file:  no such file or directory"

Thoughts?

Thanks,

-DK

---

### Post by dagrump on 2007-05-03
Yeah, great that lets you use your browser, but you can't do the things you spent your money for hardware on.  NO DRIVERS, WTF, This means no screen savers, no games, no virtualbox, NO this is getting flat out stupid. The biggest issue is NONE of the people that could fix this or lead the great unwashed from this messed up can of worms give a rat a$$. Yeah my machine no longer seems to crash if I leave it a crippled P.O.S.  Wow I'LL sleep well now, that my most powerful box needs a walker to get to the can. This machine was able to run doom3, quake4, virtualbox, & various other programs & now It is useless. Well, I feel a little better, I'd rather not have this damaged pile of goo though. But since my back up info was after they crippled it. I can't believe they haven't fixed this yet, can't blame it on nvidia, cause I was using the nvidia drivers all along. It was a kernel update, I'd bet on it.

---

### Post by mishranurag on 2007-05-03
Hey DK,

When you reconfigure xserver-xorg, which driver you use? I used nv for mine!

---

### Post by mishranurag on 2007-05-03
I can feel your pain dude. I am surprised no updates has been issued on this issue yet.  This is plain absurd. Is this the fiesty they are banking on that they are promising to sell it with DELL?

---

### Post by DemonicKyle on 2007-05-03
Yeah, I used nv.

:(  Surfing using Elinks is...balls.

-DK

---

### Post by dagrump on 2007-05-03
Kind of like anything else a fish rots from its head down, when management loses sight of the goal, it's all downhill from there. Dell must plan on using intel or ati so the paid folks don't care about the people that started using it when it was some damn obscure disto, struggling to find users. Well now it's big time so who cares, we're going to get a mainstream distributor to pre-load it we don't care about the great unwashed anymore WE'RE going big time. I've ran this since 5.1 & always had good luck getting things to work. This box started up in late sept. 06 from a daily build that could deal w/ jmicron chipsets, it was stable till late feb. 07 or early march, then it started locking up. It isn't like it's not a problem, how many people suffered from this & said screw it I'm going back to winblows. I won't quit w/o a fight but this is really starting to grate on me. If things don't get straightened out this will rear up & bite them in the butt.

---

### Post by DemonicKyle on 2007-05-04
Bump!

---

### Post by mishranurag on 2007-05-16
I installed NVIDIA back again and the system is working fine! No hangs.

---

### Post by rpseng on 2007-05-24
> **mishranurag said:**
> I installed NVIDIA back again and the system is working fine! No hangs.

Dear mishranurag/all,

I also have a NV18 [GeForce4 MX 4000 AGP] but no look with nvidia drivers on feisty. It was working fine on edgy!

I have already tried several methods (nvidia-glx, envy, manual compilation, etc...)

If I use 'nvidia' instead of 'nv' my system hangs when I run any glx program, for instance it hangs if I start 'glxgears'

Any advices?

---

### Post by mishranurag on 2007-06-01
I would suggest you to remove Nvidia and use the system with nv, and then update your system. After you update the system, try installing NVIDIA again.

Good Luck.
Anurag

---

### Post by Bloch on 2007-06-01
I just found this thread. It's good to know I'm not alone!

After the update to kernel 20-16 xorg failed to start - the drivers didn't work. I uninstalled them, did the 
sudo dpkg-reconfigure xserver-xorg
to create a new xorg.conf file and then it worked fine.

BUT no glx - no google earth, no fun, and crappy 2D performance.

I reinstalled the NVIDIA drivers using Envy. When I rebooted the error message is:
```
Error: API mismatch: the NVIDIA kernel module has the version 1.0-7184 but this X module has the version 1.0-9631. Please make sure that the kernel module and all NVIDIA driver components have the same version.

```

The same happened when I uninstalled and reinstalled with automatix.

It seems the new kernel does not play well with the NVIDIA drivers, at least for some types of NVIDIA graphics cards.

Does anyone know if this is a recognised bug? Anyone shed any light on this?

---

### Post by confused57 on 2007-06-01
There's an excellent discussion in this thread with the recent kernel update & nvidia drivers:
[http://ubuntuforums.org/showthread.php?t=456662&page=43](http://ubuntuforums.org/showthread.php?t=456662&page=43)

---

### Post by rpseng on 2007-06-02
I have a NV18 on a ASUS K8V-X SE

I reported my problem to NVIDIA and they suggested to update my motherboard bios, but that didn't the trick.
They also suggested to use the following option in my device section

```

Option         "NvAGP" "0"

```

This disables the AGP function of the card, and solved the problem for me!
They told me that can be a bug with my ASUS motherboard related to AGP support.

---

### Post by sibot on 2007-06-02
I'm having major issues with my Ubuntu Fiesty Fawn, I installed nvidia-glx drivers from restricted driver manager for my Nvidia 6200 PCI-E, and somehow my system freezes completely. Without reason, it'll work for something and then all of a sudden it would freeze. Can you guys help me out with this? Its really bugging when your system crashes every second. 

Oh btw, are official Nvidia drivers better? The ones available on their website?

Thanks

---

### Post by Ocxic on 2007-06-02
i ussually get the API mismatch error when the linux-restriced modules are installed with ubuntu nvidia driver, then try to install nvidia propitary driver, the two don't jive, try removeing all the ubuntu nvidia drivers, and restriced modules, along with nvidia's propetary drivers, and try again...

on a side note.... i used evny and it even seem to take care of kernel upgrade with the propetary driver
unless i missed something

---

