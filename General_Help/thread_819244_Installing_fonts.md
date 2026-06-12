---
title: "Installing fonts"
date: 2008-06-05
forum: General Help
---

### Post by Grimnir512 on 2008-06-05
Hi there :)

I'm using Ubuntu 8.04 and I have a large dump of .ttf fonts that I'd like to install. Is there a folder where I can just dump the files or do I need to do something else?

Grimnir512

---

### Post by talktoari on 2008-06-05
Maybe this howTO guide can help you
[http://ubuntuforums.org/showthread.php?t=85139&highlight=ttf](http://ubuntuforums.org/showthread.php?t=85139&highlight=ttf)

Also you can refer:
[http://www.wikihow.com/Install-ttf-Fonts-on-Ubuntu](http://www.wikihow.com/Install-ttf-Fonts-on-Ubuntu)

Its very easy to install fonts on Ubuntu. Have a good luck with it..!!:)

---

### Post by didac on 2008-06-05
Type in the Nautilus address bar:

```
fonts:///
```

and start dragging fonts to that windows. They get installed

---

### Post by Grimnir512 on 2008-06-05
> **talktoari said:**
> Maybe this howTO guide can help you
[http://ubuntuforums.org/showthread.php?t=85139&highlight=ttf](http://ubuntuforums.org/showthread.php?t=85139&highlight=ttf)

Also you can refer:
[http://www.wikihow.com/Install-ttf-Fonts-on-Ubuntu](http://www.wikihow.com/Install-ttf-Fonts-on-Ubuntu)

Its very easy to install fonts on Ubuntu. Have a good luck with it..!!:)

Got it! Thanks :)

---

### Post by mrMango on 2008-06-05
> **didac said:**
> Type in the Nautilus address bar:

```
fonts:///
```

and start dragging fonts to that windows. They get installed
"Couldn't display fonts:///

Nautilus cannot handle fonts: locations."

---

### Post by Kevbert on 2008-06-05
> **mrMango said:**
> "Couldn't display fonts:///

Nautilus cannot handle fonts: locations."

That doesn't seem to work any more (8.04).  Create yourself a .fonts directory in your home folder.  Then in terminal (once you've put all your new ttf files in there) enter
 ```
sudo fc-cache -fv
```

---

