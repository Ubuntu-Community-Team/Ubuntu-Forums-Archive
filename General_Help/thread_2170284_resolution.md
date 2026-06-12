---
title: "resolution"
date: 2013-08-25
forum: General Help
---

### Post by rpro1900 on 2013-08-25
Not an expert here but.. 

Why is so damn hard for linux  to detect proper resolution modes....?? ? ubuntu 12.04 on precision M4400 laptop with nvidia quadro fx770M..

Ubuntu detects the 1920x1200 resolution..good. But why is not showing in the displays other (lower) resolutions too?
so you can switch them as I need? 
why do i keep have to mess around with 10-monitor.conf.. and all sorts of things... that work for some and not for others..
why is not Ubuntu adding that 10-monitor file.. when it detects the capabilities of the monitor and video card..



I have tried adding a [COLOR=#3F3F3F][FONT=Ubuntu] 10-monitor.conf to add a 1920x1080 mode..following this 
[/FONT][/COLOR][http://samuelmartin.wordpress.com/2012/05/29/enabling-resolutions-in-ubuntu-12-04-lubuntu-12-04/](http://samuelmartin.wordpress.com/2012/05/29/enabling-resolutions-in-ubuntu-12-04-lubuntu-12-04/)

did not work..



Any other suggestions?
thanks

---

### Post by lukeiamyourfather on 2013-08-26
Did you install the proprietary graphics driver from Nvidia? You can do it through the Ubuntu repositories or the hardware drivers utility. It offers more features, functionality, and performance than the open source Nvidia driver.

---

### Post by rpro1900 on 2013-08-26
Thank you for the reply. I did install the proprietary drivers from the repositories.. 
I think there is no other way to play with these settings other then using the 10-monitor.conf file..
there is also an xml in ~/.config/monitor.xml. tried to edit those and it failed..

---

### Post by grahammechanical on 2013-08-26
Modern computer monitors or display screens have their optimum settings stored in the display itself. These settings are called Extended Display Identification Data (EDID). Ubuntu reads that information at boot time and sets the optimum resolution instead of reading a configuration file to find out the resolution. This prevents the user from setting a configuration that might damage the display/monitor.

As much as you might dislike this practice, I see it as part of the original aim of Ubuntu to be a distribution for humans who had little or no knowledge of computer hardware. For me, it means I do not have to study a monitor user manual to figure out the monitor vertical and horizizontal refresh rates when I install Ubuntu.

[http://en.wikipedia.org/wiki/Extended_display_identification_data](http://en.wikipedia.org/wiki/Extended_display_identification_data)

Do you know, that if things go according to plan, this time next year it should be possible for people to buy a Ubuntu superphone that will display Ubuntu on a monitor simply by connecting the phone to the monitor. Imagine, a Ubuntu phone that becomes a PC just by connecting it to a monitor. Now, how could that be possible if Ubuntu did not use the monitor's EDID or its replacement DisplayID?

Regards.

---

### Post by rpro1900 on 2013-08-26
Thanks for EDID explications ..

No complains about..to read the optimum resolution at boot time... as long as this config would do what I want.. but here is not the case. Ubuntu detects that optimum size ... but in certain situations (like presentations) you need to lower the resolution.. 


why not ,beside, setting up the optimum resolution and showing me (as a user) all capable resolutions of the monitor.. ??.. and allowing me to easy modify..

I.E. i have attached a second monitor with 1920x1080.. and I cannot mirror(no extend) the displays since one is 1920x1200 ..


As much as I like the distro and I would love to make a linux.. my main workstation.. it is not possible at this time.. unfortunately way too much time is spent with minor things that would have to run out of the box.. a simple task.. change the resolution ..
I followed the [https://wiki.ubuntu.com/X/Config/Resolution]("https://wiki.ubuntu.com/X/Config/Resolution#Resetting_an_out-of-range_resolution") (which seems out of date  gnome-display-properties? what gnome?) without success...




 
Thank you very much for your help..

---

