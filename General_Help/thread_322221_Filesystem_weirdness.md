---
title: "Filesystem weirdness"
date: 2006-12-20
forum: General Help
---

### Post by tigerpants on 2006-12-20
I've just this minute booted into ubuntu and there seems to be some filesystem weirdness going on in nautilus. When I click on filesystem in the left hand pane, instead of accessing the root partition with the etc, usr, bin folders etc, as normal, all I get are home and media. 

I can access a root folder in the location bar by typing it in, but when I move up through the folders to I get back to / folder, it still shows just home and media. Am I missing something obvious? I don't understand because it was fine yesterday when I logged off.

Any help appreciated.

---

### Post by chrisccoulson on 2006-12-20
You need to check View -> Show Hidden Files. This should reveal everything else on your filesystem. You should also see a .hidden file, containing a list of hidden files and folders (/bin, /boot ...), which is what is telling Nautilus to hide everythng except /home and /media

---

