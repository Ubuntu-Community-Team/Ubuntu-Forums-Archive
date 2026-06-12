---
title: "[SOLVED] Using the 'top' application."
date: 2006-12-30
forum: General Help
---

### Post by chrismyers on 2006-12-30
Hi there,

I'm having difficulty navigating. I'm absolutely convinced that there is more than just one screen of running applications, but I don't know how to step through pages.

Anyone know how to use the 'top' application properly? Or point me in the direction of some good info.

Cheers in advance :-)

---

### Post by msandoy on 2006-12-30
I do not know if there is a way to scroll trough more than one screen in the top app., but if you type ps -All in a console, you will see all the running processes.
Hope this helps... :-)

---

### Post by po0f on 2006-12-30
chrismyers,

Use `[htop](http://packages.ubuntu.com/edgy/utils/htop)`, it's a lot better than `top`, plus it's in color!  You'll have to enable universe repos to install it if you haven't already.

---

### Post by hikaricore on 2006-12-30
> **chrismyers said:**
> Hi there,

I'm having difficulty navigating. I'm absolutely convinced that there is more than just one screen of running applications, but I don't know how to step through pages.

Anyone know how to use the 'top' application properly? Or point me in the direction of some good info.

Cheers in advance :-)

I believe Shift+> and Shift+< cycle through the pages, you can also hit the "h" key while top is running to see a list of commands.  If this does not help, try:

```
man top
```

From a terminal to read the documention on top in the man pages.

---

### Post by chrismyers on 2006-12-31
> **po0f said:**
> chrismyers,

Use `[htop](http://packages.ubuntu.com/edgy/utils/htop)`, it's a lot better than `top`, plus it's in color!  You'll have to enable universe repos to install it if you haven't already.

Wow! this really is nice.

Thanks, just what I needed. :mrgreen:

---

### Post by chrismyers on 2006-12-31
> **msandoy said:**
> I do not know if there is a way to scroll trough more than one screen in the top app., but if you type ps -All in a console, you will see all the running processes.
Hope this helps... :-)

Nice quick check this.

Cheers.

---

