---
title: "Firefox 3 beta backwards"
date: 2008-05-27
forum: General Help
---

### Post by metrorat on 2008-05-27
Hi all... I am having a wee problem with Firefox 3b5. Unlike most I actually really liked using the horizontal scroll as fwd and back in firefox 2 on my Synaptics touchpad (part of an Acer 5652WLMI btw).  On upgrading to Hardy I was disappointed that Firefox 3b5 wouldn't do it. I eventually got stuck into the about:config settings and set 

```
mousewheel.horizscroll.withnokey.action = 2
```

This got me in the right area but unfortunately the left scroll is fwd and the right scroll is back... Pointing the opposite way from the buttons on the taskbar which is very weird.

I am pretty sure that this is Firefox problem as opposed to xorg.conf/xmodmap as I used ```
xmodmap -e 'pointer = 1 2 3 4 5 7 6'
``` to switch the horizontal button mappings round and Firefox started working correctly but all other applications scrolled left for right and vice versa.

After changing this back I tried playing about with the about:config settings for mousewheel.horizscroll.withnokey.numlines/sysnumlines as I suspected these might act as modifiers for the action selected but they do nothing for this action as far as I can see.

Does anyone know how to set up application-focus specific(!) xmodmaps or better still fix Firefox so I can go back to the way things were with Firefox 2.  Please don't say Just get rid of FF3b5 and go back to 2 - I tried that and couldn't get java to work and that annoyed me more than the scrolling thing so here I am.

It ain't exactly an emergency but I'd love it if someone could help me out before I get used to them being the wrong way round....!


Cheers,

---

