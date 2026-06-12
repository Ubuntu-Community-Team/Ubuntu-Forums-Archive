---
title: "save access denied"
date: 2007-10-05
forum: General Help
---

### Post by Sofie on 2007-10-05
How can I get access to edit and save a root file?


I want to change a root file to get Ubuntu to recognize my notebooks quick launch buttons. I can change the file, but when I try to save, ubuntu says: access denied. How can I get acces to edit and save the file? The file is: /etc/modprobe.d/options.
I did ad my user profile to the root group, but it still says: "You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.
" when I try saving the file?

I am using Amilo A 1650 G. If you are having trouble with the quick launch buttons, see: 
[http://damagedspline.blogspot.com/2007/03/fsc-amilo-a1650g-ubuntu-fiesty-32bit.html](http://damagedspline.blogspot.com/2007/03/fsc-amilo-a1650g-ubuntu-fiesty-32bit.html)

Sofie

---

### Post by elliotjreed on 2007-10-05
Try

```
sudo /etc/modprobe.d/options.
```

That will edit the file as root user, giving you max. permissions

or 

```
sudo gedit /etc/modprobe.d/options.
```

---

### Post by shad0w_walker on 2007-10-05
You probably aren't running as root. Try this command, back up the file before you start tinkering though.

Press Alt + F2 to open up the run dialog and try this.

```
gksu gedit /etc/modprobe.d/options
```

You will be asked for your password before it runs gedit as root and opens up your file. Should be able to save now.

---

### Post by Sofie on 2007-10-05
Thank you. But I am that new, so I do not know where to put the code?

---

### Post by elliotjreed on 2007-10-05
In the terminal! Whenever anyone gives you a code, I always goes in the terminal!

Don't worry! I've only been using Ubuntu for a week, it gets easier!!!

---

### Post by Sofie on 2007-10-05
Thank you so much. Yes, it gets easier quickly. I am already loving Ubuntu!

Ill certinly pass it on!

---

