---
title: "Cant Open Ati Catalyst"
date: 2007-10-22
forum: General Help
---

### Post by SupWiz17 on 2007-10-22
In gutsy I cant open the ATI catalyst. I type $ sudo aticonfig --initial into my  terminal and get Found fglrx primary device section Nothing to do, terminating. as response. Any help?

---

### Post by superyounan1 on 2007-10-22
whats your output for fglrxinfo```
fglrxinfo
```

---

### Post by SupWiz17 on 2007-10-22
> **superyounan1 said:**
> whats your output for fglrxinfo```
fglrxinfo
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400
OpenGL version string: 2.0.6473 (8.37.6)



OpenGl doesnt work for me though I cant run games like warsow. If that is any help.

---

### Post by Maestro23 on 2007-10-22
> **SupWiz17 said:**
> In gutsy I cant open the ATI catalyst. I type $ sudo aticonfig --initial into my  terminal and get Found fglrx primary device section Nothing to do, terminating. as response. Any help?

Are you trying to open the Catalyst Control Center?

---

### Post by superyounan1 on 2007-10-22
the command to launch CCC is 
```
amdccle
```

what is the terminal output for it

---

### Post by Maestro23 on 2007-10-22
> **superyounan1 said:**
> the command to launch CCC is 
```
amdccle
```

what is the terminal output for it

Also should be a Menu Item under Apps>> Accessories.  (At least on mine their is).

---

### Post by SupWiz17 on 2007-10-22
> **superyounan1 said:**
> the command to launch CCC is 
```
amdccle
```

what is the terminal output for it
when I type that command I get 

bash: amdccle: command not found

---

### Post by superyounan1 on 2007-10-22
oops, its  ```
amdcccle
``` 3 c's, not 2

you should have it, it looks like you're running the restricted driver available in the repository, I'm using the same and I have it (albeit an outdated version and feature starved version).

If you still don't have it then open synaptic and search for "xorg-driver-fglrx", it should be marked as currently installed. Click the green box and choose "Mark for re installation" , then click Apply

after all that, log out and log back in or restart, and try amdcccle again

post results

---

### Post by SupWiz17 on 2007-10-22
> **superyounan1 said:**
> oops, its  ```
amdcccle
``` 3 c's, not 2

you should have it, it looks like you're running the restricted driver available in the repository, I'm using the same and I have it (albeit an outdated version and feature starved version).

If you still don't have it then open synaptic and search for "xorg-driver-fglrx", it should be marked as currently installed. Click the green box and choose "Mark for re installation" , then click Apply

after all that, log out and log back in or restart, and try amdcccle again

post results
when i try that command i get 

Segmentation fault (core dumped)

I have no green box to click for re installation and i am worried that if I unistall it I wont have a video driver should i just un check it and then check it again.

---

### Post by superyounan1 on 2007-10-22
> **SupWiz17 said:**
> 

I have no green box to click for re installation and i am worried that if I unistall it I wont have a video driver should i just un check it and then check it again.

The green box next to it would indicate that it is currently installed. You say when you search for "xorg-driver-fglrx" in synaptic and find it, there is no option "Mark for Reinstallation" option, but there is an option "Mark for removal"?

If the box is not green that should mean that driver wasn't installed through the repository, go ahead and do it through synaptic, click it and choose "Mark for installation" 

if you uninstall it, ubuntu should revert back to the open source "ati" driver, there is little to worry about.

If at any point your GUI stops working, simply boot in Recovery mode, and at the command like type 
```
dpkg-reconfigure xserver-xorg
```
that will prompt you a series of questions then restore your display

---

### Post by SupWiz17 on 2007-10-22
> **superyounan1 said:**
> The green box next to it would indicate that it is currently installed. You say when you search for "xorg-driver-fglrx" in synaptic and find it, there is no option "Mark for Reinstallation" option, but there is an option "Mark for removal"?

If the box is not green that should mean that driver wasn't installed through the repository, go ahead and do it through synaptic, click it and choose "Mark for installation" 

if you uninstall it, ubuntu should revert back to the open source "ati" driver, there is little to worry about.

If at any point your GUI stops working, simply boot in Recovery mode, and at the command like type 
```
dpkg-reconfigure xserver-xorg
```
that will prompt you a series of questions then restore your display
Now that I look at it in synaptic I see that ATI binary X.org driver installed that supports 2D display drivers not 3D. How to I get xorg-driver.fglrx into my synaptic?

---

### Post by superyounan1 on 2007-10-23
Basically what you need is the restricted / proprietary video driver provided by AMD/ATI. There is some hostility in the open source community against such drivers because the source code for them is not made available by the vendors, however you should experience better opengl performance

Now the problem with AMD/ATI drivers is that they do not support AIGLX, which is required for desktop effects. Are you looking to have desktop effects? If so, and you want the official ATI/AMD drivers, then you will also need to install XGL-server, it is an alternative to AIGLX that will work reasonably well, but with slightly less stability and performance. In the near future however, ATI/AMD plans on releasing an update driver that will take away your need for the XGL option

There several ways you can install the restricted driver, here are two of them:

1) System > Administration > Restricted Drivers Manager
You should see an option that allows you to enable your the driver for ATI, click to enable it

if that option isn't available, try this

2) In synaptic, Settings > Repositories. Check all the repos the first (Ubuntu software) tab, these should be: main, universe, **restricted,** multiverse. Then click close, and in the main synaptic window click Reload. When all that is done, search for "fglrx" or "xorg-driver-fglrx" and mark it for installation

----------------------------------

to enable desktop effects after having installed the restricted driver, go back to synaptic and search for "xserver-xgl" and mark it for installation, hit apply. When you restart your computer, you will be able to enable desktop effects:
System > Preferences > Appearance > "Visual Effects" tab . and choose the setting you want

post your results.


BTW, this sort of thing is very heavily discussed and documented, searching around the forums and google would have gotten you your answers quickly. You can also use this site for easy how-to's 

[http://ubuntuguide.org/]("http://ubuntuguide.org/")

---

### Post by SupWiz17 on 2007-10-23
> **superyounan1 said:**
> Basically what you need is the restricted / proprietary video driver provided by AMD/ATI. There is some hostility in the open source community against such drivers because the source code for them is not made available by the vendors, however you should experience better opengl performance

Now the problem with AMD/ATI drivers is that they do not support AIGLX, which is required for desktop effects. Are you looking to have desktop effects? If so, and you want the official ATI/AMD drivers, then you will also need to install XGL-server, it is an alternative to AIGLX that will work reasonably well, but with slightly less stability and performance. In the near future however, ATI/AMD plans on releasing an update driver that will take away your need for the XGL option

There several ways you can install the restricted driver, here are two of them:

1) System > Administration > Restricted Drivers Manager
You should see an option that allows you to enable your the driver for ATI, click to enable it

if that option isn't available, try this

2) In synaptic, Settings > Repositories. Check all the repos the first (Ubuntu software) tab, these should be: main, universe, **restricted,** multiverse. Then click close, and in the main synaptic window click Reload. When all that is done, search for "fglrx" or "xorg-driver-fglrx" and mark it for installation

----------------------------------

to enable desktop effects after having installed the restricted driver, go back to synaptic and search for "xserver-xgl" and mark it for installation, hit apply. When you restart your computer, you will be able to enable desktop effects:
System > Preferences > Appearance > "Visual Effects" tab . and choose the setting you want

post your results.


BTW, this sort of thing is very heavily discussed and documented, searching around the forums and google would have gotten you your answers quickly. You can also use this site for easy how-to's 

[http://ubuntuguide.org/]("http://ubuntuguide.org/")
I have no problem getting my desktop effects working it is 3D games that I cant get to work. I have tried to run Warsow and it says that I do not have openGL but when I go to restricted drivers manager I have that enabled already. I have the ATI drivers installed up to date too. I guess I could trying to find it in my synaptic and install that. I have a ATI x1400m btw I dont know if that helps at all.

---

### Post by SupWiz17 on 2007-10-23
I just searched for fglrx in synaptic and all that comes up for me is the restricted drivers manager and ATI binary X.Org driver and they are both installed already.

---

### Post by SupWiz17 on 2007-10-23
This is the exact error I get when I try to open Warsow.

You're OpenGL installation doesn't support direct rendering. If you have an NVIDIA or an ATI card you'll probably need to install the propritary dirver.

---

### Post by superyounan1 on 2007-10-23
so decide what you want, OpenGL games with FGLRX or Desktop effects with your current driver. good luck

---

### Post by SupWiz17 on 2007-10-23
> **superyounan1 said:**
> so decide what you want, OpenGL games with FGLRX or Desktop effects with your current driver. good luck
So that is causing the problem the dekstop effects. How do I fix this do I just have to turn desktop effects off everytime I want to play a game?

---

### Post by superyounan1 on 2007-10-23
> **SupWiz17 said:**
> So that is causing the problem the dekstop effects. How do I fix this do I just have to turn desktop effects off everytime I want to play a game?

i'm gonna boil it down for you 

FGLRX = GOOD FOR GAMES, bad for desktop effects

YOUR CURRENT DRIVER = NOT good for games, but good for desktop effects

---

### Post by SupWiz17 on 2007-10-23
> **superyounan1 said:**
> i'm gonna boil it down for you 

FGLRX = GOOD FOR GAMES, bad for desktop effects

YOUR CURRENT DRIVER = NOT good for games, but good for desktop effects
I understand that but how do I change the driver? I want to try to play a game to see how it looks. How do I install FGLRX then?

---

### Post by superyounan1 on 2007-10-23
> **SupWiz17 said:**
> I understand that but how do I change the driver? I want to try to play a game to see how it looks. How do I install FGLRX then?

I gave you extremely detailed instructions already, look up ^^^^^^^^^^^^^^^^^^

---

### Post by SupWiz17 on 2007-10-24
> **superyounan1 said:**
> I gave you extremely detailed instructions already, look up ^^^^^^^^^^^^^^^^^^
I have already read your instructions and I can not get xorg-driver-fglrx to show up in synaptic. Everything that comes up I already have installed.

---

### Post by jocko on 2007-10-24
> **SupWiz17 said:**
> I have already read your instructions and I can not get xorg-driver-fglrx to show up in synaptic. Everything that comes up I already have installed.

Have you activated all repos? fglrx should be in universe.
(in synaptic, go to settings-->repositories)

---

### Post by SupWiz17 on 2007-10-24
> **jocko said:**
> Have you activated all repos? fglrx should be in universe.
(in synaptic, go to settings-->repositories)
Yeah I go to preferences and have all of the repositories checked.

---

### Post by superyounan1 on 2007-10-24
you can try Method #2 on this site:
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide")

first go to ati/amd's site and find the driver that they recommend for your card, I'm currently using version 8.40, so if thats what the website is going to recommend for you, then make sure to modify the directions on the link above to reflect the version of the driver you're going to use.

Also if you're using gutsy, then at this step:
sudo bash ati-driver-installer-8.41.7-x86.x86_64.run --buildpkg Ubuntu/feisty

replace teh last part with "Ubuntu/gutsy", and obviously as i mentioned above, the verson of the driver may differ.

Get the driver directly from AMD here:
[http://ati.amd.com/support/driver.html]("http://ati.amd.com/support/driver.html")

Like i mentioned, odds are you'll get version 8.40, make the necessary substitutions in the instructions as I described.

If you're not up to it, then just stay with your current configuration and forget about games for now, all avenues have been explored, and you must have missed something, but theres no use beating a dead horse

[COLOR="Red"]EDIT[/COLOR] wait a minute, i just reviewed your first few posts and it looks like you're already running the FGLRX version found in the repository, I just don't understand what the problem is. If you're just worried about Catalyst and its not loading, you're not missing much, it has almost no features, its not like the windows version.

---

### Post by DouglasAWh on 2007-12-20
I have this exact same problem, but all I want to do is dual monitors!

---

### Post by TristanMike on 2008-03-15
I'd also like dual monitors with my ATI card....any new ideas why the "Segmentation Fault" ?

---

### Post by forrestcupp on 2008-03-15
Are you sure you have the proprietary drivers enabled?

---

