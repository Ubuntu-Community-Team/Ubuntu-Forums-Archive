---
title: "Open &quot;Run Application&quot; from the command line"
date: 2007-07-21
forum: General Help
---

### Post by figgles on 2007-07-21
Can one open the "Run Application" from the command line? Or, put another way, I'd like to invoke the "Run Application" dialog from gnome when I'm running fluxbox. Yes, there's fbrun, but I like the  listing that the "Run Application" dialog show as I type the command I wish to run.

TIA!

---

### Post by prince_niceguy on 2007-07-21
not sure what you are referring to... have you tried Alt + F2. that is run dialog for gnome as far as i recall. I am using KDE which has its run dialog with short cut of win + R

---

### Post by dagnabit dang doohickey on 2007-07-21
[gmrun]("http://www.bazon.net/mishoo/gmrun.epl") might be what you want. It's in the repos.

---

### Post by figgles on 2007-07-21
thanks -- but alt-f2 is when running under gnome -- how do I invoke it (if this is possible) under fluxbox.

TIA

---

### Post by kerry_s on 2007-07-21
look in /usr/bin for something like gnome-run or gnome-exec then try and run that from the terminal and see what it launches, i only know that "gksu" is for the run application command for running as a selected user, cause i use that in fluxbox, but i don't have no gnome.

---

### Post by dagnabit dang doohickey on 2007-07-21
Gnome doesn't have a monopoly on Alt-F2. With my Openbox setup, gmrun fits the Alt-F2 combo just fine.

---

### Post by aysiu on 2007-07-21
If you have Openbox installed but are using Fluxbox, try the command ```
gnome-panel-control --run-dialog
``` More info here: [http://icculus.org/openbox/index.php/Help:GNOME/Openbox](http://icculus.org/openbox/index.php/Help:GNOME/Openbox)

---

### Post by figgles on 2007-07-22
I like gmrun better than fbrun, but I remain curious if I can call the "Run Application" dialog in fluxbox -- thanks!

---

### Post by figgles on 2007-07-22
That's cool -- I never ran gksu without arguments -- but I prefer fbrun and gmrun to gksu (the GTK front end to su and sudo) without args -- but would prefer the "Run Application" dialog most -- thanks, though!

---

### Post by figgles on 2007-07-22
Yea, I know I can map/remap fluxbox to my hearts content -- but the million dollar question is: what is the call to "Run Application" so I can map that to alt-f2? Much Thanks

---

### Post by figgles on 2007-07-22
gnome-panel-control --run-dialog seems so close but I don't have that option on my Feisty. 

I have
gnome-panel and
gnome-control-center

neither of which accept a --run-dialog arg

that OpenBox page is a cool find, though, thanks!

---

### Post by aysiu on 2007-07-22
You need to install Openbox itself in order to use that command, for some strange reason.

---

### Post by weblordpepe on 2007-07-22
Yeah I would like to know too. actually i have an idea.

---

### Post by weblordpepe on 2007-07-22
Although we do know that its not a seperate executable. Its part of gnome-panel somehow.
When I did an xkill on the alt-f2 run dialogue, it killed gnome-panel.

---

### Post by dagnabit dang doohickey on 2007-07-23
There is another solution that doesn't require Openbox. You can find it here:

[http://darkness.codefu.org/wordpress/post/152]("http://darkness.codefu.org/wordpress/post/152")

But, this solution, as well as the Openbox one, require gnome-panel to be running since gnome-run is now integrated into gnome-panel. So, if you prefer to use a different panel (or no panel at all), then these solutions will be of no use. On the other hand, if gnome-panel is your preferred panel, then you're set.

---

### Post by weblordpepe on 2007-07-23
too hard :(

---

### Post by figgles on 2007-07-23
Yea, that is a bit more work than it would be worth for me -- and I agree with that blog, too bad it is so difficult to access that dialog. I did get gmrun out of this question, thought. I greatly appreciate everyone's help!

---

