---
title: "Generate txt file with list of all files (mp3z) in a specific folder"
date: 2007-07-11
forum: General Help
---

### Post by Digitallysick on 2007-07-11
I want to export a list of all my mp3z out of 1 folder into a text file, listed a to z, whats the easiest way to do this

---

### Post by arsenic23 on 2007-07-11
```

[COLOR="White"](find *.mp3 -type f) > ~/Desktop/mp3.log[/COLOR]

```

Will put a list of all files within the folder you run it out of that end in .mp3 onto your desktop.

------ edit -------

Wait, I'm asuming you have all your files in one folder like I do....  ignore me.

---

### Post by arsenic23 on 2007-07-11
Ok, sorry for being dumb.  Running the following from the terminal in the root directory of your music should work no matter how you have your files layed out.  The only thing I'm assuming is that all your files have lowercase extensions.

```

(find -printf '%f \n' | grep .mp3 | sort) > ~/Desktop/mp3.log

```

You can change the filepath at the end to whatever you'd like.

---

