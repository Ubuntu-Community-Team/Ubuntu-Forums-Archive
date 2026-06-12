---
title: "Flash problem"
date: 2008-06-11
forum: General Help
---

### Post by nic89 on 2008-06-11
Recently, I've upgraded to Ubuntu 8.04. Well...I did the partial upgrade procedure and I have Firefox 3. The problem is: I am having trouble viewing any video that requires Flash. The sound streams well but the video displays picture frame by frame like a closed-circuit security camera.

I figured that reinstalling Adobe Flash would do the trick but the result shows no improvement. Can anyone help me out?

For the record, I am a novice Linux user but I'm ever improving :)
I also apologize if a similar thread was posted before...too sick to search around.

---

### Post by iaculallad on 2008-06-11
Try installing libflashsupport:

```
sudo apt-get install libflashsupport
```

---

### Post by nic89 on 2008-06-11
The frames go by a bit faster after the installation. I think we're getting closer.

---

### Post by iaculallad on 2008-06-11
What about installing [Gnash]("http://www.gnu.org/software/gnash/") to replace your proprietary Adobe Flash?

---

### Post by nic89 on 2008-06-11
Gnash certainly does look promising. I'll try it when I come home this afternoon and give you an update of the results.

---

### Post by nic89 on 2008-06-16
gnash works just fine! thanks

---

