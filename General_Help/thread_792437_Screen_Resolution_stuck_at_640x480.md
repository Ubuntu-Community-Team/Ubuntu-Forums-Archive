---
title: "Screen Resolution stuck at 640x480"
date: 2008-05-12
forum: General Help
---

### Post by MichaelSelf on 2008-05-12
I recently installed Ubuntu on my desktop.  It is an eMachines and has an nVidia Geforce4 video card.  I have installed and enabled the Driver and Nvidia controller, but cannot seem to adjust the resolution any higher.  My Monitor is an AOC 17" LCD and is capable of 1280x1080.  This resolution is driving me nuts, Help!

---

### Post by MaindotC on 2008-05-12
Hi, Michael - not sure how experienced you are w/ this so I'm going to ask some kiddy questions.  Did you go to System -> Administration -> Screens and Graphics and select the monitor you have?  If you've already done that, please post the contents of your /etc/X11/xorg.conf file.  Was the resolution ever better than it is now?

---

### Post by MichaelSelf on 2008-05-12
Kiddy questions are good...I'm completely new to all this, I'm pretty good with Windows, haha.  Under System>Admin I do not have a screens and graphics option, it goes from Printing straight to Services. ???  

Is this what you're asking for?

Section "Monitor"
    Identifier     "Configured Monitor"
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
EndSection

Section "Screen"
 Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "nvidia-auto-select"
    EndSubSection
EndSection

---

### Post by MaindotC on 2008-05-12
I was looking for something in xorg.conf that showed a resolution - I'll have to rely on the others because I'm learning xorg.conf.

Hmm...you don't see Screens & Graphics...I think that has something to do with the permissions of the account you are using.  I created an account and I got the same issue.  You can't log into the GUI portion of Ubuntu as root, but is there another user account that you can use to log in?  Perhaps the name of the machine which should be in the bottom right of the login screen?  If you can, go to System -> Administration -> Users & Groups.  You will probably be prompted for the root password or your current password.

When you get to that screen, select the account you wish and choose "properties".  Under "User Privileges" it should have an option for "Administer the System".  Actually if you're not concerned about security you can check all of these and then once you get the resolution set you can start disabling services as you see fit.  Let me know if that works.

---

### Post by MichaelSelf on 2008-05-12
There's only one user...Administer the system is checked.  Still, the highest resolution avaliable is 640x480.  One other problem with this is that I can't always see all of the open windows. (the bottom is cut off)

---

### Post by MaindotC on 2008-05-12
Yeah I am familiar with that bottom cut off thing - very annoying.  Way back I had to install the ATI proprietary driver and I had the same issue so when I started the installation for the ATI driver it would open up a gui and at the bottom where I had to check "Apply" or "Install" I couldn't reach it :(

If you can Administer the system, go to System -> Preferences -> Main Menu.  This will show you what entries are shown in the main menu.  I doubt you have changed any of these, but can you check the "Administration" menu and see if there is an option to enable the Screens & Graphics sub-menu?

---

### Post by MichaelSelf on 2008-05-13
There is only one user and I am set as the admin.  I disabled the nvidia driver that was installed and I now have 800x600, but I would still like to have 1280x1080.

---

### Post by MaindotC on 2008-05-13
Can you check the "Main Menu" option I described and see if it's there?

---

### Post by MichaelSelf on 2008-05-13
There is no Screens and Graphics Selection to enable under the main menu

---

### Post by MaindotC on 2008-05-13
Can you try reinstalling the package called ubuntu-desktop?
```

sudo apt-get update
sudo apt-get -f install
sudo apt-get install ubuntu-desktop

```

Then reboot.

---

### Post by MichaelSelf on 2008-05-13
Might be a stupid question, but how do I do that?

---

### Post by MaindotC on 2008-05-13
Sorry I edited the post after you replied :) Check it now.

---

### Post by ajopaul on 2008-05-13
just check if you have installed restricted drivers, it should be something like linux-restricted-2.6.24* also install nvidia-settings and then reboot

---

### Post by MichaelSelf on 2008-05-13
reinstalled, still no luck...I'll toy around with it some more tommorow sometime.  Thanks for the help.

---

### Post by Xgen on 2008-05-13
Try overriding the nvidia selection. In terminal:

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo gedit /etc/X11/xorg.conf

In the part that says: Modes "nvidia-auto-select"
Change to: Modes "1280x1080" (Are you sure that it is 1280x1080 and not 1280x1024?) Change to suit.
Restart.

---

### Post by MichaelSelf on 2008-05-13
> Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
	Option		"AddARGBGLXVisuals"	"True"
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
	Load		"glx"
EndSection

Checked without the driver enabled and with the driver enabled...here's what I'm seeing over here on xorg.conf and yes, I did mean 1280x1024...yesterday was a long day.

---

### Post by ubuntu-freak on 2008-05-13
Press Alt F2, type "gksudo displayconfig-gtk" and your password when prompted, then select the resolution you know is right. Reboot.
 
Nathan

---

### Post by MichaelSelf on 2008-05-13
> **reassuringlyoffensive said:**
> Press Alt F2, type "gksudo displayconfig-gtk" and your password when prompted, then select the resolution you know is right. Reboot.
 
Nathan

That did it...THANKS!:guitar:

---

### Post by MaindotC on 2008-05-14
> **reassuringlyoffensive said:**
> Press Alt F2, type "gksudo displayconfig-gtk" and your password when prompted, then select the resolution you know is right. Reboot.
 
Nathan

I don't understand!  That's what I was trying to get him to do with this:

> **strAlan said:**
>  see if there is an option to enable the Screens & Graphics sub-menu?

Why should he have to type this command?  How do you get it installed in his menu and why do you think it wasn't there in the first place?

---

### Post by ubuntu-freak on 2008-05-14
> **strAlan said:**
> I don't understand!  That's what I was trying to get him to do with this:



Why should he have to type this command?  How do you get it installed in his menu and why do you think it wasn't there in the first place?

 
GNOME removed it from System > Administration to protect users from doing something silly. Kinda sweet huh? Not. Seriously though, it's not completely compatible with the new Xorg, but it's still very useful for configuring monitors. I disagree with it being removed, it should have just been restricted and turned into a resolution and monitor tool. The one in System > Preferences doesn't cut it.
 
There will be a replacement GUI tool soon, compatible with the latest Xorg. It's a frontend for RandR called URandR. I presume it will be named Screens & Graphics in the menu, just as displayconfig-gtk was. We should hopefully see it in 8.04.1, if it's ready.
 
Nathan

---

### Post by MaindotC on 2008-05-14
But he stated previously that he wasn't on the only user account and it's set to administrative privileges.  I installed Hardy before and the Screens & Graphics thing was there.  Are you certain it was removed by default installation?

---

### Post by mc4man on 2008-05-14
@strAlan
```
Why should he have to type this command
```
it's in the menu -> other,  has to be enabled from edit menus

---

### Post by ubuntu-freak on 2008-05-14
> **strAlan said:**
> But he stated previously that he wasn't on the only user account and it's set to administrative privileges.  I installed Hardy before and the Screens & Graphics thing was there.  Are you certain it was removed by default installation?

 
Yes, it was previously in System > Administration, and as mc4man pointed out, it's now hidden in Applications > Other in Hardy.
 
Nathan

---

### Post by Acid.Blade on 2009-01-10
ok i have almost the same setup on my computer here but cant find the program you are talking about.... i have hit alt F2 and enter "gksudo displayconfig-gtk" it tells me it's starting an administrative tool but then nothing happens so i have searched everything i can think of to find this magic program that will fix all my problems lol.... but i cant find it.... i'm running Ubuntu 8.1 ..... what am i missing and or doing wrong?

Note i have the Nvidia drivers and X server setup installed

---

### Post by ubuntu-freak on 2009-01-10
> **Acid.Blade said:**
> ok i have almost the same setup on my computer here but cant find the program you are talking about.... i have hit alt F2 and enter "gksudo displayconfig-gtk" it tells me it's starting an administrative tool but then nothing happens so i have searched everything i can think of to find this magic program that will fix all my problems lol.... but i cant find it.... i'm running Ubuntu 8.1 ..... what am i missing and or doing wrong?

Note i have the Nvidia drivers and X server setup installed

This is an old thread and that tool isn't included with Intrepid.

I'm not sure what to tell you after reading your other post, as you say you have already tried XRandR. If XRandR doesn't allow you to set the resolution you want, try setting the highest resolution it will allow:

**sudo xrandr -q**

**sudo xrandr -s widthxheight**

Then try setting the proper resolution again.

Don't forget to file a bug.

---

### Post by Acid.Blade on 2009-01-11
yes i have played wit xrandr and with the X Server setup from nvidia. i can get any res to show up but i cant get it to save to the xorg.conf file.
i have no idea how to do a bug report... 
with xrandr i can even try to force the res it fails on 1280x1024 but will try to do the 1024x768 ... even when i can get the 1024x768 to try to work it is only a Pan still at the 640x480 res.... i have seen posts on how to use nano to edit xorg.conf but that dont seam to work very well as that's when i end up going back and reinstall the drivers to a backup and ta da i'm back to start again :( 
I'm not sure maybe i'm just not reading the post right on how to do this.... 
any other ideas.... i'm sure at this point it's going to come down to forcing the res..... or forcing the type of monitor it is ... just not sure if i'm doing this right or if it just will not work for my set up....
ok after messing around a bit in xrandr and with the nvidia X server settings i have got the res to show at startup as 1280x1024 but it is still a pan view only showing 640x480 so it's like a zoom view .... better but still not what i'm looking for lol

---

### Post by ubuntu-freak on 2009-01-11
> **Acid.Blade said:**
> yes i have played wit xrandr and with the X Server setup from nvidia. i can get any res to show up but i cant get it to save to the xorg.conf file.
i have no idea how to do a bug report... 
with xrandr i can even try to force the res it fails on 1280x1024 but will try to do the 1024x768 ... even when i can get the 1024x768 to try to work it is only a Pan still at the 640x480 res.... i have seen posts on how to use nano to edit xorg.conf but that dont seam to work very well as that's when i end up going back and reinstall the drivers to a backup and ta da i'm back to start again :( 
I'm not sure maybe i'm just not reading the post right on how to do this.... 
any other ideas.... i'm sure at this point it's going to come down to forcing the res..... or forcing the type of monitor it is ... just not sure if i'm doing this right or if it just will not work for my set up....
ok after messing around a bit in xrandr and with the nvidia X server settings i have got the res to show at startup as 1280x1024 but it is still a pan view only showing 640x480 so it's like a zoom view .... better but still not what i'm looking for lol

Could it be a graphics driver issue? Disable the non-free driver, if that's what you're using, then see if you can force the correct resolution afterward.

---

### Post by Acid.Blade on 2009-01-11
with the Nvidia drivers off i can get up to 800x600 but the system still dont see my AOC monitor.... as far as i can tell the Nvidia drivers that i got from Nvidia work well it just dont see what kind of monitor i have and will not let me set a good res.... with the X server setup i can force any res into xrandr and in xrandr i can set that res.... but it dont save to the xorg.config file so i have to redo it all every time i boot linux

---

### Post by tilerwen on 2009-01-14
Try to edit your xorg.conf under Device with:

Section "Device"
   ...
   Option "IgnoreEDID" "1"
EndSection

---

### Post by Acid.Blade on 2009-01-16
ok got it.... it took editing xorg.conf with nano from root...(be sure to edit from root or you will not be able to save when your done editing.)
ended up editing almost all of my xorg.conf file to get it to work...
also when editing use tab not space to jump over .... IE. after "monitor" (enter) then (tab) over to add in the Identifier .... ubuntu will not read the spacing right if you dont use (tab)

Section "Monitor"
        Identifier      "Configured Monitor"
        HorizSync       30-81
        VertRefresh     60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        DefaultDepth    24
        SubSection      "Display"
        Depth           24
        Modes           "1280x1024_60"
        EndSubSection
        Option  "AddARGBGLXVisuals"     "True"
EndSection

Section "Module"
        Load    "glx"
        Disable "dri2"
EndSection

Section "Device"
        Identifier      "Configured Video Device"

EndSection

Section "Module"
        Load    "glx"
        Disable "dri2"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Option  "NoLogo"        "True"
        Driver  "nvidia"
EndSection

as for my xrandr ..... (after edit)

Screen 0: minimum 320 x 240, current 1024 x 768, maximum 1280 x 1024
default connected 1024x768+0+0 0mm x 0mm
   1280x1024      50.0  
   1024x768       51.0* 
   1280x960       52.0  
   1152x864       53.0  
   960x600        54.0  
   960x540        55.0  
   840x525        56.0     57.0  
   800x600        58.0     59.0  
   800x512        60.0  
   720x450        61.0  
   680x384        62.0     63.0  
   640x512        64.0  
   640x480        65.0     66.0  
   576x432        67.0  
   512x384        68.0  
   400x300        69.0  
   320x240        70.0  


Hope this helps for anyone that has the same problem...

---

### Post by ubuntu-freak on 2009-01-16
I'm glad you got it sorted.
 
You should go to launchpad.net and tell them what you had to do in order to fix your resolution problem.

---

