---
title: "Loss &quot;Install and Remove Software&quot; under Applications menu"
date: 2007-02-03
forum: General Help
---

### Post by chinese_ys on 2007-02-03
Somebody helps me, I just find that the "Add/Remove Program" under Applications menu disappeared, I do not know why. 

I want to get it back, but how and which package do I need to install?

thanks!

---

### Post by Rhubarb on 2007-02-03
You don't need to install any packages to get it back.

Right-click on Applications --> Edit Menus
At the bottom of the right hand pane you'll see a checkbox beside "Add/Remove...", put a tick in the checkbox, then press the close button.

The Add/Remove Programs menu entry should now be back in your Applications Menu.
Hope this helps :)

---

### Post by chinese_ys on 2007-02-03
> **Rhubarb said:**
> You don't need to install any packages to get it back.

Right-click on Applications --> Edit Menus
At the bottom of the right hand pane you'll see a checkbox beside "Add/Remove...", put a tick in the checkbox, then press the close button.

The Add/Remove Programs menu entry should now be back in your Applications Menu.
Hope this helps :)

Thanks man!

i have already tried menu layout, but there is no option for "Add/Remove software". what is wrong?

---

### Post by chinese_ys on 2007-02-03
upupup

---

### Post by meng on 2007-02-03
Well since you ask (and are rather impatient!) I could say are you sure you're looking in the correct place on the menu editor? It's the right panel with the checkboxes.

---

### Post by chinese_ys on 2007-02-03
Problem has solved. I uninstall the firefox, but the "gnome-app-install" is also removed with firefox. So I can not see "Add/Remove ..." in applications and menu layout. 

I am also confused about why the firefox has the dependency with gnome-app-install?

---

### Post by chinese_ys on 2007-02-03
> **meng said:**
> Well since you ask (and are rather impatient!) I could say are you sure you're looking in the correct place on the menu editor? It's the right panel with the checkboxes.
May be I did not write clearly, I have checked my menu layout before I posted. May be this is you called about impatient?

thanks for replying!

---

### Post by Rhubarb on 2007-02-03
Firefox has many many dependencies, and as such should not be uninstalled by a beginner.
IMO you should just delete the Firefox icon if you don't want to see it.

Anyway, to get gnome-app-install back, just type this into the Terminal:
```
sudo apt-get install gnome-app-install
```

Hopefully the Add/Remove... is back up and working for you then :)

---

### Post by meng on 2007-02-03
> **chinese_ys said:**
> May be I did not write clearly, I have checked my menu layout before I posted. May be this is you called about impatient? thanks for replying!
I know you checked, I read your post, I just suggested you look again. You seemed desperate for some sort of response, and although my response didn't end up being the right answer, I responded anyway, just in case you had overlooked something obvious. It's very common to overlook something obvious, and it happens all the time. I'm very pleased you sorted out the problem on your own.

---

### Post by xhabitat4humanityx on 2007-02-03
I also had the problem of losing Add/Remove from the Applications menu. I had also removed my firefox. Will never do that again!

Have been using Ubuntu 6.06 LTS for about 2 months now. I love it! I am going to sell my Windows XP on Ebay. 

Thanks to all the folks who help newbies like me!

---

