---
title: "Invisible Usb"
date: 2022-04-25
forum: General Help
---

### Post by ioanis on 2022-04-25
Hello
I have Lubuntu and I formated an usb ( disk - format disk ) for installing puppy Linux on Usb . The icon of Usb on desktop disappeared  .
Tough i can see it on disk , terminal and Gparted .
I have tried to write the puppy linux iso image on Usb with Unetbootin but appears this message "You must first mount the USB drive /dev/sdb to a mountpoint ...." . I've found on net how to format on terminal  : delete usb , create partition table , format new volume .
With no results on Unetbootin or showing icon .
Please I need an advice for dummies . I don't know technical stuff .
Thanks

---

### Post by aug7744 on 2022-04-25
Try Etcher

---

### Post by QIII on 2022-04-26
> **aug7744 said:**
> Try Etcher

What does this mean?  How is this accomplished?  Your answer is far from supportive.

---

### Post by aug7744 on 2022-04-26
Balena Etcher create USB drive for installation.
Search in internet.

---

### Post by yancek on 2022-04-26
Are you using the instructions at the official Unetbootin site, link below?  If not try doing that.

[https://unetbootin.github.io/](https://unetbootin.github.io/)

Unetbootin generally works better if the device is formatted FAT32.  Is that what you did?  At what point in the process do you see the error message indicating you need to mount first?

---

### Post by yancek on 2022-04-26
Are you using the instructions at the official Unetbootin site, link below?  If not try doing that.

[https://unetbootin.github.io/](https://unetbootin.github.io/)

Unetbootin generally works better if the device is formatted FAT32.  Is that what you did?  At what point in the process do you see the error message indicating you need to mount first?

---

### Post by ioanis on 2022-04-26
Thanks guys ,
I have solved halfway . From same PC with Lubuntu I have also installed puppy Linux  . I've burned iso image on usb with a program from puppy Linux -something like Bootable USB creator  . I put it again on Lubuntu and worked , it appeared on desktop .
I run it through Bios but didn't appeared .
So I went back to store were I bought the USB , gave it back and received my money . Now I used another old USB of just 2 gb and downloaded Balenaetcher . Worked smoothly. I have tried to run this USB on another PC that I've got (a little better than the one with Lubuntu) but didn't worked . I guess the problem was that I used a 32 bit puppy Linux but probably this pc is for 64 bit  . I will try this later .

---

