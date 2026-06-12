---
title: "System does not halt from terminal"
date: 2013-02-08
forum: General Help
---

### Post by codingman on 2013-02-08
I used to be able to shutdown from the terminal by using halt or by using sudo shutdown, to shutdown via terminal but neither of those work. 

Has something changed since 11.10? Because that was the last time either of these commands worked. I use the commands and everything works all right, but 
then it gets stuck on the end and I need to shutdown manually (wince).

---

### Post by Cheesemill on 2013-02-08
Does this work?
```
sudo shutdown now -h
```

---

### Post by codingman on 2013-02-08
No.

---

### Post by slickymaster on 2013-02-08
Have you tried using **_halt_** instead of shutdown?
Halt can be more aggressive when shutting down than shutdown itself. It has parameters than can literally force the system to shutdown without regarding services or opened programs. If you run halt without any parameters it will simply execute the shutdown command. Something like an alias. If you run it for example with the parameter **_--force_** it will "force" it will force the system into a reboot really fast.

---

### Post by codingman on 2013-02-08
Please review my original post.

---

### Post by bantuvez on 2013-02-08
Try this:

```
sudo poweroff
```

---

### Post by slickymaster on 2013-02-08
> **codingman said:**
> Please review my original post.

I did saw your original post, the problem was that I forgot to finish my post, so I didn't append the command I was intending you to try:
```
sudo halt -n -d
```

---

### Post by codingman on 2013-02-08
> **bantuvez said:**
> Try this:

```
sudo poweroff
```

I will try.

---

### Post by codingman on 2013-02-08
> **slickymaster said:**
> I did saw your original post, the problem was that I forgot to finish my post, so I didn't append the command I was intending you to try:
```
sudo halt -n -d
```

This has the same effect as if I were to run halt.

---

### Post by codingman on 2013-02-08
sudo poweroff did the trick for me!

---

### Post by codingman on 2013-02-08
I also have a problem with suspend, I have tried sudo suspend and using the usual GUI yet when I log back on there is a black-and-white pattern like one you would see when a VGA cable is defective.

---

### Post by codingman on 2013-02-09
bump

---

