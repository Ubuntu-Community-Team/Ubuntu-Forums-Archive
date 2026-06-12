---
title: "Ati 8.33.6-1 No 3d Acceleration"
date: 2007-08-19
forum: General Help
---

### Post by Raphaelo on 2007-08-19
Hello

A few minutes ago my computer gave me a notice about 8 upgrades that should be installed. One of them was an update to the fglrx videodriver. After the update my 3d accaleration was gone, fglrxinfo now gives 'mesa' instead of 'ati'.

What would be the best way to either get this driver working, or downgrade to the older one?

Raphaelo

EDIT: 3d works, but I have video problems. see my last post.

---

### Post by Raphaelo on 2007-08-19
> **Raphaelo said:**
> Hello

A few minutes ago my computer gave me a notice about 8 upgrades that should be installed. One of them was an update to the fglrx videodriver. After the update my 3d accaleration was gone, fglrxinfo now gives 'mesa' instead of 'ati'.

What would be the best way to either get this driver working, or downgrade to the older one?

Raphaelo

hehe, i managed to uninstall the faulty driver and installed the ati 8.40.4 driver, wich does seem to work for me.

srry for the perhaps unnessesary thread.

---

### Post by Raphaelo on 2007-08-19
I'm going to bump my thread once more, since i still have problems.

With the latest ati driver installed I've got 3d acceleration but now my movies look worse than before.

Before my movies weren't blocky, more 'faded' and now even subtitles look bad...:(

---

### Post by superyounan1 on 2007-08-23
when you install fglrx drivers you typically have to reinstall it with every kernel update. 

As for the video problem, what do you mean, video output looks pixelated? what player are you using? Xvideo, opengl, or X11 ouptput?

if its pixelated, it sounds like you're set to x11, in which case switch it to xvideo so the picture is filtered. avoid opengl with fglrx drivers.

in vlc, choose settings>preferences>output modules>advanced options 

then you can change it

---

