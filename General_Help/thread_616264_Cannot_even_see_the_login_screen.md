---
title: "Cannot even see the login screen"
date: 2007-11-18
forum: General Help
---

### Post by tak1150 on 2007-11-18
Hi,

After I changed the login screen theme to "[Spread Firefox]("http://art.gnome.org/themes/gdm_greeter/744")", I logged out and couldn't log back in. It seemed like gdm would try to load the login screen, but couldn't (I saw the rotating mouse cursor for 1 second) and goes back to black screen. It repeats that cycle for a few times and reboots. After I turned it off completely, I still have the same problem. I cannot even get into virtual terminal (which I think is a known bug with gutsy). Does anybody have any solution?

One idea I had was to switch the login theme from something like Knoppix, but I don't know how to switch the login screen theme from command line. Thank you for your help!

Tak

---

### Post by Qwerty_ on 2007-11-18
Have you tried booting into recovery mode?

---

### Post by tak1150 on 2007-11-18
Thanks for replying.

I didn't even think of going into the recovery mode b/c I'm not used to seeing the Grub menu (my setting is only 2 sec and gone).

But I did manage to get it fixed. The following info for people with the same problem.

I used KNOPPIX to get into the HD, then mounted and changed the read/write permission (you can do this through right click).
In the terminal, I did:
```
sudo cp /media/hdc1/etc/gdm/gdm.conf /media/hdc1/etc/gdm/gdm.conf.backup
```
backup is a good thing.

```
sudo vim /media/hdc1/etc/gdm/gdm.conf
```
Then I changed
```
Greeter=/usr/lib/gdm/gdmgreeter
```
to
```
Greeter=/usr/lib/gdm/gdmlogin
```
Then
```
AutomaticLoginEnable=false
AutomaticLogin=myusername
```
to
```
AutomaticLoginEnable=false
AutomaticLogin=myusername
```
I also change the color (might as well :)) because I couldn't change the color of the background that shows up between the login and when Nautilus kicks in (the human skin color) even after I changed it in Login Window manager.
```
BackgroundColor=#356e7e
GraphicalThemedColor=#356e7e
```

Then I rebooted to boot to Ubuntu. It did the automatic login and bypassed the login greeter program which was crashing.

The moral of the story is:
[SIZE="4"]Don't use "Spread FireFox" theme for the login window in Gutsy![/SIZE]

I tried to reproduce the problem and I'm very sure that that particular login theme is the cause.

---

