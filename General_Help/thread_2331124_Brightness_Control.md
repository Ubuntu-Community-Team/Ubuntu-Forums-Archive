---
title: "Brightness Control"
date: 2016-07-18
forum: General Help
---

### Post by Jason_Hunter on 2016-07-18
Isn't there supposed to be a general brightness control in Ubuntu?

My desktop is quite bright enough, but playing videos is a little bit too dark; In dark scenes I can't really make out what's happening. 

We don't have a general brightness controll in like control panel?

I've got a Radeon R9 270x on ubuntu-16.04

---

### Post by sysone on 2016-07-18
System Settings  --->  Power  ----->  brightness

---

### Post by Jason_Hunter on 2016-07-18
I don't have that in there. See attached image. [IMG]http://imgur.com/LPrfbfZ[/IMG]

[http://imgur.com/LPrfbfZ](http://imgur.com/LPrfbfZ)

---

### Post by Jason_Hunter on 2016-07-18
Oh, right, yeah, I'm using gnome;)

---

### Post by Geoffrey_Arndt on 2016-07-18
That doesn't look like the Unity Desktop - which is the default in Ubuntu.    What distro and desktop are you running?

EDIT -  . . . OK, so, get the Gnome Settings tool (I forget what they call it, but it should have more options)

---

### Post by Jason_Hunter on 2016-07-19
ok, so it's not there; where can I get help with this problem, then? Any idea?

---

### Post by deadflowr on 2016-07-19
Gnome or Unity should not not matter.
What matters is whether or not your system has the ability to enable the parameters to use the brightness function.

If laptop, then it should, but might need a parameter to be set at boot.
If a tower/desktop, then more likely it is not an option to enable.
As far as this goes, you would need to provide more information about you set up for anyone to be able to actually give you advice.


An alternative is to apply an xrandr setting to increase or decrease to brightness.
To use, first run
```
xrandr
```
look at the name for the connected device, usually something like VGA-0,
then to use this to change the brightness run this command:
```
xrandr --output VGA-0 --brightness 1.0
```
Changing the name of the output to whatever the name your xrandr lists as the connected device name, of course.

brightness of 1 is the default, and to increase or decrease add or subtract .1 to that,

example: to increase change it to 1.1 or 1.2 or 1.3 and so on, 
and to decrease change it to 0.9 or 0.8 or 0.7 and so on.

Resetting to 1 will reset it back to the default.


Another alternative is to see if the brightness control extension helps;
see here: [https://extensions.gnome.org/extension/231/brightness-control/]("https://extensions.gnome.org/extension/231/brightness-control/")

So basically those are 3 options, 
1) find out if their is a simple boot parameter you can/need to set.
2)use a simple xrandr command to adjust the setting
3) try the brightness control add-on for gnome.

When thinking about it, I'd go with the gnome extension first, as that takes almost no time to install and get up and running.

Hope it helps

---

### Post by Jason_Hunter on 2016-07-19
Right, thanks, this xrandr command changed the brightness and made the movies more lit up: 

xrandr --output HDMI-0  --brightness 1.3

, but it also changed the color of my desktop, quite drastically, almost to the point of not being able to read text.

My desktop has never really been too dark, it's just movies, so maybe I'm looking for something else, to just change brightness of videos?

Also, this gnome plugin is 2 years old and doesn't seem to work. Isn't this supposed to be something that is installed out of the box?

And yes, I run a desktop computer, not a laptop.

I'm viewing the movies in Chrome. 

Hmm, I'm not really sure something is happening to the brightness of the movies. I tried running the same movie part over and over using different brightness settings, but I don't think I see a difference.

Ok, I've looked at it some more and it seems there's no difference here; the xrandr command only changes brightness of the desktop, but not of the movie.

---

### Post by DragonBoy on 2016-07-19
Make sure you have all he latest updates (sudo apt-get update & sudo apt-get upgrade)

Also go to the following:

System Settings < Brightness & Lock 

There is a Brightness bar that you can adjust. Also maybe uncheck the "Dim Screen to save power" box. Good luck!

---

### Post by deadflowr on 2016-07-19
> I'm viewing the movies in Chrome. 
Not sure what that means, but perhaps look into the player in chrome for it's settings.
Some players have settings to adjust the brightness in the player directly.

---

### Post by Jason_Hunter on 2016-07-20
Do you see the "Brightness & Lock" in this image:?

[http://imgur.com/LPrfbfZ](http://imgur.com/LPrfbfZ)

---

### Post by Jason_Hunter on 2016-07-20
> **deadflowr said:**
> Not sure what that means, but perhaps look into the player in chrome for it's settings.
Some players have settings to adjust the brightness in the player directly.

This means I'm playing movies in the Chrome web browser. 

I do however see brightness change with xrandr when using Totem.

---

### Post by Jason_Hunter on 2016-07-24
So, nobody has any idea what's going on here?

What's the next step? Can't this thread be moved up in a way?

---

### Post by sizzlineggs on 2016-07-25
I'm having a similar issue.  My brightness is fine but when I play a video with something like vlc the screen immediately dims and the video becomes much to dark.  I also don't have a slider or any control over brightness in the power & lock settings.  I'm on a desktop though.

---

### Post by Jason_Hunter on 2016-07-25
Seems we are not the only ones;) There even a plugin to control brightness in Chrome videos: 

[https://github.com/dixoncheng/video-brightness-chrome/issues/1](https://github.com/dixoncheng/video-brightness-chrome/issues/1)

So, it seems Chrome has its own video brightness controls. 

I have not installed this plugin yet and tried, but I will soon.

---

### Post by Jason_Hunter on 2016-07-25
Oh, you're talking about vlc; I haven't tried if that's got its own brightness, but will try later

---

