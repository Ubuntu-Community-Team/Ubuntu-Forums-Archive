---
title: "[SOLVED] Sorry i'm a linux noob how do i do this?"
date: 2007-11-19
forum: General Help
---

### Post by Deo Favente on 2007-11-19
I know my title sux but how do i make a folder alread in existance: "/home/johndoe/abc/def/" pop up, with the same exact contents all the time, pop up in the my computer thing labeled as "xyz" and i can type in "xyz:/ in anything and it will point to "/home/johndoe/abc/def/"?

---

### Post by SgtDude on 2007-11-19
I'm not sure exactly what you're trying to do.  What is the "my computer thing" you're referring to, and do you want to move a folder there, or just have a shortcut to your folder there?

---

### Post by Deo Favente on 2007-11-20
I'm referring to computer:///, and i just want some sort of shortcut, so that in any folder or program you could type it in the front and it would point to the folder. In windows you could map a network drive to a local folder, that's exactly what i want.

---

### Post by Mithrilhall on 2007-11-20
I'm not sure what you're using (Ubuntu, Kubuntu, etc.).

Open a console and browse to the location you want the 'shortcut' to be.

Then issue something like so:

```

ln -s /this/is/the/path/to/the/file/or/folder nameofshortcut

```

---

### Post by Deo Favente on 2007-11-20
Oh ok i see thanks. This works just as good. Now i can type /JavaRoot/ to get to all my 326 java classes. Thank you.

---

