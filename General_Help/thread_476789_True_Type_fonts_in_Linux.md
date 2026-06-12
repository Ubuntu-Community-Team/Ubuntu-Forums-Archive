---
title: "True Type fonts in Linux"
date: 2007-06-17
forum: General Help
---

### Post by guitodd on 2007-06-17
Is there a utility to bring true type fonts into linux.. Or an easy way to do it?  I have one font that I need from a win machine to complete a project.  I can't figure out where fonts are kept...

a bit of a newbie here.

Thanks,

---

### Post by s.deleeuw on 2007-06-17
Create a directory '/home/<username>/.fonts' and copy your TTF-files to that directory.
You might to logout and login again for things to work.

The dot in '.fonts' makes this directory hidden. If you want to see hidden files/directories you will have to configure this in Nautilus > Edit > Preferences.

---

### Post by steveneddy on 2007-06-17
They are in the repositories.

Do this is terminal:

```
sudo apt-get install msttcorefonts
```

That will get the basic ones there. 

Good Luck

---

### Post by guitodd on 2007-06-17
You guys saved my butt!  Again! 

Thanks,
Todd

---

### Post by steveneddy on 2007-06-17
You are welcome

---

### Post by DeeWox on 2007-06-18
Don't you have to activate them or something? Or do they automatically install and beeing activated?

---

### Post by shirilover on 2007-06-18
try the following
```

fc-cache -f -v ~/.fonts

```

---

### Post by guitodd on 2007-06-18
> **DeeWox said:**
> Don't you have to activate them or something? Or do they automatically install and beeing activated?

That's what I thought was wierd.. They just showed up in Open Office.  All I did was what the first two posters recommended.  I was able to just drop my font in that folder I created and it was there.

A lot easier than I though!

---

