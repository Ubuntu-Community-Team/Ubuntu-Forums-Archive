---
title: "Why does kxmame 2.0beta force an uninstall of xmame-x?"
date: 2007-02-16
forum: General Help
---

### Post by meldroc on 2007-02-16
I just noticed a new version of kxmame, 2.0 beta, in edgy-backports.

The problem is that when I try to upgrade to it, it forces an uninstall of xmame-x, which is highly annoying.  My impression was that kxmame was designed to be used either with the SDL or X11 versions of xmame.

How do I make these two packages coexist like God intended?

---

### Post by r3dux on 2007-02-18
Hi there,

I had the same problem and fixed it by reverting back to the older version of kxmame. Here's how I did it:

- Fire up synaptic from K | System | Synaptec Package Manager (entering your root pass as you go)
- In synaptic, click the search button on the menu bar and type "kxmame" then click the little windows [search] button
- Right click on kxmame and select "mark for installation" click okay to the warning of the conflict about xmame-x
- From the synaptic menu click Package | Force Version
- Select the 1.90-0ubuntu1 version then click [OK]
- Click the big search button on the main menu again and search for xmame, then right click on it and select "Unmark"
- Click [Apply] on the main menu

Ta-da! The older (and working!) version of kxmame should be installed, which you can point at xmame without being forced to use the legacy SDL version.

Be aware that next time you use adept or such, it will try to update your kxmame version to the newer broken one again, so just keep an eye on it and don't let it b0rk ya mame sessions!

Hope this helps.

Kind regards,
r3dux

---

### Post by megamaced on 2007-04-26
I would also like to know this, because xmame-sdl doesn't work half as well as xmame-x

---

### Post by meldroc on 2007-05-16
Still no new news on this issue.  I did file a bug report on this, so hopefully the maintainer will see that a problem exists.  If all else fails, I may end up fetching the source and fixing the dependencies myself...

---

### Post by i23098 on 2007-08-22
I've got the same problem. :( 
Can someone solve this for good? It should be fairly simple change the dependencies of the package...

---

