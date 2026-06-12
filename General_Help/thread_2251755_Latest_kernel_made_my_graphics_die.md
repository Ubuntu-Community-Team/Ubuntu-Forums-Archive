---
title: "Latest kernel made my graphics die"
date: 2014-11-06
forum: General Help
---

### Post by Joel_Hinz on 2014-11-06
I updated the system yesterday, ran apt-get autoremove, and turned the computer off. Today, when I started the computer, all I got is a blank screen with a mouse pointer. I can get into a terminal through ctrl-alt-f1, however.

After updating and rebooting again, I assumed it was an error with Nvidia's proprietary drivers, so I reverted back to the defaults. That didn't help either, so I downloaded the newest version of them using wget and reinstalled them. That kind of helped - I can now boot into the desktop, with both monitors working at intended resolution.

However, now I don't get any window management: there's no status bar, no launcher, I can't use shortcuts such as ctrl-alt-t or alt-tab. That means I am limited to my desktop. If I open a folder in my desktop, it's opened in the explorer (Nautilus? the default one), but without a window status bar. The same goes if I open e.g. a txt file with Sublime.

I don't know how to reinstall Gnome + Unity - or if that even is a good idea. Some people had a similar or even the same problem [here]("http://ubuntuforums.org/showthread.php?t=2241869&page=8"), but since I used autoremove I can only access the two latest kernels, and neither work. I'm currently running 3.16.0-24, and I also have -23 installed.

Any help would be greatly appreciated!

---

### Post by Pilot6 on 2014-11-06
Your mistake was to install drivers from a downloaded file. Install drives from Ubuntu repository.

sudo apt-get install nvidia-318

or whatever version there is. Then they won't stop working after kernel update.

To get system working properly you can remove hidden .compiz folder and reboot.

---

### Post by Joel_Hinz on 2014-11-06
I'm not too fond of that option... the repository drivers don't work nearly as well in games for me, and they don't support dual monitors in 2560x1440.

Having said that, I'm getting kinda desperate, and I appreciate the advice. :) So I've tried now to use the repository drivers, and unfortunately they work even less well - I can't get any graphics at all using them. :( Reinstalled proprietary and graphics are back again.

So I'm thinking maybe it isn't a graphics issue after all? I mean, the proprietary drivers got the graphics working again, perhaps the update borked both graphics *and* Unity, and I've managed to fix only the first? I've tried to uninstall the compiz-config settings manager in case that was the problem - no dice.

---

### Post by Pilot6 on 2014-11-06
If you need latest drivers, then you can use xorg-edgers repository

```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt get update
sudo apt get install nvidia-340 or nvidia-343
sudo add-apt-repository -r ppa:xorg-edgers/ppa
```The last command removes the repository in order not to install unstable packages besides the drivers.

Uninstalling ccsm does nothing, because it is just a tool.

---

### Post by grahammechanical on 2014-11-06
> [COLOR=#000000]I don't get any window management: there's no status bar, no launcher, [/COLOR]

You do not say what version of Ubuntu you are using. So, I am assuming it is Ubuntu 14.04 + Unity and not one of the flavours. This will reset Compiz

```
dconf reset -f /org/compiz/
```

this will restart Unity

```
setsid unity
```

They might solve the problem.

Regards.

---

### Post by Joel_Hinz on 2014-11-06
Thanks for your help. I appreciate the answers!

@Pilot6: I tried that but that somehow managed to make the issue even worse than no graphics at all... :) Had to boot into the safe mode terminal to get it back again, hehe.

@grahammechanical: My apologies, I intended to mention but forgot; I'm running 14.10 as you surmised. Resetting Compiz didn't work, however it got me on the right track. Since the graphics minus Unity were working again, I reinstalled CCSM and created a launcher for it through the terminal. There, all kinds of settings were in need of fixing. Above all, the Ubuntu Unity Plugin was disabled... no wonder it wasn't working! I still have a lot of tweaking to do, but that I can handle. Thanks again!

---

