---
title: "Ati Radeon X800 Pro + Wrong resolution (Edgy)"
date: 2007-01-08
forum: General Help
---

### Post by Joey-DK on 2007-01-08
Heya.. I'm new to Linux but not to use of computers etc. Used windows a lot!

Anyway, My problem is I cant get my Ati Radeon X800 Pro grafic card to work! I want to run nwn1 since it has 100% Linux support! I've tried a load of guides etc. none of them work. I figured the easiest way to request help would be to follow the [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide) guide here and tell you when it goes wrong =)

Two minutes ago I found the "Tips and Tricks" section, its a parent folder of the "Install guide" ([http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)) I got all the packages installed now.

But the 
> If you want to use a newer version of the driver than the one which comes with your distribution and you have linux-restricted-modules installed, you have to disable the fglrx kernel module from linux-restricted-modules because it will invariably get in the way of your more recent drivers. Detailed information on how to achieve this can be found in the distribution-specific guides.

Part confuses me! Help appreciated?

Anyway, I tried without:

I have enabled the restricted Repository in sources.list

I have added the lines to xorg.conf

And Now I try installing "the ubuntu way".

sudo apt-get update = Goes through fine.

sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed = Is the newest version.

sudo apt-get install xorg-driver-fglrx = Is already newest version.

sudo depmod -a = Nothing happens?

sudo aticonfig --initial = > Found fglrx primary device section
Nothing to do, terminating.

That wasn't supposed to do that? (right?)

Ah well, there is another way:
sudo gedit /etc/X11/xorg.conf = I replace "ati" with "fglrx"

sudo aticonfig --overlay-type=Xv = > Warning: Option 'VideoOverlay' doesn't affect running session.
Warning: Option 'OpenGLOverlay' doesn't affect running session.
Using /etc/X11/xorg.conf
Saved back-up to /etc/X11/xorg.conf.fglrx-2


Help?

I see not reason to reboot, But I try it anyway ..

ctrl + alt +backspace = Guess what .. restart .

[SIZE="4"]Alright![/SIZE]

Now My resolution works! 1280x1024 ! 75 Hz! Top Notch!

Though, still when I try to run nwn(1) it gives me a 
> Failed to initialize graphics.


Any help with release alot of cookies and prayers on your shoulder!

---

### Post by mxrten on 2007-01-08
> But the
[QUOTE]Quote:
If you want to use a newer version of the driver than the one which comes with your distribution and you have linux-restricted-modules installed, you have to disable the fglrx kernel module from linux-restricted-modules because it will invariably get in the way of your more recent drivers. Detailed information on how to achieve this can be found in the distribution-specific guides.
Part confuses me! Help appreciated?[/QUOTE]

It means you must stop the fglrx module from being loaded. Open **/etc/modprobe.d/blacklist** as root:
```
sudo gedit /etc/modprobe.d/blacklist
```
and add the line: **blacklist fglrx**

Now restart, and hopefully it will work

---

### Post by Joey-DK on 2007-01-08
Thank you for the answer, unfortunately it didn't work!

I still get a failed to initiialize graphics ?

---

