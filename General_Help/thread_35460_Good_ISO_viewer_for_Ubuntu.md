---
title: "Good ISO viewer for Ubuntu?"
date: 2005-05-19
forum: General Help
---

### Post by DutchLau on 2005-05-19
Hello Ubuntu community! 

What is a good ISO viewer (such as winiso in windows) that I can use on my Ubuntu platforms? Anyone have any suggestions that I can "apt-get" or is it more complicated than that?

Thanks,

DutchLau

---

### Post by kvidell on 2005-05-19
[QUOTE=DutchLau]Hello Ubuntu community! 

What is a good ISO viewer (such as winiso in windows) that I can use on my Ubuntu platforms? Anyone have any suggestions that I can "apt-get" or is it more complicated than that?

Thanks,

DutchLau[/QUOTE]
 Viewer?
I donno what that means...
This is what I usually do:
```
cd
mkdir vcd
sudo mount -o loop /path/to/iso.iso ~kvidell/vcd
cd vcd
ls
[file output happiness]
```

I just mount the ISO as a loopback filesystem.
Works like a charm.
- Kev

---

### Post by DutchLau on 2005-05-19
Thanks for the speedy reply.

I already saw something about doing this, but bleh.. I want a pampered little program that will just open the iso and let me see what's inside  :grin:  No just kidding, I'm going to try this as soon as my iso is done downloading  :) 

Thanks,

Any other ISO programs/tricks out there?

EDIT: Works like a charm! I even get a nice folder in "computer" umount works perfectly also

---

### Post by Sam on 2005-05-19
A little [search](http://ubuntuforums.org/search.php?q=iso) would give you:
[list][*][Two scrips for managing iso files](http://ubuntuforums.org/showthread.php?t=33881)
[*][Virtual Cdrom](http://ubuntuforums.org/showthread.php?t=34053)
[*][How to create ISO images from your HD CD DVD](http://ubuntuforums.org/showthread.php?t=6509)
[*]...[/list]

---

