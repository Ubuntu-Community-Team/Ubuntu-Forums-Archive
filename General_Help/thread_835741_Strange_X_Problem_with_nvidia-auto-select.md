---
title: "Strange X Problem with nvidia-auto-select"
date: 2008-06-20
forum: General Help
---

### Post by arbitrabbit on 2008-06-20
I have a very strange X Problem. I am using NVidia 6200SE with Hardy and a monitor and TV are connected to the computer. The problem is that my monitor (Viewsonic VA903M) supports a maximum of 1280x1024@75Hz mode and when I start X, on the login screen and for the first few seconds, I can see that it has started at 1280x1024, but after that my monitor is automatically set to 1024x768 by nvidia-auto-select (scroll towards end of Xorg log). I was wondering if there is anyway to prevent this?


The Xorg log and xorg.conf are attached herewith

---

### Post by Pjotr123 on 2008-06-20
Try this:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 2 )

---

### Post by arbitrabbit on 2008-06-20
> **Pjotr123 said:**
> Try this:
[http://ubuntutip.googlepages.com/bugsinubuntu](http://ubuntutip.googlepages.com/bugsinubuntu)
(number 2 )

Nopes, the screen resolution tool doesn't really work with nvidia driver and I have already tried nvidia-settings but can't solve this issue. I can change the resolution manually using nvidia-settings but then I have to do it every time I start X

---

### Post by Pjotr123 on 2008-06-20
> **arbitrabbit said:**
>  I can change the resolution manually using nvidia-settings but then I have to do it every time I start X

You wouldn't have to repeat that every time, if you followed my how-to. Because that says you have to put gksudo before that command.  :-)

---

### Post by arbitrabbit on 2008-06-20
> **Pjotr123 said:**
> You wouldn't have to repeat that every time, if you followed my how-to. Because that says you have to put gksudo before that command.  :-)

Did that and no, still doesn't solve the issue. The resolution reverts back to 1024x768 on restart

---

