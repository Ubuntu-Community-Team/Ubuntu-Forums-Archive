---
title: "Nvidia Driver/compiz On Edgy"
date: 2006-12-27
forum: General Help
---

### Post by Camden on 2006-12-27
Install Nvidia/Compiz on Edgy

I recently switched from Beryl to Compiz out of curiosity.  I am fairly impressed with Compiz.  It seems to be fairly stable and clean.  The one thing I was disappointed in was the documentation on go-compiz.org.  In contrast Beryl has an excellent wiki and I found myself using their wiki for Nvidia drvier setup and then switching back to go-compiz.org.  So, I decided to to put together a step by step how to covering Nvidia setup and Compiz.  Mainly for my own good but hey I might as well put it out there in case anyone else wants it.  

This works for me and I can not guarantee it working on anyone elses machine. This is from the perspective of installing on a fresh install of Ubuntu (ie. no previous graphic driver install).I'm running an Nvidia 7600 GS/x86 32 bit machine.

1) NVIDIA DRIVER INSTALL
Right click and copy:
```
deb http://www.albertomilone.com/drivers/edgy/latest/32bit binary/
```  
Navigate to System->Administration-> Software Sources->Third Party
Click Add and paste into field

In terminal:
```
wget http://albertomilone.com/drivers/tseliot.asc
```
Navigate to System->Administration-> Software Sources->Authentication
Click Import Key File and navigate to your Home folder and add the key tseliot.asc
Close Software Sources and when asked click Reload

In terminal:
```
sudo apt-get update
```
Identify your kernel
In terminal:
```
uname -r
```
If you have a fresh install Of Ubuntu it will probably come back with 2.6.17-10-generic
In terminal:
```
sudo apt-get install linux-generic
```
Or whatever architecture was returned from the uname -r (ie.  linux-386)

Now install the driver
In terminal:
```
sudo apt-get install nvidia-glx
```
Might be a good idea to back up your xorg.cong file at this point unless you wanna roll the dice
In terminal:
```
sudo nvidia-xconfig
```
In termianl:
```
sudo apt-get upgrade
```
Next ctrl+alt+backspace and log back in (or just restart)

In terminal:
```
sudo gedit /etc/X11/xorg.conf
```
Add this to the "Screen" section
```
Option "AddARGBGLXVisuals" "True"
```
SAVE and close
I restart at this point just to see if everything is cool 

2) INSTALL COMPIZ
Right click and copy:
```
deb http://gandalfn.club.fr/ubuntu edgy stable dev
```
Navigate to System->Administration-> Software Sources->Third Party
Click Add and paste into field

In terminal:
```
gpg --keyserver hkp://wwwkeys.eu.pgp.net --recv-keys 0x483170E9 ; gpg --export -a 0x483170E9 | sudo apt-key add -
```
Close Software Sources and when asked click Reload
In terminal:
```
sudo apt-get update
```
In terminal:
```
sudo apt-get install compiz-freedesktop compiz-freedesktop-extra compiz-freedesktop-gnome gnome-compiz-manager gnome-compiz-manager-extra
```
In terminal:
```
compiz-tray-icon
```
Now it all should be installed!
In your panel notification area you should see the Compiz icon
Right click on that and select GL Desktop
Then in preferences you can enable the cube and wobbly windows etc.
[COLOR="Red"]
Again this is a use at your own risk guide!!![/COLOR]
None of this is orginal it's basically a mashup of: 
[[COLOR="Blue"]http://albertomilone.com/instructions.html[/COLOR]]("http://albertomilone.com/instructions.html")
[[COLOR="Blue"]http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/nVIDIA[/COLOR]]("http://wiki.beryl-project.org/wiki/Install/Ubuntu/Edgy/nVIDIA")
[[COLOR="Blue"]http://go-compiz.org/index.php?title=Main_Page[/COLOR]]("http://go-compiz.org")

Credit goes to them all the way:mrgreen:

---

### Post by Stephen Howard on 2006-12-27
Would you recommend compiz instead of beryl?  I'm thinking about dipping my toe in the water, but I'm still a bit confused about the pros & cons of each.

---

### Post by Camden on 2006-12-27
To tell you the truth I like them both.  Beryl with emerald themes is some good looking stuff. However, compiz seems to be a bit more stable for me then beryl.  So for now my vote is for compiz.  That could change at a moments notice though.

---

### Post by The Noble on 2006-12-28
What package is used for theming? I can't find cgwd and gnome compiz preferences has no options for themes except for metacity themes.

---

### Post by c.dric on 2007-01-04
Thanks for the how-to. it worked great [[1]]("http://c.dric.be/gium/misc/Compiz-cube1.jpg") [[2]]("http://c.dric.be/gium/misc/Compiz-cube2.jpg") on my xfce desktop.

Now i've just checked for updates in synaptic and it wants me to 

**- Uninstall **
compiz-freedesktop-gnome

**- Install**
compiz
compiz-core
compiz-extra
compiz-extra-gnome
compiz-extra-plugins
compiz-gnome
compiz-plugins

**- Update**
compiz-freedesktop
compiz-freedesktop-extra
gnome-compiz-manager
gnome-compiz-manager-extra
libgnome-compiz-manager

I'm guessing i shouldn't do this ?

My compiz is working nicely now, i wouldn't want to have it screwed by synaptic [-(

---

