---
title: "Login screen won't display (incompatible resolution?)"
date: 2006-10-13
forum: General Help
---

### Post by mjpatey on 2006-10-13
Hello, Group-

I've done a search on this and have followed the suggestions to no avail.

Recently, I decided to use some custom login screens from Gnome-Look, and in installing and testing them, I must have changed resolution in an odd way.

Whatever the cause, the result is that when it's time for the login screen, my screen goes black, I think because my LCD monitor can't handle whatever resolution is selected.  I know it's time to type my username and password when I hear the bongos, and then I type them in blind.  After login, once the Nautilus splash comes up, the resolution is fine and I can see again.

In System -> Preferences, I have the resolution set to 1280x1024, which is indeed what I get once I'm past the login screen.  Also, in xorg.conf, the resolutions listed only go up to 1280x1024 and no higher, so that shouldn't be affecting anything.

It seems like there's an overall resolution setting that takes control earlier, before xorg.conf's settings take over, and that's what's causing my blank screen during login.

Does anybody know how to fix this?  What I've already tried what keeps getting suggested in other posts (to limit the highest resolutions listed in xorg.conf), but the values listed in mine don't go higher than my intended resolution, so I don't think that's it.

Thanks for any help you may have!

-Mark

---

### Post by bulldog on 2006-10-13
Did you try to switch back to the previous login screen?

Maybe you have just a corrupted new login screen.

Can't imagine it's a resolution problem because your X-server seems to work well.

---

### Post by mjpatey on 2006-10-13
Well, I have it set to choose login screens randomly (I have 5)... maybe I'll just switch back to the Ubuntu default.  Though when I first loaded these new login screens, they worked just fine.  I wish I could remember what I did to break them.

I'll switch back to the default and report back.

---

### Post by SargentFuzz on 2007-03-11
I'm having the same problem, with a widescreen LCD. I'm pretty sure the resolution is right, as I did everything that everyone else did to fix it, so I am thinking that maybe it is a refresh rate problem. If anyone thinks I may be right and knows an xorg.conf fix for it, I'd be grateful.

---

### Post by LouisChappell on 2008-02-21
I'm having the same problem too. not much fun, mines a normal widescreen tv but using it as the sole monitor.

---

