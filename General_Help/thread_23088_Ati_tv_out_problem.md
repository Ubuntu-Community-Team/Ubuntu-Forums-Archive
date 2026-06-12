---
title: "Ati tv out problem"
date: 2005-03-31
forum: General Help
---

### Post by tmowerman on 2005-03-31
Hi

I have an Hp omnibook xe4500 laptop, with an Ati Mobility M6 graphics card.  Under warty, i used the program atitvout to enable tv out.  In hoary, i think because of xorg, this only works in the console.  

I have tried getting the ati fglrx drivers, but they don't support my card.  

When i switch back to x from the console, I am getting flickering on my tv, so I have tried changing refresh rates in xorg.conf. Nothing.

As I only watch videos, i have tried xinefb, but i get the error 

video port failed.

If anyone has any more ideas, i would appreciate it, as i think my only other option is to install gatos from cvs, which scares me.  Or wait until the xorg people add the gatos code, which i have heard rumours will happen.

Thank you

Tim

---

### Post by tmowerman on 2005-04-05
I have found out some more stuff.  fbxine and the mplayer fb driver work fine, but are very slow.  The refresh rate is also wrong when tv out is enabled.  

Im sure there must be some options in xorg.conf to get the tv out working, but i cant find them.  The vesa driver lets tv out work, but video play back is too slow to be watchable.  

If anyone has any ideas on speeding up the vesa video playback, or getting the tv out working with the radeon driver, it would be much appreciated.  

Thank you very much

Tim

---

### Post by krusbjorn on 2005-04-06
try [this thread](http://www.ubuntuforums.org/showthread.php?t=19168) .

---

