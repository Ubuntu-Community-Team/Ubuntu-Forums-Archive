---
title: "Zune &amp; msxml6.0 dll  &lt;--- Help with wine...."
date: 2006-12-25
forum: General Help
---

### Post by Get_Ya_Wicked_On on 2006-12-25
Well my sister was given a Zune (the wireless, media-player by Microsoft) and wanted me to install  the software in Ubuntu, since our Windows is rarely used and would also prove inconvenient if the software were to be installed on its partition. So I attempted to run the setup from a terminal using the wine command as I would any other setup. It all was going along fine until I chose its installation directory (well, left the default) and hit "install". It could not continue because the system lacked MSXML 6.0 Well, at first I tried copying my 6.0 dll's from my *real* Sys32 folder in Windows and pasting them to my *fake* Sys32 folder in /.wine The same error message. 

Now I've come to understand that I need to download 'libxml-dev' and compile it with wine, producing a fresh installation. If this is the case, I would appreciate any useful links or quick tutorials on the matter while I'll search as well. It would be nice however to adapt a "quick-fix" of sorts and be on with it. Thank you in advance for your interest and [hopeful] help.

---

### Post by Get_Ya_Wicked_On on 2006-12-26
; )

---

### Post by fragos on 2006-12-26
Zune has a little surprise for you.  It has a new kind of DRM that's not compatible with what Microsoft has used.  I've heard that even Vista doesn't support it.

---

### Post by sandgathe on 2008-02-21
Did anyone ever figure this out? I own a Zune and I'm currently starting to learn Linux. How do I manage my Zune within Ubuntu?

---

### Post by empty pockets on 2008-06-03
yeah same here. I'd really like to be able to manage my Zune without running a virtual machine for it.

---

