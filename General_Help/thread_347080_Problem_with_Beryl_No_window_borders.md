---
title: "Problem with Beryl: No window borders"
date: 2007-01-26
forum: General Help
---

### Post by Vord on 2007-01-26
I just updated my nvidia drivers to 9746, and had Beryl installed beforehand. I went into synaptic and removed the beryl entries before installing the drivers. After I finished installation, I went through the steps to install beryl again, but when I started beryl-manager, my settings were all still intact, but when I switched to the Beryl window manager, I had no window borders, whatsoever.

As to what I've tried so far, I've removed the repository and replaced it, purged the packages through aptitude and synaptic, and gone through the install process several times over, but I just cannot get beryl to install fresh, or fix this problem.

---

### Post by floke on 2007-01-26
When you run Beryl - when you click on the diamond icon - when you click on the seledct window manager and select window decorator - they are both selected as Beryl?

I only ask since I had these problems earlier today and it turned out that, for some reason, these variables had changed.

---

### Post by kilou on 2007-01-26
try to add **emerald --replace** as a startup program in System-Preferences-Session-Startup and log out/in again. Not sure this will work but this did the trick for me. However I don't get this problem anymore with Beryl 0.1.5 (svn repos).

---

### Post by Vord on 2007-01-26
I just got this as an output when manually starting Beryl-manager

```
(emerald:9002): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine"

```

Any ideas?

---

### Post by floke on 2007-01-26
Can you get into Emerald Manager at all? If you can you might be able to select a theme that doesn't use murrine and = get Beryl running again?

I was getting strange error messages from the terminal telling me I had no 3D etc. even though Compiz would run fine - it turned out I hadn't actually told Beryl manager to use Beryl window manager.

---

### Post by KyPeN on 2007-01-26
> **Vord said:**
> I just updated my nvidia drivers to 9746, and had Beryl installed beforehand. I went into synaptic and removed the beryl entries before installing the drivers. After I finished installation, I went through the steps to install beryl again, but when I started beryl-manager, my settings were all still intact, but when I switched to the Beryl window manager, I had no window borders, whatsoever.

As to what I've tried so far, I've removed the repository and replaced it, purged the packages through aptitude and synaptic, and gone through the install process several times over, but I just cannot get beryl to install fresh, or fix this problem.

You have to set your preferred color depth to 24-bit and add the line:

Option "AddARGBGLXVisuals"

to your xorg.conf.

---

### Post by Nikron on 2007-01-26
> **KyPeN said:**
> You have to set your preferred color depth to 24-bit and add the line:

Option "AddARGBGLXVisuals"

to your xorg.conf.

How do you set the color depth?

---

### Post by Trurl on 2007-02-01
I've got the same problem. Whenever Beryl is loaded, the window borders vanish. 


I've done the fix for depth and visuals in the screen section of xorg.conf, so I'm not sure what might be the problem. 

I've also tried emerald --replace, as suggested earlier. 

Edit: I just tried all the fixes suggested at Beryl-project and none of them made a difference (n.b. removing Load "dri" crashed  X)

Any ideas would be appreciated!

---

### Post by phang on 2007-02-02
I had GTK 1.2 themes running, and it wouldn't work unless I had XLIB_SKIP_ARGB_VISUALS=1 in the environment. You should check for that ```
env | grep XLIB_SKIP_ARGB_VISUALS
``` I just got my window decorators back by removing it from my ~/.bashrc and ~/.gnomerc. 

I hope this helps. By the way, I found this on the Arch Linux Beryl Wiki: [http://wiki.archlinux.org/index.php/Beryl#Window_Decorations_Disappear](http://wiki.archlinux.org/index.php/Beryl#Window_Decorations_Disappear)

---

