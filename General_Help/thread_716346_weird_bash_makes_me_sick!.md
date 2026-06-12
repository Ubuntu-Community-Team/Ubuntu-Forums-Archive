---
title: "weird bash makes me sick!"
date: 2008-03-05
forum: General Help
---

### Post by pavallokazzo on 2008-03-05
that's probably something that must be actived somewhere but I think that ubuntu mainteners should implement it as a default...
in gentoo, I can work in the bash history by typing 3-4 characters of the last command I gived and I want to call and by pressing the pgup key...
i.e.
history:
1 mplayer blu.avi
2 ls
3 mplayer red.avi
4 vlc blu.avi

typing "mpl" at bash shell gives me the whole last command called starting with "mpl"...
#mpl  /pressing pgup will give me...
#mplayer red.avi
again with the same key I can navigate through the history
#mpl  /pressing pgup will give me
#mplayer red.avi /pressing again pgup will give me
#mplayer blu.avi

any help on how to do that???

THANKS!!

---

### Post by kaens on 2008-03-06
If you type Ctrl-r it will search recursively through your command history as you type.

---

### Post by soldats on 2008-03-06
actually there is a way. i believe the file is located in /etc as inputrc. 
```
sudo nano /etc/inputrc
```
i think its on the line that says map pgup pgdwnto search history. i used to have this working and i "believe" you need to uncomment it and add a \e to the beggining. dont quote me. ive also seen people who have just uncommented it and have it working.

---

### Post by pavallokazzo on 2008-03-07
thank you both!

---

### Post by pavallokazzo on 2008-03-07
why isn't that as a default option?
it's so cool...
how to propose that upstream?

---

