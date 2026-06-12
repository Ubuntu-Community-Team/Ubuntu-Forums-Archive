---
title: "problem w/kde-core and shared /home"
date: 2006-11-11
forum: General Help
---

### Post by m.musashi on 2006-11-11
When I installed edgy I did not removed dapper. Instead, I installed to a separate partition and pointed edgy at my /home for dapper (it was on a separate partition). The install when fine and I was happy to see that my desktop and files were all accessible. I had also installed the kubuntu-desktop package, beryl and some other themes and such. After a bit of messing around with edgy, I managed to mess up things a bit and decided to reinstall edgy. Again, I pointed it at my /home for dapper. This time, when I reinstalled kde I tried kde-core instead. That resulted in a menu bar that had only a couple icons and was even missing the K menu. So I installed the kubuntu-desktop package again hoping that would fix things. It didn't.

Thinking that some hidden theme files in /home might have been the problem, I deleted anything that seemed related to kde and did another fresh install (still pointing to the dapper /home). This time I just installed the kubuntu-desktop package but I have the same problem. I have managed to add some of the items (clock, desktop switcher, trash can) but they go where they want and I cannot move them (see screenshot).

Any ideas what is going on? Is it because I'm sharing a /home with two distinct installations of ubuntu? Is that a bad idea? It was working but now things are kind of a mess. I would like to keep just one /home if possible since it's really cool to have access to everything regardless of which version I boot.

Thanks in advance.

---

### Post by Brando569 on 2006-11-21
i think its a quirk in edgy, i have the same problem. if i do a fresh install of edgy and use my existing home directory (using the same username) everything works fine. the problem arises when i remove the kubuntu-desktop metapackage (and all of its dependencies) and install kde-core, then reboot (or restart the x server) that i have the same problem that you have. i get an error that says "KDE cannot load the KDE Panel" or something to that extent (actually i just checked yours and its a little different, i only have the icons that i placed there myself. i dont have the k menu or system tray or anything) i tried installing stuff to get it back but nothing seems to work. 

the only solution i have found is to create another user and use that account, but as im finding out now that arises other problems such as not being able to access your windows partitions :( 

im about to try a server install and hope everything goes well

---

### Post by m.musashi on 2006-11-21
I ended up just doing a clean install and setting up edgy with its own /home rather than sharing. I mounted my dapper /home so I can access the files but they are not shared. I don't have any problems now (well, actually I have problems with beryl and conky and... Edgy is a work in progress).

Good luck to you. Keep a dapper install if you can. That way you have something to fall back on if you need to.

---

### Post by Brando569 on 2006-11-23
ehh i dont like dapper, i think edgy is way better. besides i have (dare i say it) a windows xp install to fall back on :D

---

