---
title: "Point me in the right direction..."
date: 2006-11-03
forum: General Help
---

### Post by MrFSL on 2006-11-03
Hello all,
     I have been seeing alot about dock-type applications that mimic OSX's dock in funcitonality. I have compiled and ran most of the popular ones (kiba-dock, kxdocker, ksmoothdock, gnome-dock, gdesklets, adesklets, etc.) and, although these are all good programs in their own right they simply are not what I am looking for.

     After testing the above list of applications and monitoring system stability and memory usage (etc) for the last few weeks I find that either these programs are buggy, memory intensive, or just WAY TOO feature filled (for example: kiba-dock does everything that I DON'T need VERY WELL and not much of what I need at all).

     So after stepping back and pondering what exactly it is that I am trying to accomplish it occured to me that all I really want to do is use the standard gnome-panel like a dock, but I don't want it expanded from left to right I want it centered WITHOUT the hide menu buttons OR bars. It occurs to me that (given the age of gnome) that I am not the first to want this and there must be a patch or hidden config which will accomplish this.

     I have googled, I have searched, I have turned up nothing. Now I turn to you; can someone please help me remove those dang bars when the panel is not extended? :confused: 

Thank You.

MrFSL

(Also)
It seems to me that adding a few zooming effects, some nicer looking tooltips, and getting rid of those awful hide buttons/bars would give people the quintesential dock application and would eliminiate the need to create a new project from scratch and "reinvent the wheel."  Does anyone know why this project has never caught on? Some limitation in gnome-panel?
Thank you all again. This forum rocks. Best one I have ever seen and I came a LONG way on linux before I ever ended up on Ubuntu! This forum is one of the primary reasons that I shall stay Ubuntu!

---

### Post by 23meg on 2006-11-03
> all I really want to do is use the standard gnome-panel like a dock, but I don't want it expanded from left to right I want it centered WITHOUT the hide menu buttons OR bars. It occurs to me that (given the age of gnome) that I am not the first to want this and there must be a patch or hidden config which will accomplish this.You can have this by tweaking kiba-dock's options. Is there some other reason you want to avoid it?

---

### Post by MrFSL on 2006-11-03
Thank you very much for the quick reply...

I have tweaked the daylights out of kiba-dock (and again it is WONDERFUL software) however I can't seem to avoid a few things regardless of how I set it.

For instance, a big problem is the launchers not staying in a certain order. Using the "rope" model I can keep them in order but often times the "rope" then gets tangled and I have a big mess.

Kiba-dock also stays ontop of any application that I run full screen (a problem that I don't have with gnome-panel) - you can set it to autohide but the text (or tooltip - whathaveyou) is displayed whenever the cursor hovers about where the dock "used" to be before minimizing. This gets in the way of controls on the applications and is an annoyance. I could turn off the text entirely but for the type of computer setups that I do lets just say there needs to be a text/tooltip. 

If you know a way around these 2 issues that would be a start. It is also a plus that with standard panels I do not need to run a composite manager (aka xcompmgr, beryl, compiz, etc). 

Really this seems like someone MUST have done the same thing at one point in time.

Thanks again!

MrFSL

---

### Post by MrFSL on 2006-11-04
Update - I continued to scour google for answers. Finally when I searched for "gnome-panel ugly" I found more information (which just goes to prove the point that I am not alone in thinking these would be worthwhile to remove...

Ok, according to [this]("http://comments.gmane.org/gmane.comp.gnome.desktop/26847") these hide buttons are constants in the source. So I am asuming tha t there is no magic setting that will solve my issue.

A patch then -
As it is I suck at C/C++ ... and I am assuming that SOMEWHERE, SOMEONE has already addressed this...

Please help. At least someone point me to where in the source this is coded ... I can't make heads or tails out of it.

Respectfully,
MrFSL

---

### Post by kvonb on 2006-11-04
Let me know if you find the answer, I've been looking for the exact same thing for ages!

---

### Post by MrFSL on 2006-11-04
How about this...

The hide buttons themselves are theme-able yes? Perhaps can someone explain how I might create or modify a theme so that I can put in some transparent pngs or something to that nature? I looked at gone-look.org for themes that might have this feature but so far no luck.

Much oblidged,

MrFSL

---

### Post by MrFSL on 2006-11-05
Updates ...

I found this [site]("http://gnomethemes.org/forum/index.php?topic=67.0") that showed that talks about creating a ***.gtkrc-2.0*** file in your home directory. Doing this made all the handles on the TOP panel I use disappear (totally transparent) but did not make the "hide-button" handles disappear on my bottom panel!!

Perhaps all is not lost... does anyone know if you can modify this file to make the "hide-button" handles disappear for a non-Expanded panel?

ALSO ...
I found another forum (lost the address) where a person talks about modifying the source file *toplevel.c* for gnome-panel effectively setting the pixel size for these handles to 0. I am not clear but it seems that this causes some ill side-effects.

Does anyone have any more information about this? I downloaded the source for gnome-panel but still can't make heads or tails on what I am supposed to edit or where... or even how to recompile it correctly after I change it.

Hopefully someone out there can help. :-? 

MrFSL

---

### Post by kvonb on 2006-11-05
I was messing with ~/.themes/<current theme whatever its called>/gtkrc and there are a few things in there to play with.

---

### Post by MrFSL on 2006-11-05
@kvonb,

Will it is my understanding that you can either edit the themes or edit the .gtkrc-2.0 file and both have their advantages and disadvantages.

I found that this is a common subject on some development forums and had turned up as an official "bug" (grip handles not go to transparent with floating panel) more then 2 years ago...

Looks like none of the maintaners are interested in changing this. I like gnome-panel and I think it is very powerful and efficient. Really the issue I have is only asthetic but, when all the functionality and power are there... what is left but asthetics to improve on?

Like most people I made a transparent png file and applied it as background to an expanded lower panel. This looks alright unless I open any application or windows... especially with drop shadows enabled...

I seriously wish there was a fix. The alternatives are many but I would just as soon use gnome-panel for its utility. Now if only someone would help beautify it a bit I would be happier. :(

Thank you for your input and the time you have spent helping me with this.

---

### Post by kvonb on 2006-11-07
Have a look at my groovy desktop:

[http://ubuntuforums.org/gallery/showphoto.php?photo=3946&size=big&cat=500&ppuser=97068](http://ubuntuforums.org/gallery/showphoto.php?photo=3946&size=big&cat=500&ppuser=97068)

All the parts (icons, backgrounds, applets etc') are available on my server if you are interested:

[http://wamrfixit.homeip.net:8000/themes/](http://wamrfixit.homeip.net:8000/themes/)

You wouldn't believe that I'm the happier side of 40 with a desktop like that would you!  I got carried away with transparent images in GIMP.

Happy hacking :D

---

### Post by Mimsy on 2006-11-07
Oh... that's pretty. =P~ 

If I ever put ubuntu on a desktop computer, I might have to do that with it... just for the Oh! and Ah! effect when I show it to people. :) 

/Mimsy

---

### Post by LMP900 on 2006-11-07
> **MrFSL said:**
> [...]you can set it to autohide but the text (or tooltip - whathaveyou) is displayed whenever the cursor hovers about where the dock "used" to be before minimizing. This gets in the way of controls on the applications and is an annoyance.

I apologize in advance for not reading through the entire thread, so this might already be answered but here goes...

Firstly, I'm a Mac user, and with a little (okay, A LOT) of tweaking, I was able to make Kiba-Dock behave almost like OS X's dock. Your specific problem (quoted above) can be solved easily by changing the "Hide Area" to 0.0

Kiba-Dock is absolutely wonderful. Although the default settings are enough to scare away many innocent users wanting a simple dock (trust me, I ran away the first time I installed it), it is possible to make it behave properly. :)

---

### Post by kvonb on 2006-11-07
```
Oh... that's pretty.
```

...thankyou :D

---

### Post by Nonno Bassotto on 2006-12-01
> **LMP900 said:**
> I apologize in advance for not reading through the entire thread, so this might already be answered but here goes...

Firstly, I'm a Mac user, and with a little (okay, A LOT) of tweaking, I was able to make Kiba-Dock behave almost like OS X's dock. Your specific problem (quoted above) can be solved easily by changing the "Hide Area" to 0.0

Kiba-Dock is absolutely wonderful. Although the default settings are enough to scare away many innocent users wanting a simple dock (trust me, I ran away the first time I installed it), it is possible to make it behave properly. :)

Could you please post here you settings? I wasn't able to make kiba-dock do anything reasonable.

---

