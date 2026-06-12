---
title: "How can I use the default theme from 12.10 in 12.04?"
date: 2013-02-24
forum: General Help
---

### Post by georgelappies on 2013-02-24
I really like the changes that was made to the default theme in 12.10. However 12.10 keeps on loosing the ability to see my braodcom wifi card and I am experiencing a lot of graphical glitches as well.

12.04 is rock solid and I use this for my production work. Please tell me there is a safe and easy way to import the new theme from 12.10 into 12.04.

Thanks in advance

---

### Post by tpprynn on 2013-02-24
In the olden days, I would paste a different version of the Clearlooks metacity border into the inferior one's file, replacing the sketchy version. You could do a version of that. Or you could see if the ubuntu light-themes packages from 12.10 will install without griping about dependencies, taken from packages.ubuntu.com. For the former method I assume as you've been using Ubuntu two years longer than me that you can open the file system as route and navigate to the relevant folder.

I didn't notice a difference though - is it slightly less garish an orange and a slightly less murky grey?

---

### Post by georgelappies on 2013-02-24
> **tpprynn said:**
> In the olden days, I would paste a different version of the Clearlooks metacity border into the inferior one's file, replacing the sketchy version. You could do a version of that. Or you could see if the ubuntu light-themes packages from 12.10 will install without griping about dependencies, taken from packages.ubuntu.com. For the former method I assume as you've been using Ubuntu two years longer than me that you can open the file system as route and navigate to the relevant folder.

I didn't notice a difference though - is it slightly less garish an orange and a slightly less murky grey?

Thanks, will definitely try that. The biggest changes are in the shape of the buttons and the indicator bars etcetera. They do not look as flat in 12.10 when compared to 12.04.

---

### Post by zombifier25 on 2013-02-24
I wouldn't hold my breath though, since it's possible that the newer light themes is only made to work with GTK 3.6, not 3.4.

It wouldn't hurt if you try, but instead of replacing the current theme you should extract the .deb package for the themes and put them in .themes. That way you can safely try the theme without potentially borking your system.

---

### Post by georgelappies on 2013-02-24
> **zombifier25 said:**
> I wouldn't hold my breath though, since it's possible that the newer light themes is only made to work with GTK 3.6, not 3.4.

It wouldn't hurt if you try, but instead of replacing the current theme you should extract the .deb package for the themes and put them in .themes. That way you can safely try the theme without potentially borking your system.

Thanks, that is the way I did it ;) The colors are all messed up and it just looks fugly. Pity, was looking forward to it.

---

