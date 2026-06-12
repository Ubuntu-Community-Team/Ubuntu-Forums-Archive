---
title: "Ubuntu 16.04 (64 bit ) Desktop: Work spaces Don't work"
date: 2016-12-19
forum: General Help
---

### Post by Hakachukai on 2016-12-19
What I'm running---------------------
Ubuntu 16.04 64 bit Desktop version ( brand new install )
Gnome flashback/compiz session ( I think it's Gnome 3, but I'm not sure )
Did a Dconf setting to move the menu bar to the bottom of the screen
Did a Dconf setting to move the close, maximize and minimize buttons to the right side of the window
Changed some xinput settings to make my 2 button trackball emulate a scroll wheel [ doesn't work :-( ]

Nothing but the bare bones are installed. I need to make sure that I can get the basics working before I switch over.


The problem----------------------------------------------------
I can't get the work space switcher to do anything. When I click on it and tell it to add more work spaces it does nothing. Every time I revisit work space switcher preferences, it always forgets my previous settings and resets to the default of 1 work space.
I also have hotkeys set up for switching work spaces. They do nothing ( probably because the work spaces don't exist )

What I've tried-----------------------------------------------
So I hit the web for suggestions.
I tried going to appearance settings and enabling work spaces. It remembers my setting, but it changes nothing.
I tried using compiz manager, but I couldn't find anything that looked useful in there

What I want--------------------------------------------------
I want multiple work spaces with hotkeys. I don't want compiz animations. I don't want to waste resources on anything extra or fancy, I just want multiple workspaces.

---

### Post by Hakachukai on 2016-12-19
I was able to get this working by using a gnome flashback / metacity session

When I use the metacity session vs the compiz session it works as expected.
I did have to use some Dconf settings to set the hot keys for all 8 workspaces ( because the GUI only allowed me to set hot keys for 4 workspaces ), but it DID work in the end :-)

---

