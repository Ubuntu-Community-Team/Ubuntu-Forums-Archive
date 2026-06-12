---
title: "how to lower system resource usage  {old machine}"
date: 2014-02-16
forum: General Help
---

### Post by jimbean on 2014-02-16
ive got a old machine windows xp made for 1 gig ram 
ive tried
To achieve this, open Applications > System Tools > Configuration Editor (or Alt+F2 and enter gconf-editor). Once open, browse to /apps/metacity/general/, and in the right pane you will notice the option “reduced_resources”, so tick that to set it to true
but no go
ive tried
Open the Appearance Preferences dialog by clicking on the System menu then "Preferences" and then "Appearance."
Read more: [http://www.ehow.com/how_8220530_turn-compiz-off.html#ixzz2tUmPAwZE](http://www.ehow.com/how_8220530_turn-compiz-off.html#ixzz2tUmPAwZE)
but no go
any quick and easy fix for ubuntu 13.10
id like to use system as is without reinstalling kubuntu and or xubuntu

---

### Post by GrouchyGaijin on 2014-02-16
You might want to try Jupiter
[http://www.webupd8.org/2010/07/jupiter-ubuntu-ppa-hardware-and-power.html](http://www.webupd8.org/2010/07/jupiter-ubuntu-ppa-hardware-and-power.html)

I installed it and set it to Power Saving mode.  I noticed a dramatic decrease in my laptop's temperature.
My laptop is pretty old with only 2 GB of ram.

---

### Post by ibjsb4 on 2014-02-16
Are you sure your running metacity?  Default install uses compiz.

Edit:

To run metacity in 13.10:
```

sudo apt-get install gnome-panel
```

Reboot and at the login window click on the icon and select "no-effects".  Then you will be running metacity.

---

### Post by grahammechanical on 2014-02-16
I do not think that Kubuntu is any less resource hungry then Ubuntu. Xubuntu, on the other hand may show improvements. I am confused about your setup. You are looking for an easy fix for Ubuntu 13.10 but you seem to be using metacity. Are you using an alternative desktop/user interface than Unity?

I think a major component is often overlooked when it comes to user experience and that is the video graphic card. I am running Ubuntu on a machine with 1GB of system RAM. The experience is fine. I also have a video adapter with 1GB of its own memory. I think that is making a lot of difference.

In Ubuntu 13.10 we can install gnome-session-flashback. That will give us a login option of using Gnome Flashback (with Metacity). The user interface is different from the Unity interface. Things may seem faster but a lot depends upon the applications that you are using and how many that you have open at the same time. You may want to consider using alternative applications that use less system resources than the default applications.

Regards.

---

### Post by deadflowr on 2014-02-16
For what it's worth, what desktop are you using anyway?
Don't think metacity has anything to do with kubuntu, or xubuntu, or default ubuntu(unity).

---

