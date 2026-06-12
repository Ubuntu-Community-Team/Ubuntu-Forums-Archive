---
title: "Minimal xfce 16.04 install problem"
date: 2018-02-24
forum: General Help
---

### Post by Chris1965 on 2018-02-24
Everything is going well with new install besides for one problem. Programs such as synaptic, firewall (gufw), gparted, lightdm greeter settings won't work from menu and additional drivers loads but won't change driver. If I use gksu on the program names they work but I don't know the specific program for additional drivers to see if it will work or not. Other past installs didn't do this which is why this one caught me off guard. Any ideas would be greatly appreciated as I don't wish to do a total new install again.

---

### Post by DuckHook on 2018-02-25
Well, each of the apps you have listed require root privileges, so I am not sure what the problem is. In 16.04, most root privilege apps are built to work with *pkexec* instead of *gksu*, but either form should still work.

*EDIT*

On second reading, I see that it is driver installation that you are specifically asking about. *apt* will install drivers just as it will install any package. Of course, this needs to be preceded with *sudo*. Perhaps you are looking for the graphical front end. I believe that this package is called: *software-properties-gtk*. But if you are doing a minimal XFCE install, do you really want this clutter?

*EDIT*

After mulling over the matter further, perhaps you are not looking for minimal XFCE so much as a minimal Xubuntu desktop? I don't know how you originally installed XFCE, but if you are actually looking for the latter, then the following steps might be easier/better:

[LIST=1]
[*]Start by installing either the mini.iso or Ubuntu Server
[*]If mini.iso, then: ```
sudo tasksel
```If Ubuntu Server, then *tasksel* will automatically launch as part of the install process
[*]Choose *Xubuntu minimal installation*
[/LIST]
This will download more than the bare XFCE environment, but nowhere near the full Xubuntu desktop. The resulting install will contain most of the administrative apps and tools that you are looking for, set up *lightdm* in the way you are accustomed to and give you a bare-bones desktop with no userland apps.

I'm just guessing that this was your original intent. If I'm wrong and you really wanted just a primitive XFCE environment, then ignore the above instructions and install only *software-properties-gtk*.

---

### Post by Chris1965 on 2018-02-25
Well I already have this minimal Xfce installed including the "software-properties-gtk". What I want to know is how to fix and understand what makes a fresh install not want open programs like it should from the menu. Is there a way to reset this problem? The reason I used gksu to open is because I read in other posts that it was used to give root to gui programs. I am newer to linux so I try to trust what I read but have noticed most information posted is very old or down right false.

I have already used minimal xubuntu which installs onto a 5 gb drive, mine installs onto a 2 gb drive. My intension is to run it from an image into ram. This way I can test software from the repositories all I want, fool with the settings and all I have to do is reboot to have a clean os to work with next time.

---

### Post by Chris1965 on 2018-02-25
I have now made many attempts to create a minimal xfce and all attempts using xserver-xorg and xfce produce the same results every time. I've tried it with just the needed parts of each along with the full installs of each with the same results. It used to work with the xfce 4.10 so something has changed since the upgrade to 4.12. I really would like to know why these programs will not open without root and the xfce additional drivers won't even function after opening with root.

---

### Post by again? on 2018-02-25
You probably need an authentication agent.
Arch wiki...
[https://wiki.archlinux.org/index.php/Polkit](https://wiki.archlinux.org/index.php/Polkit)
[https://wiki.archlinux.org/index.php/Xfce](https://wiki.archlinux.org/index.php/Xfce)
> **Authentication agents**
An authentication agent is used to make the user of a session prove that the user of the session really is the user 
(by authenticating as the user) or an administrative user (by authenticating as an administrator). 
The polkit package contains a textual authentication agent called 'pkttyagent', which is used as a general fallback.

[COLOR="#B22222"]If you are using a graphical environment, make sure that a graphical authentication agent is installed and autostarted on login.[/COLOR]

Here in Xubuntu 17.10, "policykit-1-gnome" is used.
Would installing **xfce4-session** give you your required environment.

---

