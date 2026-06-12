---
title: "How to change the icon of AWN dock  permanently?"
date: 2008-02-07
forum: General Help
---

### Post by chunchengch on 2008-02-07
I change the icon of AWN dock, such as OpenOffice, Thunderbird and Firefox, but when I re-lunch the application, the icon changes back to the original one, how can I change it permanently?

I asked the similar question in AWN forum, but no useful answer, I hope I can get it here, thanks a lot!

---

### Post by aashay on 2008-02-07
I use custom icons and have never encountered such a problem. Which version are you referring to?

---

### Post by mozetti on 2008-02-07
Are you closing AWN after you change the icon, or does it crash? If it crashes, then most likely any changes won't be saved. If this is the case, then change the icon, then close AWN, and then re-open it. Hopefully this fixes it, because I don't know enough to to offer another suggestion. 

The only other thing that comes to mind is maybe there's a config file somewhere (maybe /home/<user>/.awn/) that contains a path the icon, and you could make the change there.  Good luck!

---

### Post by chunchengch on 2008-02-07
just move icon to /usr/share/pixmaps and then change the dock icon, this solves the problem.

---

### Post by itsjustarumour on 2008-02-13
The custom AWN icons are stored in

/home/(user)/.config/awn/custom-icons

Delete anything in there that looks like it shouldn't be there, and AWN SHOULD then use the correct icons. Obviously, replace (user) with your own username.  I'm still having some trouble with OpenOffice and Synaptic icons diplaying correctly though...

---

### Post by Nakoma on 2008-05-16
I haven't seen a good solution (besides a patch?) for this OO icon problem. So here's what I did. 

In the ~/.config/awn/custom-icons/ folder I added an icon for OpenOffice 2.3 manually by copying one of the OpenOffice icons already in the directory and renaming it "OpenOffice.org-2.3" (this is the name OpenOffice first displays when it opens on AWN before changing it's icon). 

Here's a screenshot of my own directory (above). For some reason when OO opens from both the AWN bar and individual files my custom icons are loaded. Go figure... 

Screen:
[http://www.css.taylor.edu/~screasey/awn/Screenshot-custom-icons%20-%20File%20Browser.png](http://www.css.taylor.edu/~screasey/awn/Screenshot-custom-icons%20-%20File%20Browser.png)

Icons (I'm using):
[http://www.css.taylor.edu/~screasey/awn/custom-icons.tar](http://www.css.taylor.edu/~screasey/awn/custom-icons.tar)

Oh, and of course, I'm on trunk.

---

