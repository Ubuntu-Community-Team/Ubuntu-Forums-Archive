---
title: "Automatic Login not working on 17.10"
date: 2017-09-30
forum: General Help
---

### Post by darran-kelinske on 2017-09-30
I have automatic login configured on my 17.10 install with the latest packages and each time I reboot I have to login with my account credentials. Does anyone know how to fix this? Thank you!

---

### Post by olsooty on 2017-10-02
hello,

have same issue. I can configure my account - enable automatic login in "system setting - users". But after system restart automatic login is not working (need to write password).

---

### Post by mc4man on 2017-10-02
Works fine here when checking (don't use as certain keyrings I use aren't unlocked on auto login). Tried with both a ubuntu & ubuntu-xorg sessions, both fine.
What's the genesis of your install? (i.e. new fresh or an install with some age or upgrade from 17.04

---

### Post by mc4man on 2017-10-02
> **olsooty said:**
> hello,

have same issue. I can configure my account - enable automatic login in "[COLOR="#0000CD"]system setting - users[/COLOR]". But after system restart automatic login is not working (need to write password).

What are you using?, the current location would be Settings > Details > Users in Ubuntu

---

### Post by ppetterr on 2017-10-03
Hello,
do you have NVIDIA graphic card? If yes, try to use Nouveau driver instead of NVIDIA driver and let us know (this helps in my case).

Best regards,
Peter

---

### Post by olsooty on 2017-10-03
Hello, in my case i have freshly installed daily build of 17.10. Installed on dell mobile workstation (precision m4700, with nvidia quadro k1000 graphic card) from usb stick.

I changed binary driver to open and after that i restarted OS. All was fine (no password or whatever needed)! After screen was loaded i checked system settings-details-accounts-users but automatic login was off (switch was on left side, which means that AL is disabled). So i opened locked settings with button situated in right upper corner of window, writed down my pass and pulled switch to right side, signed as enabled AL. After that i restarted OS. But now login screen appears again (with open nvidia driver). Maybe is some problem between graphics and AL. I will try switch off discrete graphic and try run OS on intel integrated graphic.

Sorry for my english, i use it only on christmas :-)

---

### Post by mc4man on 2017-10-03
> **olsooty said:**
> Hello, in my case i have freshly installed daily build of 17.10. Installed on dell mobile workstation (precision m4700, with nvidia quadro k1000 graphic card) from usb stick.

I changed binary driver to open and after that i restarted OS. All was fine (no password or whatever needed)! After screen was loaded i checked system settings-details-accounts-users but automatic login was off (switch was on left side, which means that AL is disabled). So i opened locked settings with button situated in right upper corner of window, writed down my pass and pulled switch to right side, signed as enabled AL. After that i restarted OS. But now login screen appears again (with open nvidia driver). Maybe is some problem between graphics and AL. I will try switch off discrete graphic and try run OS on intel integrated graphic.

Sorry for my english, i use it only on christmas :-)

Works for me  with a nvidia mobile (GeForce GT 755M) but at least here the 'switch' is to the left side though it would also just say either On or Off,  does your's say On (no idea if that screen gets translated..
I'd give you a screen shot but at the moment the forum isn't allowing me to do so.

---

### Post by olsooty on 2017-10-03
[ATTACH=CONFIG]276956[/ATTACH]

see attachment

---

### Post by jbicha on 2017-10-03
olsooty, that screenshot shows that Automatic Login is turned off. Click the Unlock button in the top right of the Settings window. Then turn the switch on next to Automatic Login.

---

### Post by olsooty on 2017-10-03
> **jbicha said:**
> olsooty, that screenshot shows that Automatic Login is turned off. Click the Unlock button in the top right of the Settings window. Then turn the switch on next to Automatic Login.

yes, you are right. Now looks that AL is turned off. When i will unlock button (write password, button will be green and i can change switch) and will turn the switch on and close window the next reboot and login will be NOT automatic. I will must again write password. And if i will check the switch after that it will be again on left side (turned off).
It will looks like i didnt made any changes in AL setup.

Im common user, but for me looks like changes in AL (off/on) are not saving. Duno why.

---

### Post by jbicha on 2017-10-03
olsooty, could you paste or attach the contents of
```
/etc/gdm3/custom.conf
```

---

### Post by mc4man on 2017-10-03
n.a. only on a moded installed was twice needed

---

### Post by olsooty on 2017-10-04
> **jbicha said:**
> olsooty, could you paste or attach the contents of
```
/etc/gdm3/custom.conf
```

ok, will do after work, ty

---

### Post by olsooty on 2017-10-04
> **jbicha said:**
> olsooty, could you paste or attach the contents of
```
/etc/gdm3/custom.conf
```

here:
```
# GDM configuration storage
#
# See /usr/share/gdm/gdm.schemas for a list of available options.

[daemon]
AutomaticLoginEnable=True
AutomaticLogin=alois

# Uncoment the line below to force the login screen to use Xorg
#WaylandEnable=false

# Enabling automatic login

# Enabling timed login
#  TimedLoginEnable = true
#  TimedLogin = user1
#  TimedLoginDelay = 10

[security]

[xdmcp]

[chooser]

[debug]
# Uncomment the line below to turn on debugging
# More verbose logs
# Additionally lets the X server dump core if it crashes
#Enable=true


```

---

### Post by olsooty on 2017-10-04
and system setting looks like in attachement

---

### Post by mc4man on 2017-10-04
The only thing that matters is what /etc/gdm3/custom.conf has. It seems on a new updated install that after setting alo to on,  after a reboot the settings panel will always show off. But aol is still enabled & working. 
On a sightly different install the settings panel always reports the actual setting.
Can maybe be seen in the 2 screens, button to the right means on, button to the left means off but in both installs aol is enabled & does work

@olsooty your custom.conf looks deficient, should be like screen3 after you enable alo. Have you checked the file right after setting alo to on in the settings panel?

---

### Post by mc4man on 2017-10-05
The weird thing about Gnome's design  for  settings is it looks & acts like a switch but really it's a cover.
(- i.e. whatever you uncover is enabled, what you cover up is disabled.
I think they could have done a better job there..

---

### Post by olsooty on 2017-10-05
ok, because im not patient patient i downloaded ubuntu 17.10 beta 2 (i had installed daily build 17.10 before).
I created bootable usb stick again with beta 2 and installed 15min ago over existing 17.10 (reinstall).
So now im running on 17.10 beta2 and custom.conf looks like:
```
# GDM configuration storage
#
# See /usr/share/gdm/gdm.schemas for a list of available options.

[daemon]
AutomaticLoginEnable=true
AutomaticLogin=alois

# Uncoment the line below to force the login screen to use Xorg
#WaylandEnable=false

# Enabling automatic login

# Enabling timed login
#  TimedLoginEnable = true
#  TimedLogin = user1
#  TimedLoginDelay = 10

[security]

[xdmcp]

[chooser]

[debug]
# Uncomment the line below to turn on debugging
# More verbose logs
# Additionally lets the X server dump core if it crashes
#Enable=true


```

during installation beta2, when i wrote name of user, name of machine and password, i marked "automatic login" (was written in my language, idk if my translate is exact)
im using open nvidia drivers now and system is not up-to-date

NOW ITS "AL" WORKING FINE!!! \\:D/

now im going to update my system and after that i would like to try binary nvidia driver (would like to test my favourite game via wine emulator)

i will come back after this :-)

system settings looks like in attachement (i didnt change anything here):

---

### Post by mc4man on 2017-10-05
> **olsooty said:**
> ok, because im not patient patient i downloaded ubuntu 17.10 beta 2 (i had installed daily build 17.10 before).
I created bootable usb stick again with beta 2 and installed 15min ago over existing 17.10 (reinstall).


NOW ITS "AL" WORKING FINE!!! \\:D/

Yeah it should because as mentioned the .conf file is what matters.
Apparently the settings panel will always show the default (off) not the actual setting

---

### Post by olsooty on 2017-10-05
ok im back

so automatic login dont work together with nvidia binary drivers (closed)
simple change back from binary to open noveau driver, restart and all is fine
duno if this problem is caused only by nvidia K1000M series graphics or its wider, who knows

im stayin with open source drivers and will see

---

### Post by mc4man on 2017-10-05
> **olsooty said:**
> ok im back

so automatic login dont work together with nvidia binary drivers (closed)
simple change back from binary to open noveau driver, restart and all is fine
duno if this problem is caused only by nvidia K1000M series graphics or its wider, who knows

im stayin with open source drivers and will see
That was mentioned in post 5 so seems to affect Desktop Gpu machines as it isn't an issue with laptops (at least with nvidia via nvidia-prime

---

### Post by darran-kelinske on 2017-10-06
I did this in console and now automatic login works:

xhost +si:localuser:root

---

### Post by orangereaper on 2017-10-21
The following sequence fixed this form me.
[LIST=1]
[*]*in **Settings -> Details -> Users** switch off automatic login. *
[*]*Then logoff.*
[*]* Log Back in. *
[*]*Re-enable automatic login.*
[*]* reboot.*
[/LIST]

---

### Post by cariboo on 2017-10-21
Moved, as artful has been released.

---

### Post by dmitrijddd on 2017-10-22
> **orangereaper said:**
> The following sequence fixed this form me.
[LIST=1]
[*]*in **Settings -> Details -> Users** switch off automatic login. *
[*]*Then logoff.*
[*]* Log Back in. *
[*]*Re-enable automatic login.*
[*]* reboot.*
[/LIST]



does not work for me :(

---

### Post by superkid333 on 2017-10-25
Hi,
I am still having the same issue, where I cannot automatically login. I have tried editing the /etc/gdm3/custom.conf file to "AutomaticLoginEnable=true". Another forum suggested it needed to be lowercase "true" as opposed to "True". I tried both and neither work. I still have to put in my password when I log in. 

I am on a laptop, and I use the Nvidia drivers. Here is the code from my config file:
```

# GDM configuration storage
#
# See /usr/share/gdm/gdm.schemas for a list of available options.


[daemon]
# Uncoment the line below to force the login screen to use Xorg
#WaylandEnable=false


# Enabling automatic login
AutomaticLoginEnable=true
AutomaticLogin=superkid


# Enabling timed login
#  TimedLoginEnable = true
#  TimedLogin = user1
#  TimedLoginDelay = 10


#AutomaticLoginEnable=True
#AutomaticLogin=superkid


[security]


[xdmcp]


[chooser]


[debug]
# Uncomment the line below to turn on debugging
# More verbose logs
# Additionally lets the X server dump core if it crashes
#Enable=true

```

I have also included screen shots. I am aware of the cover vs switch issue and it appears to be set up properly.

---

### Post by AvatarGG on 2017-10-28
> **superkid333 said:**
> Hi,
I am still having the same issue, where I cannot automatically login. I have tried editing the /etc/gdm3/custom.conf file to "AutomaticLoginEnable=true". Another forum suggested it needed to be lowercase "true" as opposed to "True". I tried both and neither work. I still have to put in my password when I log in. 

I am on a laptop, and I use the Nvidia drivers. Here is the code from my config file:
```

# GDM configuration storage
#
# See /usr/share/gdm/gdm.schemas for a list of available options.


[daemon]
# Uncoment the line below to force the login screen to use Xorg
#WaylandEnable=false


# Enabling automatic login
AutomaticLoginEnable=true
AutomaticLogin=superkid


# Enabling timed login
#  TimedLoginEnable = true
#  TimedLogin = user1
#  TimedLoginDelay = 10


#AutomaticLoginEnable=True
#AutomaticLogin=superkid


[security]


[xdmcp]


[chooser]


[debug]
# Uncomment the line below to turn on debugging
# More verbose logs
# Additionally lets the X server dump core if it crashes
#Enable=true

```

I have also included screen shots. I am aware of the cover vs switch issue and it appears to be set up properly.

Same problem here.

---

### Post by yakov81 on 2017-10-30
Auto login not working in 17.10 (in 16.04 AL work fine) GPU: 908Ti nvidia (384.90 ver)

---

### Post by superkid333 on 2017-10-31
Just as an update, I am still experiencing this problem. I have yet to find a solution. Can anyone help?

---

### Post by Tulsapoke on 2017-10-31
I also have this annoying problem. I would just like to know that it has been logged as an official bug. 

It's already bad enough that when it does "auto login" with the open driver that you still have to swipe up with the mouse to open the screen due to the gnome curtain. So far I am recommending for my friends and family to hold off on upgrading due to the horrendous screen wake issues.

---

### Post by dchirva on 2017-11-06
Hey there.
Got the same problem when I use nvidia prop. drivers.
Autologin works fine as soon as I switched to opensource video drivers.

Looks like this is a nvidia fault.

---

### Post by #&amp;thj^% on 2017-11-06
Can someone here show me their "/etc/gdm3/custom.conf" file please.
EDIT: **with the Nvidia Driver installed.**
```
gedit /etc/gdm3/custom.conf
```

---

### Post by superkid333 on 2017-11-07
> **dchirva said:**
> Hey there.
Got the same problem when I use nvidia prop. drivers.
Autologin works fine as soon as I switched to opensource video drivers.

Looks like this is a nvidia fault.

I also changed to the opensource drivers and the problem is solved. This is an Nvidia bug. If you're using Nvidia, you will not be able to use the auto-login option. Switch to the opensource drivers.

---

### Post by AvatarGG on 2017-11-07
> **1fallen said:**
> Can someone here show me their "/etc/gdm3/custom.conf" file please.
EDIT: **with the Nvidia Driver installed.**
```
gedit /etc/gdm3/custom.conf
```

```
# GDM configuration storage#
# See /usr/share/gdm/gdm.schemas for a list of available options.


[daemon]
# Uncoment the line below to force the login screen to use Xorg
#WaylandEnable=false


# Enabling automatic login
#  AutomaticLoginEnable = true
#  AutomaticLogin = user1


# Enabling timed login
#  TimedLoginEnable = true
#  TimedLogin = user1
#  TimedLoginDelay = 10


AutomaticLoginEnable=True
AutomaticLogin=carlos


[security]


[xdmcp]


[chooser]


[debug]
# Uncomment the line below to turn on debugging
# More verbose logs
# Additionally lets the X server dump core if it crashes
#Enable=true



```

---

### Post by bardo2 on 2017-11-09
Hey, guys,  this may not be the final solution, but it is a viable workaround, that i am using on several boxes already: In the file /etc/gdm3/custom.conf just uncomment the line WaylandEnable=false and reboot.  autologin is working!

---

### Post by #&amp;thj^% on 2017-11-09
> **AvatarGG said:**
> ```
# GDM configuration storage#
# See /usr/share/gdm/gdm.schemas for a list of available options.


[daemon]
# Uncoment the line below to force the login screen to use Xorg
#WaylandEnable=false


# Enabling automatic login
#  AutomaticLoginEnable = true
#  AutomaticLogin = user1


# Enabling timed login
#  TimedLoginEnable = true
#  TimedLogin = user1
#  TimedLoginDelay = 10


AutomaticLoginEnable=True
AutomaticLogin=carlos


[security]


[xdmcp]


[chooser]


[debug]
# Uncomment the line below to turn on debugging
# More verbose logs
# Additionally lets the X server dump core if it crashes
#Enable=true



```
AvatarGG  is this with the Nvidia Driver Installed?
Thanks remove the "#" from:
```
#  AutomaticLoginEnable = true
```
So it now Looks like this:
```
AutomaticLoginEnable = true
```
and make sure the username is is your user  name (Login Name) 
And Remove the "#" there also. Like this
```
AutomaticLogin = user1
```
Where user1 is your user name.

EDIT: I just realized that I also have the Wayland Option Like this:
```
WaylandEnable=false
```
I did this a few months back so it wasn't fresh in my memory.

---

### Post by AvatarGG on 2017-11-10
> **1fallen said:**
> AvatarGG  is this with the Nvidia Driver Installed?

Yes, it is.

> 
Thanks remove the "#" from:
```
#  AutomaticLoginEnable = true
```
So it now Looks like this:
```
AutomaticLoginEnable = true
```
and make sure the username is is your user  name (Login Name) 
And Remove the "#" there also. Like this
```
AutomaticLogin = user1
```
Where user1 is your user name.


As you can see, I already did that. Please read the full file contents.

> 
EDIT: I just realized that I also have the Wayland Option Like this:
```
WaylandEnable=false
```
I did this a few months back so it wasn't fresh in my memory.

Thanks, will try this!

---

### Post by Tulsapoke on 2017-11-19
I have tried all these tricks to get the automatic login to work to no avail.  Also I have tried (every trick I can find) to get the daym Gnome curtain to stop requiring me to awkwardly swipe up with the mouse every time my screen goes to sleep to save energy.  These may not be horrendous/damaging bugs but they are the most annoying Ubuntu bugs I can ever remember.  I literally get users complaining about this on their pc's every single day.

---

### Post by parrenin-ujf on 2017-11-19
I had this problem on ubuntu 17.10 with the nvidia driver.
I solved it by setting:
WaylandEnable=False
in /etc/gdm3/custom.conf

---

### Post by e.bilko on 2017-11-20
It's not just nvidia cards - I installed an old AMD Radieon GFX card this afternoon and the same, really, annoying problem happened.
I log out and logged back in using Xorg from the GUI user log in screen (the option is in the cog wheel by the log in button) and it fixed it.
Just ANOTHER problem with Wayland, to add to a huge list...

---

### Post by gofman-mike on 2017-12-02
Not working for me either. NVidia proprietary drivers needed for CUDA. I modified /etc/gdm3/custom.conf as suggested. Still booting to login screen. 
```
AutomaticLoginEnable=True
AutomaticLoginEnable=<myusername>
WaylandEnable=false
```

UPD: I had XFCE4 environment installed as well as a login choice. I have removed it since and auto login still not working. Still prompting to login. 

What makes matters worse is that Vine does not allow any VNC connections until I login on the physical machine. This renders my Ubuntu machine unusable in headless mode. 
Very disappointed with this version of Ubuntu.

---

### Post by jimav on 2017-12-14
> **jbicha said:**
> olsooty, that screenshot shows that Automatic Login is turned off. ...

It is** turning itself off** after every reboot. 

I clicked Unlock, entered my pw and set the Automatic Login switch to ON.  Closed the dialog,  Re-started the *Users* dialog and confirmed that the setting was still there.  But after reboot, I had to enter my password, and the switch had turned itself off.


This worked fine in 16.04.

---

### Post by Drew_Lustro on 2017-12-20
:( **Apparently this is a known bug if you are using Nvidia proprietary drivers and thus, non-Wayland session.**

*Tracking here: *[https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1719128?comments=all](https://bugs.launchpad.net/ubuntu/+source/gdm3/+bug/1719128?comments=all)

---

