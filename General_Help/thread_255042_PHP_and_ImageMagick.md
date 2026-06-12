---
title: "PHP and ImageMagick"
date: 2006-09-10
forum: General Help
---

### Post by simon360 on 2006-09-10
What program/extension would I want for accessing ImageMagick and resizing an image from a PHP script?

---

### Post by simon360 on 2006-09-11
Anyone know?

---

### Post by Colonel Kilkenny on 2006-09-11
I don't know about ImageMagick or system commands but is there a particular reason you cannot use GD and imagecopyresampled?

---

### Post by simon360 on 2006-09-11
I'm not really sure of what those are... if they're built in, any chance of telling me how to use them? Thanks!

---

### Post by David Corrales on 2006-09-11
What I did once was an external script that I called from PHP. Worked well enough for my needs.

---

### Post by frankabel on 2008-01-22
This package provides a wrapper for ImageMagick library directly from PHP scripts.

sudo apt-get install php5-imagick

Salute
Frank Abel

---

