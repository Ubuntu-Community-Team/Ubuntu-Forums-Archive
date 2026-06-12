---
title: "Raleigh Theme has no scrollbar in Terminal"
date: 2017-06-08
forum: General Help
---

### Post by Ralph L on 2017-06-08
I would like to use the Raleigh theme, because it has the stepper arrows.  I used it in xubuntu 16.04 and it worked fine.  However, in xubuntu 17.04, it does not put a scrollbar on Terminal.  Thus whenever I have a long output in Terminal, I can't scroll up using the scrollbar.  The problem may be that both the scrollbar and the background are the same color, and thus the scrollbar doesn't show.  I selected Raleigh in "Appearance".  It doesn't matter what Style I select in Windows Manager; I can see no scrollbar on Terminal. If anybody knows of changes I can make to Raleigh to correct this problem I would appreciate it.  I just noticed that firefox has the same problem with Raleigh.  However, all other apps seem ok.

I also tried installing the Clearlooks Phenix theme.  This worked fine except that, for main panel pull down menus and for Thunar pull down menus, there is too little contrast on highlighted item to read them.  So fixing this would be another alternative, if somebody knows how.

---

### Post by vasa1 on 2017-06-08
What about the default Greybird theme? Have you tried that?

In my opinion, Raleigh is a vestigial theme. At least in 16.04, there's just a gtkrc file, nothing more. Compare that with other actively developed themes.

---

### Post by Ralph L on 2017-06-08
vasa1:  Thanks for the response.  Yes, I have tried Greybird.  It doesn't support stepper arrows on scrollbar.  Only High Contrast and Raleigh support them, and I really want stepper arrows. In the past I have used Rayleigh, because of the stepper arrow support, but now that Rayleigh doesn't work right on some apps, I am stuck with High Contrast, or load some other theme from the web, and take my chances.  In the way past I have used Clearlooks Phenix.  The out of the box version of Clearlooks Phenix has a problem with lack of contrast on the pull down menus (particularly in Thunar).  This makes it almost impossible to read the highlighted (the one you want to read) item in the menu.  However, I have found that by manipulating Theme Configuration I have been able to somewhat fix this problem and get a reasonably usable theme.  So for now, unless someone can tell me how to fix Raleigh, I am going to go with my fixed Clearlooks Phenix.  
By the way Theme Configuration (in my usage) is really screwed up, and never does the same thing twice.  I fiddled with it for over an hour, trying all settings in all different orders, until I finally go something like I wanted.  I am surprised that nobody else is complaining about it.

---

### Post by vasa1 on 2017-06-10
> **Ralph L said:**
> vasa1:  Thanks for the response.  Yes, I have tried Greybird.  It doesn't support stepper arrows on scrollbar.  Only High Contrast and Raleigh support them, and I really want stepper arrows. In the past I have used Rayleigh, because of the stepper arrow support, ...
Have you tried Ambiance which is Ubuntu's default gtk theme?
To install Ambiance, you need to install the *light-themes* package from the standard repos (at least in 16.04).

Then, 
assuming you're using the default Xubuntu xfce4-terminal which may still be a gtk2 app, 
and
assuming that Ambiances still has the same gtk2 code as the 16.04 version has,
look at [https://ubuntuforums.org/showthread.php?t=2345941](https://ubuntuforums.org/showthread.php?t=2345941) and you'll need to modify only the gtkrc file as described there.

---

