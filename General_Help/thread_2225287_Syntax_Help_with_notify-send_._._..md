---
title: "Syntax Help with notify-send . . ."
date: 2014-05-20
forum: General Help
---

### Post by BuntuSeriously on 2014-05-20
Hello folks!

Here's a simple question for the community tonight:

What is the properly-formed commandline/bash to display a popup image with notify-send using image_data?  Need to specify height & width parameters; so -i is not useful in this case.

My attempt:```
notify-send 'Some Message' image_data 250, 250, , , , , ~/Desktop/test.png
```...returns the following error:```
Invalid number of options.
```Here's the apparently relevant supporting documentation from [The Galago Project]("http://www.galago-project.org/specs/notification/0.9/notification-spec-0.9.txt"), as referenced by the manpages:

> image_data  (iiibiiay)
This is a raw data image format which describes the width, height, rowstride, has alpha, bits per sample, channels and image data respectively.  We use this value if the icon field is  left blank.

Anyone know what's the correct commandline/bash syntax to make this work as described???

FWIW, running 12.04 --


Thanks ;)

---

### Post by Habitual on 2014-05-21
image data cannot be embedded in the message itself. Images referenced     must always be local files

from [https://developer.gnome.org/notification-spec/](https://developer.gnome.org/notification-spec/)

---

