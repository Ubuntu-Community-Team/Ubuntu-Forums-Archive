---
title: "[SOLVED] Poblem with caps in &amp;quot;R&amp;quot; and &amp;quot;Q&amp;quot;."
date: 2008-05-23
forum: General Help
---

### Post by pogztimz on 2008-05-23
i have a pRoblem typing loweR case foR "R" and "Q".. pls help me... as you may have noticed i am using uppeR case foR letteR "R"...:confused:

---

### Post by mali2297 on 2008-05-23
How QueeR.

To troubleshoot...
Is it the same in all applications? 
Have you had this problem since installation of Ubuntu 8.04? 
What happens if you press Shift+R?

---

### Post by bingoUV on 2008-05-23
Can you post the output of the following command?
```

xmodmap -pke

```

---

### Post by pogztimz on 2008-05-24
> **mali2297 said:**
> How QueeR.

To troubleshoot...
Is it the same in all applications? 
Have you had this problem since installation of Ubuntu 8.04? 
What happens if you press Shift+R?

 
SeRiuosly.. i cant PRint oR Type loweR case of R.. the same foR Q..
i know my keyboaRd is woRking fine bcoz i can log in.. (my passwoRd has letteR R on it.)..

1. it is the same foR all applications.
2. afteR i installed 8.04, it woRked peRfectly fine. but i Really cant RemembeR when this pRoblem StaRted.
3. if i pRess Shift+R i get "R" :)

help me pls..

---

### Post by pogztimz on 2008-05-24
> **bingoUV said:**
> Can you post the output of the following command?
```

xmodmap -pke

```


heRe is the link.. pls tRy to look..

[http://www.pastebin.ca/1027676](http://www.pastebin.ca/1027676)

---

### Post by mali2297 on 2008-05-24
> **pogztimz said:**
> heRe is the link.. pls tRy to look..

[http://www.pastebin.ca/1027676](http://www.pastebin.ca/1027676)
```

keycode  24 = q Q
keycode  25 = w W
keycode  26 = e E
keycode  27 = r R

```
I can't see anything wrong here.

Can you rule out that the keyboard may have been damaged? Have you tried it on another system?

---

### Post by pogztimz on 2008-05-24
> **mali2297 said:**
> ```

keycode  24 = q Q
keycode  25 = w W
keycode  26 = e E
keycode  27 = r R

```
I can't see anything wrong here.

Can you rule out that the keyboard may have been damaged? Have you tried it on another system?

actually i tried it on another system,and yes, my keyboard works perfectly fine..

---

### Post by mali2297 on 2008-05-25
Can you confirm that r and q work at the login screen? (Try typing in the name entry.)

Create a new user (through System -> Administration -> Users and Groups) and log in as this person. Do you encounter the same problem?

---

### Post by mali2297 on 2008-05-27
There is a hidden file **.gconf** in your home directory, try removing it. 

(The idea comes from the this [thread]("http://ubuntuforums.org/showthread.php?t=806139").)

---

### Post by kdwillia on 2008-05-27
Have you tried a different keyboard?   It could be a hardware issue.   You could also boot with a LiveCD and see if the problem is still there... if it is.. you have a bad keyboard.

---

