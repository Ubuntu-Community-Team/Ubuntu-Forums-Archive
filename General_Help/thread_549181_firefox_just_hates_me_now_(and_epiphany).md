---
title: "firefox just hates me now (and epiphany)"
date: 2007-09-12
forum: General Help
---

### Post by TheRingmaster on 2007-09-12
last night i was wanting to preview a certain song with the rapsody plugin that they provide you and it turned out that it didn't work with the current version so i quickly removed it. Then firefox starts crashing on me. No matter what the website. Google.com <CRASH> regnumonline.com.ar <CRASH> You get my point. I tried opening up via a terminal and when it crashed it outputted "bus error (core dumped). Does anyone have an idea what deal is with this. I also installed epipany (to be like my back up,) but it crashes in the same manner too. 


Thank god for opera. My only saving grace in this weird situation.

thanks,

The Ringmaster

---

### Post by nikhilk on 2007-09-12
Have you installed the firefox .deb or directly copied it from mozilla website? What happens if you start firefox in safe mode?

---

### Post by raijinsetsu on 2007-09-12
trying running "sudo aptitude reinstall mozilla-firefox". Most likely, when you uninstalled your plugin, it left enough behind for firefox to think it's a full plugin. So, when it tries to access the plugin, it crashes.
You could also try cleaning out your firefox plugins directory. It's somewhere in your home directory, I forget where.

---

### Post by TheRingmaster on 2007-09-12
> **nikhilk said:**
> Have you installed the firefox .deb or directly copied it from mozilla website? What happens if you start firefox in safe mode?

actually this is just the firefox that came with ubuntu. In safe mode, <CRASH> "bus error (core dumped).

---

### Post by TheRingmaster on 2007-09-12
> **raijinsetsu said:**
> trying running "sudo aptitude reinstall mozilla-firefox". Most likely, when you uninstalled your plugin, it left enough behind for firefox to think it's a full plugin. So, when it tries to access the plugin, it crashes.
You could also try cleaning out your firefox plugins directory. It's somewhere in your home directory, I forget where.


i tried the reinstalling thing, and still no luck. 

Where might this plugin folder be located. ~/.mozilla?

---

### Post by Maestro23 on 2007-09-12
> **TheRingmaster said:**
> i tried the reinstalling thing, and still no luck. 

Where might this plugin folder be located. ~/.mozilla?

In terminal:

> cd ~/.mozilla


---

### Post by nikhilk on 2007-09-12
> **TheRingmaster said:**
> Where might this plugin folder be located. ~/.mozilla?
That is correct.

---

### Post by TheRingmaster on 2007-09-12
is there anything in particular i should be looking for?

---

