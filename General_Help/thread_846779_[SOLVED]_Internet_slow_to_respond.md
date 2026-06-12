---
title: "[SOLVED] Internet slow to respond"
date: 2008-07-01
forum: General Help
---

### Post by jeremy1138 on 2008-07-01
Ever since I installed Ubuntu 8.04 (clean install not upgrade), Firefox seems slow to respond when I click a link or hit reload or type an address in the bar and hit enter.  Once a page starts loading however, it works fine but it's just soo sluggish.  Anyone have any ideas?  Thanks so much!

---

### Post by iaculallad on 2008-07-01
Connection Type: Wired or Wireless?

---

### Post by jeremy1138 on 2008-07-01
> **iaculallad said:**
> Connection Type: Wired or Wireless?

Thanks for the response.  I'm using a wireless connection.  Actually I just fixed the problem by following these instructions:

[http://forevergeek.com/open_source/make_firefox_faster.php](http://forevergeek.com/open_source/make_firefox_faster.php)

I recommend that everyone that uses Firefox and has a broadband connection should use these tweaks.  I used this before but I couldn't remember where I found it.  It works great.

---

### Post by iaculallad on 2008-07-01
You could also do this if it works for you:

```
sudo iwconfig wlan0 rate 54M
```

Anyway, Im glad you found a solution.

---

### Post by jeremy1138 on 2008-07-01
> **iaculallad said:**
> You could also do this if it works for you:

```
sudo iwconfig wlan0 rate 54M
```

Anyway, Im glad you found a solution.

Thanks!  I'll do that too.

---

