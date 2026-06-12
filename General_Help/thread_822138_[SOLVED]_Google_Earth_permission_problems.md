---
title: "[SOLVED] Google Earth permission problems"
date: 2008-06-07
forum: General Help
---

### Post by ARhere on 2008-06-07
This is going to drive me nuts.

When I run Google Earth, it stops at the star field and no earth appears.

If I use "sudo" to start Google Earth, no problems.  So obviously permission problems.

I did not install the .bin as root, but as the main user.

](*,)  -AR

---

### Post by overdrank on 2008-06-08
> **ARhere said:**
> This is going to drive me nuts.

When I run Google Earth, it stops at the star field and no earth appears.

If I use "sudo" to start Google Earth, no problems.  So obviously permission problems.

I did not install the .bin as root, but as the main user.

](*,)  -AR

HI and you can right click on the applications and choose edit menus. Then locate the google earth right click and right click select properties and add gksu at the command line. It may be just a patch but it works for me. :)

---

### Post by IcemanV9 on 2008-06-08
That's what happened when you clicked the "Start" button when the installation was done. And, it was owned by root (sudo) in your own home directory.

Anyway, it is fixable. In the terminal, type ...
```
sudo chown -R $USER:$USER .config/
```

---

### Post by ARhere on 2008-06-08
Thank you Ice, that solved it!

---

### Post by hardyn on 2008-08-21
> **IcemanV9 said:**
> That's what happened when you clicked the "Start" button when the installation was done. And, it was owned by root (sudo) in your own home directory.

Anyway, it is fixable. In the terminal, type ...
```
sudo chown -R $USER:$USER .config/
```

What does the $USER:$USER do?

---

### Post by seshomaru samma on 2009-02-03
Thank you
I encountered the same problem on Hardy and the command solved it...

---

### Post by amadeus244 on 2009-12-26
Thanks this work perfectly for me , but do you know if this is a problem documented by Google ?

---

