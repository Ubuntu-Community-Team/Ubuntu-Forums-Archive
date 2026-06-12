---
title: "Problems with compiz"
date: 2006-09-26
forum: General Help
---

### Post by Esmo2000 on 2006-09-26
After I installed compiz movies run ridiculously slow, particularly when I expand the window.  The larger it is the slower it is.  Likewise, very basic simple OpenGL apps have tremendous trouble when i expand the window.  When i don't run compiz they are both fine.

My graphics card is new (nvidia) and i have the appropriate drivers.

Suggestions anyone?
J

---

### Post by catanzag on 2006-09-26
What I can suggest is if you followed some compiz installation guidelines as, for instance, in [http://ubuntuguide.org](http://ubuntuguide.org) . There is a troubleshooting on slow down moving window
```
If moving windows slows down the system, run gconf-editor from the terminal. 
Find apps/compiz/general/screen0/options. Disable detect_refresh_rate and set refresh rate to 60.
```

regards

---

### Post by Esmo2000 on 2006-09-26
Hey, thanks for your response.

The guide didn't have any information on my problem and setting the refresh rate didn't help either.  Any other ideas?

Thanks,
J

---

### Post by catanzag on 2006-09-27
> **Esmo2000 said:**
> ...Any other ideas?...

Unfortunately not (for now); my last suggestion is that you could check other wikis help in

[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=compiz&titlesearch=Titoli](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=compiz&titlesearch=Titoli)
[https://help.ubuntu.com/community?action=fullsearch&context=180&value=compiz&titlesearch=Titoli](https://help.ubuntu.com/community?action=fullsearch&context=180&value=compiz&titlesearch=Titoli)

and in

[http://wiki.beryl-project.org/index.php/Ubuntu](http://wiki.beryl-project.org/index.php/Ubuntu)

regards

---

### Post by arsenic23 on 2006-09-27
Just out of curiousity, exactly what model Nvidia card do you have ?

---

