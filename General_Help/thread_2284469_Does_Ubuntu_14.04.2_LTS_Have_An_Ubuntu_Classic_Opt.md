---
title: "Does Ubuntu 14.04.2 LTS Have An Ubuntu Classic Option?"
date: 2015-06-29
forum: General Help
---

### Post by coljohnhannibalsmith on 2015-06-29
Hello,

I just bought a used Dell Inspiron at a pawnshop, and built a dual boot Windows 7 & Ubuntu 14.04.2 LTS system on it.  I have noticed that there does not appear to be an Ubuntu Classic/Gnome Desktop option.  Is this true or is it hidden somewhere?  Also, the Workspace Switcher does not appear to allow any customization.  I would really like to have the Desktop Cube back.  Can I still install Compiz Config Manager, which adds 3D graphics capabilities?  Since there is no Synaptic Package Manager, how do I access the repositories?  GPartEd has been removed from the Live-CD, so I can't edit partitions except during install so, I guess I'll have to download Knopix for this.

Any help appreciated

Thanks, Hanniball

---

### Post by TheFu on 2015-06-29
Been awhile, huh?

Use apt-get to install synaptic ... or start using "software center."

From the liveCD, you can install gparted.  **sudo apt-get install gparted**.

You can also install a multitude of different DEs - just be aware that some DEs will write incompatible settings to the same config file, causing issues.  Best to create new userids for each DE you play with, until you find the one you like best.  gnome3, lxde, xfce4, and there are probably 5 others to pick from. cinnamon ... kde and a few others.  I like fvwm-crystal, but I'm old-school.

Sorry - cannot help with 3D accel stuff - I generally run desktops inside a VM and any heavy graphics just don't work that way - pretty much don't work at all.

---

### Post by ajgreeny on 2015-06-29
**gparted** is still available by default in all the live *ubuntu systems as far as I'm aware, so no need to download anything new to be able to use that.

14.04 does not have the classic gnome-2 style DE by default when installed but you can easily add it with command ```
sudo apt-get install gnome-panel
```It will bring in several dependencies and it does not work exactly like gnome-2, though it looks like it, or can be made to do so easily enough.

If it is simply that layout style that you like you can also get that using DEs such as xfce, mate (which is a fork of gnome-2), cinamon and probably others that I don't really know well enough.

I'm not sure about compiz any more as I haven't used it since 10.04, but I gather from what I've read that the cube is not as easy to deal with as it used to be; I might be wrong about this so search for more on compiz before you jump into doing things that may break your system.

---

### Post by CantankRus on 2015-06-29
Compiz is already installed because unity is a compiz plugin.
Many of the old compiz plugins you'll find in the unsupported package compiz-plugins.

The cube still works after installing compiz-plugins and enabling using ccsm.
```
sudo apt-get install compiz-plugins compizconfig-settings-manager
```

P.S. according to the ubuntu-14.04.2 manifest, gparted is included in the iso.

---

### Post by grahammechanical on 2015-06-29
Excuse me but it is my understanding that from 14.04 onward we install gnome-session-flashback. It is in the Software Center. We get 2 extra login sessions - Gnome Flashback (Compiz) and Gnome Flashback (Metacity).

It replaces the Gnome Fallback of 12.04. There is one thing that we need to be careful about. Gnome Classic is a Gnome 3 Shell extension. Install Gnome Classic on Ubuntu and we end up with Gnome 3 shell as well. Which would be more than I would bargain for. Unless I was using Ubuntu Gnome. Then it would be a different matter.

[https://wiki.gnome.org/Projects/GnomeFlashback](https://wiki.gnome.org/Projects/GnomeFlashback)

Regards.

---

### Post by CantankRus on 2015-06-29
> **grahammechanical said:**
> Excuse me but it is my understanding that from 14.04 onward we install gnome-session-flashback. It is in the Software Center. We get 2 extra login sessions - Gnome Flashback (Compiz) and Gnome Flashback (Metacity).

It replaces the Gnome Fallback of 12.04. There is one thing that we need to be careful about. Gnome Classic is a Gnome 3 Shell extension. Install Gnome Classic on Ubuntu and we end up with Gnome 3 shell as well. Which would be more than I would bargain for. Unless I was using Ubuntu Gnome. Then it would be a different matter.

[https://wiki.gnome.org/Projects/GnomeFlashback](https://wiki.gnome.org/Projects/GnomeFlashback)

Regards.
Installing **gnome-panel** as ***ajgreeny*** said is virtually the same as installing **gnome-session-flashback** 
because ubuntu regards recommended packages as dependencies and so pulls in gnome-session-flashback.

As for the compiz cube you can use it in the **Gnome Flashback(compiz)** session and/or the **Ubuntu** session.

---

### Post by yetimon_64 on 2015-06-29
> **ajgreeny said:**
> **...**but I gather from what I've read that the cube is not as easy to deal with as it used to be; I might be wrong about this so search for more on compiz before you jump into doing things that may break your system.

You're pretty much right about the cube, when first enabled here it caused a lot of crashes. It is extremely finicky to get stable, you need to be EXTREMELY careful in what combination of plugins that get enabled in ccsm. It regularly sent me back to a stock unity set up and was very frustrating to get going. Once a stable combination of plugins are found then it works OK, with only an occasional crash. 

14.04 Ubuntu (Unity) seems very touchy here where the cube is concerned, I suspect it would perform better without the Unity plugin as is the case in the fallback session, though I don't have fallback installed on this set up to test such. Though one improvement is what happens when a crash occurs; It seems that unity now resets itself more automatically than it used to in, say 11.04, but the constant resets may disturb/annoy some users.It does require quite a bit of perseverance to get a stable enough combination to work with.

---

### Post by coljohnhannibalsmith on 2015-06-30
> **yetimon_64 said:**
> You're pretty much right about the cube, when first enabled here it caused a lot of crashes. It is extremely finicky to get stable, you need to be EXTREMELY careful in what combination of plugins that get enabled in ccsm. It regularly sent me back to a stock unity set up and was very frustrating to get going. Once a stable combination of plugins are found then it works OK, with only an occasional crash. 

14.04 Ubuntu (Unity) seems very touchy here where the cube is concerned, I suspect it would perform better without the Unity plugin as is the case in the fallback session, though I don't have fallback installed on this set up to test such. Though one improvement is what happens when a crash occurs; It seems that unity now resets itself more automatically than it used to in, say 11.04, but the constant resets may disturb/annoy some users.It does require quite a bit of perseverance to get a stable enough combination to work with.

I've got everything installed and booted into Flashback (Compiz).  I was able to get the Desktop Cube stable in 12.04 with this combination of settings:

CCSM General: Desktop Size:
Horizontal Virtual Size: 4
Vertical Virtual Size: 1
Number of Desktops: 1  (Missing in 14.04)

Desktop Icons: Preferences:
Switcher:
Show all Workspaces in 1 row.
Workspaces:
Number of Workspaces 1.

In the lower right-hand corner of the Desktop, I have 1 row with 4 Desktop icons; however, they all say "Workspace 1" and the cube will not rotate.  Do I have to take some extra step like enabling 3D graphics, or something else?

BTW, this is an older Dell Inspiron with a dual core Pentium T4400.  I'm not sure if this chipset is capable of 3D.

Thanks, Hannibal

---

### Post by yetimon_64 on 2015-06-30
> ..and the cube will not rotate. Using "ccsm" check to see if the "rotate cube" and "viewport switcher" plugins are active (checked). 

I think you'll need both working to actually rotate the cube from the panel applet you describe at the "lower right-hand corner of the Desktop". I assume that is the gnome panel based viewport switcher, if so, to change its titles right click (you may need to press another key with the right click as well, I think the "alt" key as well, from memory) to get the context menu for the gnome panel applet. You may be able to rename or remove the names "workspace 1" from that menu (if you can work out how to get it to show up ... ;)).

---

### Post by CantankRus on 2015-06-30
When in the flashback compiz session leave the panel workspace switcher applet set to one workspace.
Just use ccsm to change the horizontal and vertical virtual size and the switcher will display accordingly.

P.S. In this session, to interact with the panel you need to  alt+Super+Right-mouse on it.

---

### Post by coljohnhannibalsmith on 2015-07-01
> **yetimon_64 said:**
> Using "ccsm" check to see if the "rotate cube" and "viewport switcher" plugins are active (checked). 
if so, to change its titles right click (you may need to press another key with the right click as well, I think the "alt" key as well, from memory) to get the context menu for the gnome panel applet. You may be able to rename or remove the names "workspace 1" from that menu (if you can work out how to get it to show up ... ;)).

Ok, did everything here.  Alt+Right gave me the context menu with the following options:
Always on top.
Always on visible workspace.
*Only on this workspace.
Move to workspace right.
Move to another workspace > 
     Move to workspace 1 (grey)
     Move to workspace 2
     Move to workspace 3
     Move to workspace 4
None of 2,3, & 4 work.

I was not able to rename the workspaces.

BTW, the unit is a Dell Inspiron 1545 & it does have graphics acceleration & 3D built in.

Thanks, Hannibal

P.S.,  ContankRus thanks for the tip about Alt+Super+Right. I didn't know this.

---

### Post by CantankRus on 2015-07-01
The menu items to move to a specific workspace number don't work with compiz because 
you really only have 1 workspace no matter how many virtual desktops you create.

Set up your own shortcuts in the ccsm rotate cube plugin or in keyboard shortcuts.

---

### Post by mattharris4 on 2015-07-03
> **grahammechanical said:**
> Excuse me but it is my understanding that from 14.04 onward we install gnome-session-flashback. It is in the Software Center. We get 2 extra login sessions - Gnome Flashback (Compiz) and Gnome Flashback (Metacity).

It replaces the Gnome Fallback of 12.04. There is one thing that we need to be careful about. Gnome Classic is a Gnome 3 Shell extension. Install Gnome Classic on Ubuntu and we end up with Gnome 3 shell as well. Which would be more than I would bargain for. Unless I was using Ubuntu Gnome. Then it would be a different matter.

[https://wiki.gnome.org/Projects/GnomeFlashback](https://wiki.gnome.org/Projects/GnomeFlashback)

Regards.

This is also what Edubuntu 14.04 had when I installed it -- Unity, Gnome Compiz and Gnome Metacity.  I was able to switch between them at the login screen, there was a circle to click at the left side of the bar above the login prompts (name and password).  These were Gnome 2 as far as I could tell, I did not check to see if Gnome 3 was also installed but an option for it did not appear when selecting a DE.  Of the three I preferred Gnome Metacity, it was easiest to use and was less demanding on the CPU and RAM.

As posted earlier Ubuntu MATE is also an option and is reputed to be essentially Gnome 2 with some further refinement.  I haven't tried it so I cannot say whether it works as well as Gnome Classic (2).  I may install it on my replacement refurbed desktop in a couple of months (after the Win 10 update and me using it enough to feel comfortably voiding the warranty) as I am not a fan of Unity.

Whatever you do pick an LTS version if you change OS versions (14.04 in the case of the Canonical OSes and also 12.04 for Ubuntu-Unity).

---

