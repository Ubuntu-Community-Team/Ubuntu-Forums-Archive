---
title: "Plymouth boot splash - unexpected result?"
date: 2013-09-12
forum: General Help
---

### Post by MrGrumpyArse on 2013-09-12
[U][B]Relevant system info
[/B][/U]Ubuntu-gnome 13.04 (running 3.10.11 mainline kernel)
Gnome 3.8
Nvidia Geforce graphics (running driver 325.15)



[U][B]Issue

[/B][/U]I`m currently attempting to modify my Plymouth boot theme, as I am not overly fond of the blue stripes that come as default with Gnome 3. 

At the moment, with the use of Google and a number of on-line tutorials I seem to be getting the principle of the process and have hashed together a quick rough and ready edit to the default theme, replacing the default images with some knocked together with images and artwork shamelessly plundered from the web, complimented by a similarly constructed matching wallpaper. (once I have reliable results I will attempt to make some from scratch).

My problem is my "replacement Plymouth images" show as expected up until just before the password prompt, then the "blue stripes" appear, followed by password prompt, more "blue stripes" then eventually my "personalised wallpaper" loads.


[U][B]My question is

[/B][/U]How do I stop the blue stripes loading (around the password prompt) and load something more consistent with the modified Plymouth theme?  Where is the system pulling the blue stripes from? Is there a config or similar that will allow me to edit which image is loaded?


This 90 second video hopefully shows the issue more clearly (apologies for the poor quality :-(  -  Blue stripes appear around 49 seconds )



[http://youtu.be/T-Z2eiktSoc](http://youtu.be/T-Z2eiktSoc)

Thanks in advance for any help

Mark

---

### Post by MrGrumpyArse on 2013-09-12
Doing a bit more reading has lead me to the gdm greeter settings configuration file at -  /et/gdm/greeter.gsettings

Not made any changes as yet but the available options seem like possibly what I am looking for.

I will update with any developments

Mark

---

### Post by MrGrumpyArse on 2013-09-12
Well it seems like the configuration file was not quite the success I had hoped, as in no change what so ever, but the issue does appear connected to the greeter rather than Plymouth.

After searching the system for further copies of the "blue stripes" wallpaper I found the same images but under the names "bright day" "goodnight" & "morning" at -

/usr/share/themes/Adwaita/backgrounds

Temporarily renaming the files ( had to sudo ) and rebooting had the hoped for effect replacing the pre & post login " blue stripes" with  - 
a blank screen - then log in screen - blank screen again -  and finally the desktop loads complete with custom wallpaper.

I will try replacing the renamed files with custom images of the same file type etc and see what happens

Mark

---

### Post by Jonathan Precise on 2013-09-14
Please install ubuntu-tweak to do this graphically:

```
sudo add-apt-repository ppa:tualatrix/ppa
sudo apt-get update
sudo apt-get install -y ubuntu-tweak
```

If ubuntu-tweak crashes on start-up, then try:

```
sudo nano /etc/apt/sources.list.d/ubuntu-tweak-testing.list
```

It is empty, so add the following:

> deb [http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu) saucy main 
deb-src [http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu](http://ppa.launchpad.net/ubuntu-tweak-testing/ppa/ubuntu) saucy main

Note: I put in "saucy" instead of "raring" as "saucy" uses gnome 3.8.

Then:
```
sudo apt-get update
sudo apt-get upgrade
```
Make sure you are not prompted to remove unity, ubuntu-gnome-desktop, branding-ubuntu... or you will end up with a system without ubuntu-gnome!

If you are prompted to remove them, press n. Then install dconf-editor. Use it to navigate to LightDM or GDM settings. (Optional: Post a picture of your login screen to see whether it's LightDM or GDM. Install Gimp and use it to blur out sensitive-info [hostname, username, etc.])

If it fails to install, then post the errors.

---

### Post by MrGrumpyArse on 2013-09-21
Thanks for the info Jonathan - been away from the PC for a few days but I will investigate your suggestions as soon as an opportunity arises :-) 

Mark

---

