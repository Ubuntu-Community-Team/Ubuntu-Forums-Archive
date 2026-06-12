---
title: "right arrow key doesnt work"
date: 2007-02-22
forum: General Help
---

### Post by corytoneill on 2007-02-22
My right arrow key stopped working, i think it is because i messed with the keyboard short cuts, but i cannot figure out how to fix it. is there anyways to go back to the default keyboard shortcuts??? help

---

### Post by Grog140 on 2007-02-22
That very same thing happened to me once upon a time. With the same key as well. I couldn't fix it without doing a reinstall but I went a few months just executing the following every time I boot the computer:

```
xmodmap -e "keycode 102 = Right"
```

See if that works. And if it is anything like what happened to me then it will forget that configuration when you reboot (and maybe if you logout).

---

### Post by corytoneill on 2007-02-23
wow thanks

---

### Post by gradedcheese on 2007-02-23
> 
I couldn't fix it without doing a reinstall but I went a few months just executing the following every time I boot the computer


I hope you actually mean that you added it to /etc/rc.local right? ;)

---

