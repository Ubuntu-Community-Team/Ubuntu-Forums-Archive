---
title: "Changing the monitor settings for the login screen or globally."
date: 2013-07-10
forum: General Help
---

### Post by ferulebezel on 2013-07-10
I have a rotated monitor.  It sucks that every user has to change their individual settings but that can be dealt with.  What really sucks is that I can't figure out how to change the login screen.

How do I do it?

---

### Post by Cavsfan on 2013-07-11
> **ferulebezel said:**
> I have a rotated monitor.  It sucks that every user has to change their individual settings but that can be dealt with.  What really sucks is that I can't figure out how to change the login screen.

How do I do it?

What version of Ubuntu do you have installed? Are you talking about changing the bootup screen (Grub2) or just the login screen?

---

### Post by ferulebezel on 2013-07-11
> **Cavsfan said:**
> What version of Ubuntu do you have installed? Are you talking about changing the bootup screen (Grub2) or just the login screen?

The login screen, although the grub screen would be nice.  I'm using 12.10

---

### Post by Cavsfan on 2013-07-12
> **ferulebezel said:**
> The login screen, although the grub screen would be nice.  I'm using 12.10

Try this:

[ATTACH=CONFIG]244643[/ATTACH] 

That should set the login screen to whatever background you are using. My login has always worked that way - the same picture as my background.

As far as the Grub 2 bootup screen. If you just want a background picture you could just make sure there is no picture in **/boot/grub/** and then move one that is the same size as your desktop resolution into that filder.
**sudo cp *picture-file* /boot/grub/** That should make a picture of your choosing display although not all pictures work. You can only have one piture in that folder as it looks for the first one it finds.
It looks for any kind of picture as the code looks like this

```
	case "${1}" in
		*.jpg|*.JPG|*.jpeg|*.JPEG) reader="jpeg";;
		*.png|*.PNG) reader="png";;
		*.tga|*.TGA) reader="tga";;
		*) return 3;; # Unknown image type.
	esac
```

If it finds a picture in **/boot/grub/** you can setup custom font colors. But, the font colors displaying are based on a single picture existing in **/boot/grub/**.

If you want to change the font colors and customize what displays at bootup you could look at the green link in my signature. There are several examples and there is a link in the bottom to report any questions or problems.

---

### Post by ferulebezel on 2013-07-14
That has nothing to do with the **rotation**.

---

### Post by Cavsfan on 2013-07-15
> **ferulebezel said:**
> That has nothing to do with the **rotation**.

Guess I can't help then as I have no idea how to deal with **rotation**.

---

### Post by ferulebezel on 2013-08-14
Perhaps I should have made it more clear.  My **monitor** is **physically** rotated.  Everything is sideways unless the settings are changed.  This has nothing to do with background pictures.

For some reason this can only be and has to be accommodated in each user account.  It makes no sense that monitor rotation isn't a global setting, yet it isn't.

It can be done at each users level.  How do I do it for the rest of the system?

---

