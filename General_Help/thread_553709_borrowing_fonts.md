---
title: "borrowing fonts"
date: 2007-09-18
forum: General Help
---

### Post by dave666 on 2007-09-18
I’ve been playing with ubuntu at home for a few weeks and like what I’m discovering. The command line is still a pain I wish I had come here before I got used to windows. It wouldn’t have been such a pain if I still had to work with dos on a daily basis. Any way I have found something I really love and it’s some of the fonts. Is it possible to transfer font from ubuntu to my windows machine at work. TSCu_times is the one I seem to have started to use a lot, but there are a few that I used at home but can’t get at work.     

Thanks for any help
Dave666

---

### Post by por100pre1 on 2007-09-18
First make a fonts folder:

```
mkdir .fonts
```

Now open your user folder and press crtl+H to see your hidden folders.

Copy your **.ttf** fonts form the Windows/Fonts folder to the .fonts folder in your Ubuntu user folder.

Logout or reboot.

---

### Post by dave666 on 2007-09-18
Thanks I did that and it worked to get my windows font to my home computer:), but how do I do it the other way around to get my ubuntu fonts to my windows computer:confused: I can find them but they don't seem to want to copy:confused:. I have to copy them to floppy or a pen drive though. my windows computer is at work.I decided that if i didn't have windows on the computer at home i would have to make linux work and not give up and go back to windows as i had in the past.:)

thanks Dave666

---

### Post by por100pre1 on 2007-09-18
You can try using Nautilus in superuser mode for that:

```
gksudo nautilus
```

but **I don't recommend it** because it can mess up your removable media permissions...

---

### Post by dave666 on 2007-09-18
How do I become a superuser, in windows I just am, in linux I can even make myself root. :confused::(
dave666

---

### Post by maybeway36 on 2007-09-18
press alt+F2 and type:
```
gksu nautilus
```

---

### Post by dave666 on 2007-09-18
thanks i'll try that. if it messes up a floppy disk i won't cry too much:)

thanks again 

dave666

---

