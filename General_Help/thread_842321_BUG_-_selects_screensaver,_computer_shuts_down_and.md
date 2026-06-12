---
title: "BUG? - selects screensaver, computer shuts down and goes to login screen"
date: 2008-06-27
forum: General Help
---

### Post by tunznath on 2008-06-27
Hi
If I select system>preferences>screensaver the computer shuts down and goes to login screen where i have to fill in user and password - anyone know why and how to fix it?
thanks
Nath

---

### Post by tunznath on 2008-06-27
OK this is now not a joke anymore- after 10 mins of not using the computer it just shuts down and goes to the login screen - I cant access the screensaver pael to see whats happening, when ai do it just shuts down to the login screen - 
is there a way to reinstall the screensaver program, or should I reinstall ubuntu? - If I have to reinstall ubuntu how do I do it, and how do i save my settings - I am dual booting

---

### Post by tunznath on 2008-06-27
I think I have solved it - I selected screensaver - system preferences screensaver, and quickly clicked into the pane that has the different screensavers, and got a random screensaver, this stopped the computer shutting down, then I deselected the after 10 mins option, and now I think it works - the problem screensaver seems to have been the one called matrix view -  the one that draws faces in the falling matrix letters - is this a standard screensaver - or is it one I downloaded from somewhere (i cant remember) - if it is a downloaded one how can I delete it - where are the screensaver files kept?
Hope this helps someone if they have the same problem.

---

### Post by Vivaldi Gloria on 2008-06-27
> **tunznath said:**
> the problem screensaver seems to have been the one called matrix view

I have that ss but it works fine for me. 

I guess somewhat you video driver cannot handle that ss. Does Hardware drivers in the system menu > administration show any uninstalled drivers?

---

### Post by tunznath on 2008-06-27
i can look if you tell me where to look -GLmatrix works OK but not  matrix view

---

### Post by Vivaldi Gloria on 2008-06-27
> **tunznath said:**
> i can look if you tell me where to look -GLmatrix works OK not the other matrix view

On the top panel click 

system > administration > Hardware drivers.

Does it show any non-selected drivers?

---

### Post by tunznath on 2008-06-27
No
Just my software modem is unselected -
ralink RT2570 etc is in use
I am not using propriety drivers for video - I have a ati mobility radeon 7000 card and there arent propriety drivers for it

---

### Post by Vivaldi Gloria on 2008-06-27
Well, then your video driver cannot handle matrixview for some reason and I don't think there is anything that you can do about it.

You can get rid of matrixview by deleting the following files:

```
/usr/lib/xscreensaver/matrixview
/usr/share/applications/screensavers/matrixview.desktop
/usr/share/applnk/System/ScreenSavers/matrixview.desktop
/usr/share/man/man1/matrixview.1.gz
/usr/share/xscreensaver/config/matrixview.xml
```

If I remember correctly, after deleting these files the matrixview will be greyed out in screensaver preferences and it will be unclickable. There is a way to get rid of that line completely from ss perefences but I don't remember it.

---

### Post by tunznath on 2008-06-27
OK I will try that - Thanks for your help on this
nath

---

### Post by cariboo on 2008-06-27
Are you sure you weren't telling the screen saver to lock the screen, that will also take you to a login window. It's great if you don't want anyone to use your computer if you are away from it.

Jim

---

### Post by tunznath on 2008-06-27
Thanks but - No definately not telling it to lock the screen, BTW the preview of matrix view runs ok in the little preview window - I am not going to try it in the big preview screen - I am happy without it working - I prefer GLmatrix anyhow.

---

