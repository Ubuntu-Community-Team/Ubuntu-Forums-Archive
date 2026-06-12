---
title: "GRUB - how can I edit preferences?"
date: 2004-11-11
forum: General Help
---

### Post by Monika on 2004-11-11
Well, if I manage to tweek Ubuntu to work for me like I need it to (and if it's going to happen for me with any linux distribution in the near future, then it looks like it's going to be this one :) ), then I'll be installing it on my mum's computer alongside her windows. The thing is that she won't be convinced into having it on her computer if the default system to boot is Ubuntu and she has 10seconds to make a decision about it. For me this default GRUB setting works fine, but I know that for her it won't - at least not at first.

So how do I change this? :)

---

### Post by JProgrammer on 2004-11-11
you change the default boot option it is a zero based index so windows is probably 3 ie

Ubuntu - 0
Ubuntu safe - 1
Other OS - 2
Windows 3


This is assuming you have a default grub

just edit /boot/grub/menu.lst

with vim gedit nano. Whatever you want

sudo vim /boot/grub/menu.lst

and if your mother thinks 10 seconds is too long like my wife does change the delay to 3 and you know when you want to boot Linux so you can do it within the 3 seconds

---

### Post by Monika on 2004-11-12
Thanks :)
And my mum is weird, 10s is too little for her ;)

---

### Post by iminj on 2004-11-12
Another option is to install "grubconf" from the repository. It's a GUI-based package that makes editing your GRUB options simple. 

iminj

---

