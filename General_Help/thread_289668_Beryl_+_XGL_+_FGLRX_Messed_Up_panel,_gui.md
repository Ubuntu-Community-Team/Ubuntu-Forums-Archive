---
title: "Beryl + XGL + FGLRX Messed Up panel, gui"
date: 2006-10-31
forum: General Help
---

### Post by aldrlandon on 2006-10-31
So here's the deal: Basically I installed xgl, fglrx, and beryl according to the beryl wiki for ubuntu. It also has you create another session specifically for XGL and Beryl in case it has problems and you need to use metacity again. The problem, as you will be able to see from the picture, is besides the top of the windows, nothing else is skinned and looks really ugly. My question is: Is there anything I did wrong to cause them to look that way, or is there some way I could skin them to look halfway decent? Thanks for all of your help!!!

Pic: [http://i9.photobucket.com/albums/a78/aldrlandon/panelwierd.png](http://i9.photobucket.com/albums/a78/aldrlandon/panelwierd.png)

---

### Post by aldrlandon on 2006-10-31
Any Ideas?

---

### Post by marc_th on 2006-10-31
I'm very new to Linux and I'm having trouble understanding what you're looking to do.  But it sounds like you don't like the way your Desktop looks in metacity or Beryl.

To change the look in metacity you'll have to mess around with the Themes Preferences. You can access the “Theme Preferences” by selecting System &#8594; Preferences &#8594; Theme from the Ubuntu menu.

Under Beryl, you'll still have to mess around with the Theme Preferences, but you'll also have to mess around with the Emerald Theme Manager, which you can access by clicking on the red emerald on ye desktop.  You'll prolly also want to mess around with the Beryl settings.

There's TONs of articles and post on how to do these specific things.

---

### Post by aldrlandon on 2006-10-31
Basically what's happening, is the themes are fine when I run metacity, but when I run beryl, everything but the titlebar on windows isn't skinned.

---

### Post by marc_th on 2006-10-31
I could be wrong, but I think that's exactly how it's  supposed to work.  If you want to change the look of the system (other than the titlebar) use the Theme Preferences.  When I was messing around trying out Emerald Themes, I often saw suggestions on which system themes go well with it a particular Emerald theme. For example the Emerald theme called "Human" works well with the "Human" Ubuntu theme.  I hope this helps.

---

### Post by Outworlder on 2006-11-02
> **marc_th said:**
> I could be wrong, but I think that's exactly how it's  supposed to work.  If you want to change the look of the system (other than the titlebar) use the Theme Preferences.  When I was messing around trying out Emerald Themes, I often saw suggestions on which system themes go well with it a particular Emerald theme. For example the Emerald theme called "Human" works well with the "Human" Ubuntu theme.  I hope this helps.


It seems that you have completely misunderstood what the guy said. His themes are *not* working (the ones set via Theme Preferences). So it's not how it is supposed to work. Read carefully.

aldrlandon, what you have to do is to add gnome-settings-deamon in the startup programs list for your session (or run it manually after login). The correct themes should now show up.

---

### Post by marc_th on 2006-11-02
> **Outworlder said:**
> It seems that you have completely misunderstood what the guy said. His themes are *not* working (the ones set via Theme Preferences). So it's not how it is supposed to work. Read carefully.

aldrlandon, what you have to do is to add gnome-settings-deamon in the startup programs list for your session (or run it manually after login). The correct themes should now show up.

I re-read the thread very carefully and have come to the same original conclusion: the guy didn't know Beryl's theme manager had to be used in conjunction with the Ubuntu themes. Know that I've only been using Ubuntu, Linux for that matter, since Friday last; and having said this, I made the exact same mistake: after installing Beryl I was like "Why are the Emerald themes only changing the look toolbars?" A couple hours of googling later, I had figured it out. Dude, I think you've lost touch with the newbie in you; why over complicate a novice's problem. *Disclamer* I could be wrong, but if I am, he'll be back....

---

### Post by ~LoKe on 2006-11-02
I agree with Marc.  GTK themes must be used in conjunction with Emerald.

---

### Post by fancyydk on 2007-01-06
Thank you Outworlder.

I'm not sure if marc_th's interpretation of aldrlandon's problem was indeed aldrlandon's problem, but your interpretation was my problem. The themes via Theme Preferences weren't being applied and now I know I have to have gnome-settings-daemon working in order to do that. YAY!

---

