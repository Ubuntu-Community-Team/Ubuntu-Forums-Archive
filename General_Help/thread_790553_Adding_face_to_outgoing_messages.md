---
title: "Adding face to outgoing messages"
date: 2008-05-11
forum: General Help
---

### Post by olskar on 2008-05-11
Hi,
I wanted to try to add a face to outgoing mails in evolution. However they want me to have an image of a face, in png-format, 48x48 big and be less than 720 bytes big! So far I havent been able to create such a lowsizefile and still see what (yes, what not who) is on the picture. Why is this limit so low? Are you able to create a file that meets this requirements?

---

### Post by FakeOutdoorsman on 2008-05-11
I've seen a few of these on mailing-lists.  Use fewer colors.  In GIMP: Image -> Mode -> Indexed... -> Generate Maximum Palette / Maximum number of colors.  Try 16 colors first, then 8 if it is still too big. Once you have your final PNG file run it through optipng, which will optimize and compress it further without making any visual difference to the image.  It's in the universe repo:
```
sudo aptitude install optipng
```
then
```
optipng -o7 inputimage.png
```

---

### Post by FakeOutdoorsman on 2008-05-11
Attached are a few test images.  The black and white was made with "Use black & white (1 bit) palette" in GIMP instead of choosing 8 or 16 colors.

---

