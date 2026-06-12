---
title: "nvidia-settings and &quot;separarte-x-screen&quot;"
date: 2008-04-25
forum: General Help
---

### Post by Tombigel on 2008-04-25
I hope it's the right forum to ask -

I set up a dual monitor system with 8.04 using nvidia-settings.

Worked like a charm, with compiz and everything.

I played with the options a bit and came across the "separate-x-screen" option and now I'm using it.

I'm trying to understand what exactly it means to work with 2 X screens -
Is it like "Dual View" on Windows? Are the 2 X systems are 2 different sessions? can I move an application between them? what happens if I run the same app on both Xs? 

I tried to google for some info but couldn't find a comprehensive explanation for the "noob".

---

### Post by Zorael on 2008-04-26
There is no equavilence. :>

The 'extend desktop to this screen' option available in Windows is the same as DualView (or TwinView or whatever it's called), and Xinerama.

When it's a separate X session, whatever applications are running there cannot be moved onto the other one. It is not an extension of your desktop, it is *another* desktop.

---

### Post by Nythain on 2008-04-26
aye, seperate-x-screens are pretty much two different desktops... this works a little odd, since they will both share the same system settings for appearances (colors, window borders, gtk theme, icons, etc.) and in gnome, as far as i know to this point, you cant change the wallpaper for each one (major flaw in my opinion as you've been able to do this in kde for a while now)...

apps cant be moved across from one to the other (wich i consider a good thing, no more WoW trying to be 3200x1200 resolution) and since both desktops are on the same system, trying to open multiple instances of certain apps that dont like that, of course wont work... also, setting up compiz to work EFFECTIVELY on both seperate x screens has proven to be quite annoying and impossible for me, your experience may vary.

overall, if you have your dual monitor set up behaving as desired i wouldnt mess with this alternative option... but if it sounds like something you need, go for it :P

---

### Post by Zorael on 2008-04-26
> **Nythain said:**
> aye, seperate-x-screens are pretty much two different desktops... this works a little odd, since they will both share the same system settings for appearances (colors, window borders, gtk theme, icons, etc.) and in gnome, as far as i know to this point, you cant change the wallpaper for each one (major flaw in my opinion as you've been able to do this in kde for a while now)...
I believe you can have two different themes in KDE. The whole desktop configuration seems different, even the panel menu is set to defaults when starting it for the first time.

*jab* :D

---

### Post by nidelius on 2009-03-25
You can have different Gnome setup in Ubuntu 8.10 at least, if you have any questions about this I am running dual X-screens and can explain if you need help or wonder something.
I've put up dual X-screens and running compiz on both of them with a great setup (in my opinion)

---

### Post by FHavlak on 2010-06-01
I have a question.

Is it possible to send a window from one screen to another.

I do a fair amount of work in matlab and I'd like to have my editor in one screen and my terminal in the other.

I know I can't easily move from one screen to another, but the editor is a separate window, so I was thinking it might be possible

Alternately, I could edit my m-files with a different program.

Just exploring my options.

---

### Post by Wardje on 2010-06-01
> **FHavlak said:**
> I have a question.

Is it possible to send a window from one screen to another.

I do a fair amount of work in matlab and I'd like to have my editor in one screen and my terminal in the other.

I know I can't easily move from one screen to another, but the editor is a separate window, so I was thinking it might be possible

Alternately, I could edit my m-files with a different program.

Just exploring my options.

If you use TwinView, you can simply drag windows between them. It's nothing more than an extended desktop then (see it as if you bought a bigger screen). Is there a particular reason you want to use two seperate X screens?

---

### Post by FHavlak on 2010-06-01
> **Wardje said:**
> If you use TwinView, you can simply drag windows between them. It's nothing more than an extended desktop then (see it as if you bought a bigger screen). Is there a particular reason you want to use two seperate X screens?

The screens are different sizes and resolutions.  I like each screen having menus / taskbars and I like each screen having it's own four desktops.

Basically I like everything about separate x screen except that I can't have windows from the same program on both screens.

---

### Post by pieman711 on 2010-09-30
I've got separate x screens working very nicely on my ubuntu 10.04 set up. It was very simple to do. No playing around with any configs or compiling from source. I don't think I even opened the terminal! 
I can have different compiz settings for each screen but I can't work out how do have different themes or screensavers. Is this even possible in Gnome? I saw above that it is in KDE...
The best advantage I can see to having separate x screens over dual view (twin view) is that running games ect in full screen doesn't affect what is going on on the other side.

---

