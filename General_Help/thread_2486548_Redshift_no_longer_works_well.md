---
title: "Redshift no longer works well"
date: 2023-05-03
forum: General Help
---

### Post by jonfisher on 2023-05-03
Ubuntu 22.04.2 LTS

I use to use Redshift to help eye strain (at night); however, Redshift often crashes/quits as soon as I open it now.  Any thoughts on this?

Also, are there any similar programs in the Ubuntu Software Center ?

---

### Post by guiverc on 2023-05-03
I've used Redshift since Ubuntu 15.04 (*when I discovered it, and added it back to 14.04 LTS too*), and have noted no problems with it from then, to my current install (*which is now mantic; or the current development release*). What I still suggest checking is the following

- ensure you have only one redshift running; you'll have problems if more than once instance of a redshift is running  (ie. *you can have it autostart with a selection option, but I've found it clumsy as you can also tell it to start elsewhere too & thus end up with two copies running & they interfere with each other*)
- the same applies if redshift plus another like program is also running, Ubuntu Desktop uses GNOME, which includes [GNOME's Night Light]("https://help.gnome.org/users/gnome-help/stable/display-night-light.html.en") so ensure that's turned off; they'll both work badly if both are running..

I've not configured redshift in years (*so I won't be any help there*)... as I'm still using the config I made back on Ubuntu 15.04 (*with only minor tweaks* *to suit room lighting changes*).  FYI:  My setup includes Lubuntu/LXQt, Xubuntu/Xfce & Ubuntu Desktop (GNOME) and use redshift as the same config works regardless of which DE/WM I choose to use for my session..

---

### Post by jonfisher on 2023-05-03
> **guiverc said:**
> I've used Redshift since Ubuntu 15.04 (*when I discovered it, and added it back to 14.04 LTS too*), and have noted no problems with it from then, to my current install (*which is now mantic; or the current development release*). What I still suggest checking is the following

- ensure you have only one redshift running; you'll have problems if more than once instance of a redshift is running  (ie. *you can have it autostart with a selection option, but I've found it clumsy as you can also tell it to start elsewhere too & thus end up with two copies running & they interfere with each other*)
- the same applies if redshift plus another like program is also running, Ubuntu Desktop uses GNOME, which includes [GNOME's Night Light]("https://help.gnome.org/users/gnome-help/stable/display-night-light.html.en") so ensure that's turned off; they'll both work badly if both are running..

I've not configured redshift in years (*so I won't be any help there*)... as I'm still using the config I made back on Ubuntu 15.04 (*with only minor tweaks* *to suit room lighting changes*).  FYI:  My setup includes Lubuntu/LXQt, Xubuntu/Xfce & Ubuntu Desktop (GNOME) and use redshift as the same config works regardless of which DE/WM I choose to use for my session..

I unistalled it and installed Gamastep Indicator, which looks like the  same logo/icon - it crashes upon opening, as RedShift does now.  I  just doesn't seem to work either....

If anyone can suggest a program that does what they are suppose to do, it would be much appreciated.

---

### Post by guiverc on 2023-05-03
Are you using Wayland or Xorg?

Redshift to my understanding only support Xorg, and whilst Gammastep provides very limited Wayland support; it's only provided in a very limited way.  GNOME Night Light would be my recommendation if using Wayland.

---

### Post by jonfisher on 2023-05-04
I'm using Ubuntu 22.x LTS   Wayland.
I'll try Night Light
Couldn't find it in Ubuntu soft. ctr. or Synaptic pckg. manager - have a link for it?

---

### Post by guiverc on 2023-05-04
> **jonfisher said:**
> I'm using Ubuntu 22.x LTS   Wayland.
I'll try Night Light
Couldn't find it in Ubuntu soft. ctr. or Synaptic pckg. manager - have a link for it?

Ubuntu 22.04 or the 2022-April release is the LTS (22.04 = 2022.April using the *year.month* format used by Ubuntu).  Ubuntu 22.10 is the first of the releases in the *development* cycle that will conclude with the next LTS which is Ubuntu 24.04 LTS (ie. three *snapshot* releases are providing being 22.10, 23.04 & 23.10 before final LTS concludes the two year development cycle).  22.x makes no sense to me with two different *two year* cycles ending & starting in 2022.

GNOME includes Night Light by default, so nothing needs be installed.

Note:  As I have multiple desktops on my system, I just ensured GNOME's Night Light was off on my system so redshift (*which works on all my installed desktops*) worked correctly; I can't recall if it's *enabled* or *disabled* by default (I'm also mostly using Xorg; esp. given I mostly use LXQt or Xfce).

---

### Post by Dennis N on 2023-05-04
> I'll try Night Light
Couldn't find it in Ubuntu soft. ctr. or Synaptic pckg. manager - have a link for it? 
You'll find it in Settings > Displays
See the screen shots.
Once set up as you want, there is a toggle switch to easily activate/deactivate in the quick settings menu.

---

### Post by aug7744 on 2023-05-04
Redshift not run in wayland.

---

### Post by MAFoElffen on 2023-05-04
Please let up on him. 

I can confirm that RedShift stopped working for me 2 nights ago on my Lenovo laptop. That is before he started this thread started.

I noticed it wasn't working. I have not looked into the why yet. All my settings say it is on and nothing has changed. But it is definitely not working for me. This problem affects me also. He is not alone.

---

### Post by ajgreeny on 2023-05-04
Once or twice in the past I found redshift didn't run, or didn't change the colour temp or gamma values as it had but it turned out to be geoclue that was the problem, not redshift itself.

Changing the redshift configuration to manual location detection worked straight away and I have left it as manual. 
I wonder if you are using manual or geoclue location.  If the latter change to manual giving the longitude and latitude of your location and all may work again.

I have to admit that I have not actually checked if my redshift is working and have said a&#314;l this using an Android tablet  not my Xubuntu machine.  I will check tomorrow and report back.

---

### Post by MAFoElffen on 2023-05-05
??? ==> Tonight when I got home, it is working again. The icon is in the upper right tray. It says night light is on. I don't know. I changed 'nothing'

I can not confirm now that it has a problem now... That is just strange.

---

### Post by ajgreeny on 2023-05-05
> **MAFoElffen said:**
> ??? ==> Tonight when I got home, it is working again. The icon is in the upper right tray. It says night light is on. I don't know. I changed 'nothing'

I can not confirm now that it has a problem now... That is just strange.

Just wanting to check that you are still talking about **Redshift** and not **Night Light** which is used in the default gnome system.

---

### Post by Dennis N on 2023-05-05
Just wondering - could Redshift use in Gnome have some conflict with Night Light?  
It's been a long time since I used Redshift, and that was back when I used Xubuntu. I could be wrong but based on what I remember, Redshift in Xubuntu and Night Light in Gnome have the same functionality. If anyone knows of some difference that makes Redshift preferable in Gnome, I'd like to know.

---

### Post by jonfisher on 2023-05-07
Thanks, marking as solved

---

### Post by ajgreeny on 2023-05-08
Please tell us the solution or this whole thread is no help to other users.

---

