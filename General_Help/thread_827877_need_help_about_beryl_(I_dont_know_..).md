---
title: "need help about beryl (I dont know ****..)"
date: 2008-06-13
forum: General Help
---

### Post by dinbrca on 2008-06-13
Ok..
I am very very new at ubuntu..
And I understood that there are some applications like beryl that can change the desktop, visual effects (if I had understood good)..
so I wanted to learn about beryl but I dont even know where to download it
cause in there website there is no download page.. (yes I know I am noob at linux cause I just started!)
Oh..And I have ubuntu 8.04
Thx for the helpers

---

### Post by chewearn on 2008-06-13
Ubuntu 8.04 comes with compiz fusion preinstalled; you just need to enable it.  Don't use beryl, as it's obsolete.

First, you need to enable 3D graphics driver.  What graphics chip you have?

---

### Post by dinbrca on 2008-06-13
I have NVidia 8800GT

---

### Post by chewearn on 2008-06-13
Have you enabled nvidia restricted driver?

Top panel menu > System > Administration > Hardware Drivers

Click the checkbox for nvidia driver.  This will enable your 3D acceleration.

You will need to reboot.  Later, there is a slight chance that your resolution might not be detected properly.  To fix this, you need to install nvidia-settings, and run it with root privilege to configure.  We will get there if needed later.

---

### Post by mpschenck on 2008-06-13
I would like to achieve this look by using compiz-fusion...

[IMG]http://wiki.compiz-fusion.org/Welcome?action=AttachFile&do=get&target=cube2.png[/IMG]

taken from here...

[http://wiki.compiz-fusion.org/]("http://wiki.compiz-fusion.org/")

I don't understand a lot of the things the site says, but I have already enabled the nvidia driver.

---

### Post by chewearn on 2008-06-13
> **mpschenck said:**
> I would like to achieve this look by using compiz-fusion...
[I]<picture removed>
[/I] taken from here...

[http://wiki.compiz-fusion.org/](http://wiki.compiz-fusion.org/)

I don't understand a lot of the things the site says, but I have already enabled the nvidia driver.

Ok, first thing after enable 3D graphics, verify desktop effects are enabled:
Top panel menu > System > Preferences > Appearance > Visual Effects (last tab)

Set the radiobutton to anything other than none.

Compiz-fusion should now be enabled.  However, you would only see minimal effects (the defaults are conservative).  To enable custom effect, install CCSM:

```
sudo apt-get install compizconfig-settings-manager
```

This will give you a new menu entry:
Top panel menu > System > Preferences > Advanced Desktop Effects Settings

There are many things to tweak, but don't go overboard!  Some settings are unpolished and the wrong one might break things.

As for the screen capture in your post, some of the related compiz settings are:
1. Desktop cube
2. Rotate cube
3. 3D Windows

---

### Post by mpschenck on 2008-06-13
Ok, I already had Compiz-fusion installed and had those option checked in Advanced Desktop Effects settings, but nothing happened even after a reboot.

I thought I was doing something wrong...


Being a XP convert I was thinking there should be an "Apply" button somewhere?

I found this site [http://gnome-look.org/]("http://gnome-look.org/").  There are some cool desktops/themes there but I'm still looking.  I really don't understand how this stuff works.

---

### Post by ad_267 on 2008-06-13
Did you install compizconfig-settings-manager like AstalaVista said? You already have the basic effects on but you need that in order to customize them.

This is a good start for basic themeing but it doesn't go into more advanced things like compiz-fusion or emerald: [http://justanothertechblog.blogspot.com/2007/03/quick-guide-on-customizing-ubuntu.html](http://justanothertechblog.blogspot.com/2007/03/quick-guide-on-customizing-ubuntu.html)

---

### Post by mpschenck on 2008-06-14
> **ad_267 said:**
> Did you install compizconfig-settings-manager like AstalaVista said? You already have the basic effects on but you need that in order to customize them.

mpschenck@mpschenck-desktop:~$ sudo apt-get install compizconfig-settings-manager
[sudo] password for mpschenck: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compizconfig-settings-manager is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
mpschenck@mpschenck-desktop:~$


> **ad_267 said:**
> This is a good start for basic themeing but it doesn't go into more advanced things like compiz-fusion or emerald: [http://justanothertechblog.blogspot....ng-ubuntu.html](http://justanothertechblog.blogspot....ng-ubuntu.html)

Looks like some good info.

---

### Post by ad_267 on 2008-06-14
I forgot about this too: [http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

That thread contains a good overview of all the different things you might want to know and links to more detailed reading.

---

### Post by chewearn on 2008-06-14
Is it working already?

If not, reconfirm that 3D graphics is enabled:
```
glxinfo | grep rendering
```

If answer is "direct rendering: yes", then you are good to go.  Else, your 3D graphics driver is not properly enabled.

---

### Post by Sef on 2008-06-14
> AstalaVista: Compiz-fusion should now be enabled. However, you would only see minimal effects (the defaults are conservative). To enable custom effect, install CCSM:

Code:

sudo apt-get install compizconfig-settings-manager



> mpschenck: Being a XP convert I was thinking there should be an "Apply" button somewhere?

There is an apply button to install it.

Applications > Add/Remove > Show: Change to 'All Available Applications' > Search: CCSM > Check box next to ccsm > Apply Changes > Apply > close

---

### Post by mpschenck on 2008-06-14
> **AstalaVista said:**
> Is it working already?

If not, reconfirm that 3D graphics is enabled:
```
glxinfo | grep rendering
```

If answer is "direct rendering: yes", then you are good to go.  Else, your 3D graphics driver is not properly enabled.



```
mpschenck@mpschenck-desktop:~$ glxinfo | grep rendering
direct rendering: Yes
mpschenck@mpschenck-desktop:~$ 

```


> **Sef said:**
> There is an apply button to install it.

Applications > Add/Remove > Show: Change to 'All Available Applications' > Search: CCSM > Check box next to ccsm > Apply Changes > Apply > close

Ok, went there and the box was already checked and the Apply Changes button was greyed out. I unchecked the box the button ungreyed. I rechecked the box and the button once again was greyed out. 

I should mention that by fumbling around on other threads I was able to get a little blue icon in what I know as the system tray (on the bar at the top of the screen) that says "Compiz Fusion Icon" this give a few options such as...
 
"Settings Manager" 
"Emerald Theme Manager" 
"Reload Window Manager" 
"Select Window Manager">Compiz or Metacity 
"Compiz Options" >Loose Binding or Indirect Rendering 
"Select Window Decorator" >GTK Window Decorator or Emerald 
"Quit"

---

