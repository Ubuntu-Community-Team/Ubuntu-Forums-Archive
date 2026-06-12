---
title: "Noobie with questions"
date: 2008-07-05
forum: General Help
---

### Post by darksoul7 on 2008-07-05
Ok... I have an absolute noob question since I'm brand new to Linux and a more complex question following.

Noob question - What's the terminal command to edit a locked py file in gedit from Terminal? sudo ???? <location> gedit???

The more complex question is this. I'm French Canadian and I am using the US International keyboard layout but I can't seem to get the little squiggly under the C (I don't know what it's called in English). In Windows I just had to type ' then c. Also, I seem to just get nothing if I type ' and a letter that does not accept an accent (ie. typing don't requires me to type a space after the ') is there a way to fix this? 

Thanks in advance!

---

### Post by YaroMan86 on 2008-07-05
> **darksoul7 said:**
> Ok... I have an absolute noob question since I'm brand new to Linux and a more complex question following.

Noob question - What's the terminal command to edit a locked py file in gedit from Terminal? sudo ???? <location> gedit???

The more complex question is this. I'm French Canadian and I am using the US International keyboard layout but I can't seem to get the little squiggly under the C (I don't know what it's called in English). In Windows I just had to type ' then c. Also, I seem to just get nothing if I type ' and a letter that does not accept an accent (ie. typing don't requires me to type a space after the ') is there a way to fix this? 

Thanks in advance!

Assuming you mean a Python file in a root access-only area:

```
gksudo gedit /path/to/file.py
```

---

### Post by flytripper on 2008-07-05
arr i concur Dr. Yaroman86 arr

---

### Post by darksoul7 on 2008-07-05
ARR! That worked! Thanks, now I can finally get ClearWeather to work! HAHA!

Any idea about the international characters problem I am having?

I have to admit, I absolutely love how helpful the Ubuntu community is! I'm sure I will love it here :D

---

### Post by darksoul7 on 2008-07-05
Well, that didn't fix my Screenlets, but that command was exactly what I was looking for. Thank you both again!

---

### Post by karasuman on 2008-07-05
I think it's called a cedille in English, just like in French.  I don't know another word for it, anyway.  :)  

Have you tried Applications -> Accessories -> Character Map?

---

### Post by VMC on 2008-07-05
Also, if you go to System > Preferences > Keyboard, you can use add to add Canadian layout.

---

### Post by jocko on 2008-07-05
> **darksoul7 said:**
> Any idea about the international characters problem I am having?
Sometimes wikipedia may be very helpful. [Here's the US-International keyboard layout]("http://en.wikipedia.org/wiki/Image:KB_US-International.svg").
I would guess Alt Gr + , would do it?

---

