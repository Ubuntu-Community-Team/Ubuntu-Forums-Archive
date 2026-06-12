---
title: "Weird Display On Ubuntu Install Screen Please Help"
date: 2016-02-13
forum: General Help
---

### Post by Patrick_S on 2016-02-13
Like the title says idk what to do here is image.
[https://drive.google.com/a/g.mvusd.net/file/d/0BwpWAlrNaIzNX01VWngwNlRHLUU/view?usp=docslist_api](https://drive.google.com/a/g.mvusd.net/file/d/0BwpWAlrNaIzNX01VWngwNlRHLUU/view?usp=docslist_api)

---

### Post by branau on 2016-02-13
I'm unable to see the image without logging into a Google account, any chance you could attach the image here? And when are you getting this error? Can you provide more details?

---

### Post by Patrick_S on 2016-02-13
Yes here
[http://s13.postimg.org/6digmhcsn/20160212_233818.jpg](http://s13.postimg.org/6digmhcsn/20160212_233818.jpg)

---

### Post by Patrick_S on 2016-02-13
And I am getting the error when I press enter on install Ubuntu. At the top all it says is ignoring bgrt: invalid status 0 (except 1)

---

### Post by branau on 2016-02-13
Can you [check the md5sum](https://help.ubuntu.com/community/HowToMD5SUM#MD5SUM_on_Windows) of the ISO file that you downloaded and verify that it's a match?

---

### Post by Patrick_S on 2016-02-13
It says they are the same

---

### Post by branau on 2016-02-13
Which method did you use to set up your USB?

---

### Post by Patrick_S on 2016-02-13
I used universal USB installer 1.9.6.3 to create the ISO to a USB format

---

### Post by branau on 2016-02-13
Looks like you're not the only one to have this issue. Check out this {url=http://askubuntu.com/a/482977]answer on Ask Ubuntu[/url].

From Windows, edit/add the following line in your /boot/grub.cfg on the USB drive like so:

```
set gfxmode=1024x768
```

In addition, the answer recommends [setting the nomodeset option]("http://ubuntuforums.org/showthread.php?t=1613132")

---

### Post by Patrick_S on 2016-02-13
TY SO MUCH!!! It booted correctly now

---

### Post by branau on 2016-02-13
Glad I could help :)

If all is good for this now, could you please mark the thread as solved?

---

