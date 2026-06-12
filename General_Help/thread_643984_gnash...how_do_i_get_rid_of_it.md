---
title: "gnash...how do i get rid of it?"
date: 2007-12-18
forum: General Help
---

### Post by Kal-El in SLO on 2007-12-18
Hi, I'm an ultra-noob to ubuntu and linux. I installed Gutsy and it's running great. Firefox also runs great, but gnash does not.

how do i uninstall the gnash flash plugin? 

one more thing. When firefox starts up, everything is sooo small. not so small that i can't read it, but it's small enough to be annoying. i tried to change the minimum text size, but that only changes certain parts of the page. going to view/text size/increase only changes the size temporarily. a good example of a page that bothers me is yahoo's home page. does anyone know how i can change the default settings for firefox?

thanks.

---

### Post by Geekys on 2007-12-18
> If you built Gnash from source, go to your build directory and type 'make uninstall'. If you installed it as a package, remove it using your package manager.

Source: [http://www.gnashdev.org/?q=node/25#uninstall](http://www.gnashdev.org/?q=node/25#uninstall)

Hope that helped :)

---

### Post by aysiu on 2007-12-18
> **Kal-El in SLO said:**
> Hi, I'm an ultra-noob to ubuntu and linux. I installed Gutsy and it's running great. Firefox also runs great, but gnash does not.

how do i uninstall the gnash flash plugin? Paste this command into [the terminal](http://www.psychocats.net/ubuntu/terminal): ```
sudo apt-get remove mozilla-plugin-gnash gnash
``` > one more thing. When firefox starts up, everything is sooo small. not so small that i can't read it, but it's small enough to be annoying. i tried to change the minimum text size, but that only changes certain parts of the page. going to view/text size/increase only changes the size temporarily. a good example of a page that bothers me is yahoo's home page. does anyone know how i can change the default settings for firefox? It's entirely possible the page was coded to fix the size of the font or the font is displayed as an image or Flash file, in which case you can't adjust the font size. The other possibility would be that you've somehow managed to change ownership of your Firefox settings directory so that it is owned by root, and you can't modify your own settings permanently, in which case, this command would help: ```
sudo chown -R kalel:kalel /home/kalel/.mozilla
```

---

### Post by Kal-El in SLO on 2007-12-18
> **aysiu said:**
> It's entirely possible the page was coded to fix the size of the font or the font is displayed as an image or Flash file, in which case you can't adjust the font size. The other possibility would be that you've somehow managed to change ownership of your Firefox settings directory so that it is owned by root, and you can't modify your own settings permanently, in which case, this command would help: ```
sudo chown -R kalel:kalel /home/kalel/.mozilla
```

Thanks for the info!

I dont think that the text is being displayed as an image or flash file because when i go to view/text size/increase, all the text increases in size...and firefox looks exactly how i want it. I just don't know how to keep it that way.

When I run firefox from XP with the same monitor, it looks normal. 

Is there a way that I can check to see if i accidentally changed ownership of my firefox settings directory to be owned by root? I was thinking that I might as well check before running that command that you just gave me.

---

