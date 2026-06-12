---
title: "Copying a website for ofline viewing?"
date: 2007-06-07
forum: General Help
---

### Post by rob1101 on 2007-06-07
how can i copy a website ( i think it is called mirroring ) to my HDD so i can view them offline? i remember i had a program many years ago that did this. but that was for windows. any help would be great, thanks

---

### Post by raul_ on 2007-06-07
just Save the page (from the file menu i think)

---

### Post by rob1101 on 2007-06-07
> **raul_ said:**
> just Save the page (from the file menu i think)

well that works just for one page and it just takes the html and its not all formated and stuff with the CSS. 

what i want to do is copy some sites that have several pages and keep the formating. for viewing offline.

---

### Post by AnRa on 2007-06-07
You can use httrack ;)

---

### Post by pbw on 2007-06-07
*nod* httrack is good. wget with mirror flag should also do the trick

---

### Post by bashologist on 2007-06-07
You could use the wget "-k" switch, which converts the webpages links to that they're linking locally. And optionally use the "-r" switch to copy the entire server. I've never tried the "mirror" option, but that might work aswell.
```
wget -kr [http://www.example.com/](http://www.example.com/)
```

---

### Post by pbw on 2007-06-07
bashologist, cool. i didn't know about the k flag. The -m (mirror option just automatically adds a few flags for you)

> 
-m
Turn on options suitable for mirroring.  This option turns on recursion and time-stamping, sets infinite recursion depth and keeps FTP directory
           listings.  It is currently equivalent to -r -N -l inf --no-remove-listing.


---

