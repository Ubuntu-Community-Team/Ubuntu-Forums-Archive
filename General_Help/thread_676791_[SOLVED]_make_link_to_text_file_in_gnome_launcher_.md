---
title: "[SOLVED] make link to text file in gnome launcher panel"
date: 2008-01-24
forum: General Help
---

### Post by startling on 2008-01-24
I was fed up with not having bookmarks in the Gnome Terminal (like the KDE terminal has) so I tried a workaround. I created a text file containing the terminal commands I use most frequently. (Why aren't there bookmarks in the Gnome Terminal, by the way? Surely not all Ubuntu users are lightning fast typists with flawless memories... ) 

I then tried to create a shortcut to this file in the launcher panel at the top of the screen, by dragging the file from Nautilus onto the panel (similar to the way I used to create shortcuts on the Windows quick launch bar). Instead of the file icon, a big red X appeared, and when I clicked it an error message appeared that states: "Could not launch application - Not a launchable item".

Is there a better solution to the problem of Terminal Bookmarks? Or can anyone tell me how to create a link to a text file in the launcher? Thanks.

---

### Post by p_quarles on 2008-01-24
Like so: Edit the launcher, and place "gedit" before the text file name.

---

### Post by startling on 2008-01-24
Wow! Thanks for the fast reply, p_quarles

I cannot edit the launcher. When I click on Launcher Properties it shows up as Type: Application and all the other boxes are completely blank. Sorry, but I'm still a noob.

---

### Post by p_quarles on 2008-01-24
Hmm. Then I guess just delete it, and create a new one with the proper syntax:
```
gedit filename
```
Also, just so you know, Konsole works just fine in Gnome, so if you prefer that one, it's only a trip to the package manager away.

---

### Post by startling on 2008-01-24
Thanks to p_quarles' reply I found out how to do this: 

Right-click on the panel and choose "+  Add to panel... "
Click on "Custom Application Launcher"
in the command box, type: 
  gedit "/home/username/terminal bookmarks"  (using quotes because the filename has a space in it)

And it works!

Thanks again p_quarles

---

### Post by startling on 2008-01-24
> **p_quarles said:**
> Hmm. Then I guess just delete it, and create a new one with the proper syntax:
```
gedit filename
```

Thanks. I just posted a reply that crossed with yours regarding this.

> **p_quarles said:**
> 
Also, just so you know, Konsole works just fine in Gnome, so if you prefer that one, it's only a trip to the package manager away.

Aha! Thanks for that suggestion, and your prompt help with this issue. Ubuntu has the best support of any OS!

---

### Post by SanskritFritz on 2008-01-24
You may also wish to consider using aliases (see your .bashrc file), and using the history (press up in the terminal). Also if you press Ctrl-R and type a part of a previously entered command, it finds it. Repeated Ctrl-R finds some more.
And then there is **[Hotwire]("http://www.getdeb.net/app/Hotwire")**!

---

### Post by startling on 2008-01-24
> **SanskritFritz said:**
> You may also wish to consider using aliases (see your .bashrc file), 

Thanks - I'll look into that.

> **SanskritFritz said:**
> and using the history (press up in the terminal) 

It was after a marathon session of pressing the up arrow about a couple of hundred times and **still** not finding the command I'd forgotten that I thought, 'Bah, this is silly - there has to be a better way' and hence this thread.

---

### Post by SanskritFritz on 2008-01-24
> **startling said:**
> It was after a marathon session of pressing the up arrow about a couple of hundred times and **still** not finding the command I'd forgotten that I thought, 'Bah, this is silly - there has to be a better way' and hence this thread.I know that, that is why I wrote about the Ctrl-R trick. ;-)

---

