---
title: "Desktop Effects not saved after restart!"
date: 2008-07-03
forum: General Help
---

### Post by alexmclaren on 2008-07-03
Have just waged the well travelled warpath against compiz, and seem to ahve everything organized as I would like, then I reboot, and nothing is saved??? any ideas ?

---

### Post by Vadi on 2008-07-03
Which settings aren't saved?

---

### Post by alexmclaren on 2008-07-03
most noticeably the window edge effects, the accessibility becomes 'Disabled', (i.e most things in the compiz-config console are not kept...), furhtermore, having reverted back to the no effects option, all my scrolling seems slow and fragmented ...

---

### Post by Vadi on 2008-07-03
What is your video card?

---

### Post by alexmclaren on 2008-07-03
ATI Radeon RV516 X1300

---

### Post by alexmclaren on 2008-07-04
bump?

---

### Post by Vadi on 2008-07-04
In the settings manager, go to preferences, and save everything to a profile. After a reboot, apply the profile - do the settings come back?

---

### Post by alexmclaren on 2008-07-04
hmm as soon as I saved the profile it went straight back to two dektops, chucked all the windows open in various dektops into one and removed all the edge effects (like expo, show desktop, switch etc..) will reboot now and see what happens after making a change or two to the profile

---

### Post by alexmclaren on 2008-07-04
saving it to a profile has worked thankyou! but i ahve lost lots of options in the window edge effects (switch, window picker, etc ... ? ideas) and i've lost window decorations!

Thank you for all the help!

---

### Post by Vadi on 2008-07-04
Hmm.

What are you using to start Compiz, do you know? Did you add anything special to System - Preferences - Sessions?

---

### Post by alexmclaren on 2008-07-04
not that i'm aware of, by ticking boxes in the compiz config settings manager i've been able to restore most of the options for the edges, but despite looking into the window decorations tab i'm still missing the title bar to drage a window around and the close minimize and maximize buttons ...

---

### Post by Vadi on 2008-07-04
Try doing alt+f2 and **gtk-window-decorator --replace**. Does it come back?

btw, meanwhile, if you don't know - you can move a window with alt+left click.

---

### Post by sayakb on 2008-07-04
Or press Alt+F2 and do:
```
gtk-window-decorator --replace
```

---

