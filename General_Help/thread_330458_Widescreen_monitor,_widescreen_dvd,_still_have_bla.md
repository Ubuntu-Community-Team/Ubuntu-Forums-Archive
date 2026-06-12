---
title: "Widescreen monitor, widescreen dvd, still have black borders"
date: 2007-01-03
forum: General Help
---

### Post by Levander on 2007-01-03
I've got a wide-screen monitor and I'm watching a wide-screen DVD.  I've tried this under totex, gxine, and gmplayer.  All three, there's still a black border around the video image.  

I thought that if you had a monitor with a 16:9 (well, 16:10 in my case) aspect resolution on your monitor, you didn't get the black bars on top and bottom of your video like you did with an older style 4:3 aspect ratio television.

Can I get rid of the black borders?

---

### Post by goatflyer on 2007-01-03
What does System>Preferences>Screen Resolution say? 

Widescreen monitors try to 'adapt' to whatever signal is being put out by your video card/chipset.  Thats why icons and text can sometimes look short and fat on a widescreen monitor.

If your screen-resolution does not match your monitor's capability I would recommend the tried-and-true:

```

sudo dpkg-reconfigure xserver-xorg

```

and work through the questions (just answer the default to everything) until you get to the screen resolutions and make sure your monitor's resolution (I'm guessing 1440x900) is selected.

Also: be sure that the DVD is actually made for true widescreen format - sometimes the black bars are actually part of the signal on the DVD!!!

---

### Post by Levander on 2007-01-03
Yeah, System -> Preferences -> Screen Resolution says 1680 x 1050 @ 60 Hz, which is the native resolution on the LCD.

I have no idea how to make sure the DVD is "true" wide-screen format, it's just a copy of Sling Blade I bought a few years ago that says WIDE SCREEN in a banner on top of the box cover.

---

### Post by goatflyer on 2007-01-03
Okay, good! (your resolution is set properly)

So goto Applications>Sound & Video>Movie Player  (which is totem)

Then View>Aspect Ratio  select 16:9

Then Movie>Play Disc>DVD-ROM drive

this should work for you.

Also, try toggling between Full Screen and window.  If the black bars appear even in the window, then the black bars are really on the DVD signal, then there is only one hope left.

On the actual dvd menu (the one put in by the movie studio) they may have a menu which lets you select different formats.  The black bands could be coming from there.

---

### Post by Levander on 2007-01-04
I've played with the aspect ratio.  It is wierd that the DVD says Widescreen on it, but that when the opion in that menu says "Auto", the video looks the same as it does when that option says 4:3.  But, I tell you, comparing the video to another DVD I have that doesn't say Widescreen on it - the video "looks" 16:9 to me.

I can't figure out how to get into the DVD's menu.  In totem there's Go -> DVD Menu, but it does nothing.  I've played around with it, put the movie on pause, nothing.  In gxine (which is what I plan to use to watch movies in the future because totem can only play a dvd when you insert the disc into the drive, can't navigate to the DVD after it's already been put into the drive) I see no way whatsoever to get into the menu.

---

### Post by darrenm on 2007-01-04
There are many different types of widescreen. 16:9 isnt the only one. You very rarey get a DVD to play at the correct aspect without bars.

---

### Post by goatflyer on 2007-01-04
totem can play dvds that have been previously inserted (prior to starting totem) .  Its just when you previously inserted it the gnome automounter mounted it as /media/cdrom1 (for example).  From the totem menu, just Movie>Open and select where gnome auto-mounted your dvd.

The Go>DVD Menu takes you to the dvd menu, if there is one registered on that dvd.  I pop in my Fellowship of the Ring DVD, and even the Chapter Menu works.  Maybe your particular movie doesn't have a menu, it just plays.  Or, just scan through the Next Chapter<>Prev Chapter until you find the screen saying Special Features/Options/Play Movie

As for top and bottom bars when watching fullscreen, yes I can see them they are there (but fairly thin) and the undistorted picture goes from edge to edge on the widescreen display (cheap Samsung 941)  I suspect the bars are there because the movie image of LoTR is wider than 16:9

16:9 is less than 2:1, yet the LoTR is definitely wider than twice the height.  Maybe even widescreen is just not wide enough....

(Hey Santa, how about an IMAX monitor next christmas?)

EDIT:
I just checked, the resolution in LoTR (and maybe many other movies) is 2.1:1, not 16:9, so for sure we will still have to live with some bars until they make yet wider displays.

---

### Post by Levander on 2007-01-04
How did you check the resolution for Lord of the Rings?

---

### Post by goatflyer on 2007-01-04
>How did you check the resolution for Lord of the Rings?

The low-tech way.  I held up a pencil along the left edge of the screen and measured the height.  Then I held the pencil horizontally and counted 'pencil lengths'.  It was 2 and a bit...

;)

---

