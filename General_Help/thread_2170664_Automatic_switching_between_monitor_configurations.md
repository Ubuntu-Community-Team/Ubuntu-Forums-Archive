---
title: "Automatic switching between monitor configurations"
date: 2013-08-27
forum: General Help
---

### Post by michaelaquilina on 2013-08-27
[COLOR=#333333][FONT=UbuntuRegular]I have a laptop and an external monitor and i was wondering if there was a simple approach to switching between multiple monitor configurations based on the detected available displays.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]For example:
[/FONT][/COLOR]

[LIST]
[*]When i am at home and i plug in my external monitor i would like this to automatically become enabled and the laptop screen to become disabled.
[*]As soon as i pull out the display cable for the external monitor, i would like the laptop screen to automatically become enabled.
[/LIST]
[COLOR=#333333][FONT=UbuntuRegular]
I was expecting this to just "work" just like it does in windows - but it seems to be much harder than that.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]
I am aware of the **xrandr** command to turn displays on and off but i cannot seem to find a way to get this to work the way i describe above. Instead i am currently using the xrandr --auto command to enable all outputs on login and then manually disable and change what i mean using the xrandr command in a  terminal.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I had also found [this post]("http://askubuntu.com/questions/42393/simple-switching-between-multiple-monitor-configurations") about switching between multiple monitor configurations and the results seem a bit inconclusive. However i was hoping that with xrandr there would be a simpler solution.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]
For me, the fact that when i pull out my external monitor the screen just goes black and i get an error message is a big issue holding me back from making the complete switch to linux as i move around alot as a student.
[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]My OS of choice is currently Kubuntu 12.04 but i am willing to change to something else if it provides a better way of setting up the described setup.[/FONT][/COLOR]

---

### Post by rai_shu2 on 2013-08-27
Monitor configurations depend quite a bit on the display driver and its configuration. Additionally, you could use ARandR, which is in the repos.

---

### Post by tgalati4 on 2013-08-27
What is the model of the laptop?  What graphics chip do you have?  Does your laptop have an Fn+F7 to cycle displays?  That is what I use on my IBM thinkpad and it works well when switching to projectors or external displays.  To lock in resolutions, you need to put specific entries in your /etc/X11/xorg.conf file to match the exact monitor that is attached and detected.  It will happen automatically, but sometimes the resolution is not what you want, so you have to lock it in.  

At worst, you might have to put an icon on your desktop that runs a xrandr script with your exact setup values.  There are ways to trigger the script with a dbus message command when an external monitor is attached, but you will have to research it because it is tricky to set up.

---

