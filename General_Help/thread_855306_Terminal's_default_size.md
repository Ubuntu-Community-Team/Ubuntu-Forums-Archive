---
title: "Terminal's default size"
date: 2008-07-10
forum: General Help
---

### Post by enchance on 2008-07-10
Is there a way to change the terminal's default size? I always have to resize it to something bigger whenever I open it the first time.

---

### Post by Slim Odds on 2008-07-10
Yes, add the "+geometry XxY"  parameters to the command line, where X and Y are the dimension that you want

---

### Post by enchance on 2008-07-10
> **Slim Odds said:**
> Yes, add the "+geometry XxY"  parameters to the command line, where X and Y are the dimension that you want

Did I do this right? I typed in
```
gnome-terminal +geometry 103x28
```
but nothing's changed.

---

### Post by Dr Small on 2008-07-10
Just a whimsical thought since I don't use gnome-terminal anymore, but it should be:
```
gnome-terminal --geometry 103x28
```

More information for it should be in the manual:
```
man gnome-terminal
```

Dr Small

---

### Post by enchance on 2008-07-10
> **Dr Small said:**
> Just a whimsical thought since I don't use gnome-terminal anymore...

Dr Small

Really? What do you use?

---

### Post by Dr Small on 2008-07-10
> **enchance said:**
> Really? What do you use?
[Sakura](http://pleyades.net/david/sakura.php).
It's probably in Ubuntu's repositories, too.

---

### Post by enchance on 2008-07-11
This one works!
```
gnome-terminal --geometry 103x28
```

---

