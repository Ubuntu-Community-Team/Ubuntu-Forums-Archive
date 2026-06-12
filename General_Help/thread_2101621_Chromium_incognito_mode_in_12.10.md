---
title: "Chromium incognito mode in 12.10"
date: 2013-01-05
forum: General Help
---

### Post by jk3920 on 2013-01-05
Can anyone help me change my Chromium to start in incognito mode both on the panel and in the menu in Lubuntu 12.10? Thanks

---

### Post by dino99 on 2013-01-05
its easy to find how, using google a little, yeah ):P

[http://www.techdrivein.com/2010/09/how-to-make-incognito-mode-default-in.html](http://www.techdrivein.com/2010/09/how-to-make-incognito-mode-default-in.html)

---

### Post by jk3920 on 2013-01-05
I know how to use Google. The steps described there don't apply to Lubuntu 12.10!

---

### Post by vasa1 on 2013-01-05
> **jk3920 said:**
> Can anyone help me change my Chromium to start in incognito mode both on the panel and in the menu in Lubuntu 12.10? Thanks
What do you mean by "both on the panel and in the menu"?

Okay, I think I know what you mean. I've removed the panel one a long time ago, but for the menu one, you need to open /usr/share/applications/chromium-browser.desktop or whatever it's called (I use Chrome) with Leafpad. Find out the correct name by running
```
ls /usr/share/applications
```

Then, look for a line like this:
```
Exec=/opt/google/chrome/google-chrome %U
```

and modify it to
```
Exec=/opt/google/chrome/google-chrome --incognito %U
```

Save the file and you're done.

As I said, instead of google-chrome you'll put in chromium-browser or whatever is correct.

---

### Post by jk3920 on 2013-01-05
You're awesome - thanks.

---

