---
title: "Ubuntu has experienced internal error - Wayland"
date: 2020-05-08
forum: General Help
---

### Post by rpessoa on 2020-05-08
Hello,

Every now and then I get the pop-up error screen saying:

Sorry, Ubuntu 20.04 has experienced an internal error.

When I go to "/var/crash" I see  some files and the last one is named: 

```
_usr_bin_Xwayland.121.crash
```

Any idea what is happening?

---

### Post by TheFu on 2020-05-08
> Any idea what is happening? 

This is a wild guess, but perhaps Xwayland is crashing?
But I get the feeling that isn't the real question.  Have you considered looking at the stack trace in the crash file? Any other crash files from the same 5 min period?  Anything in the system log files?

---

### Post by rpessoa on 2020-05-08
> **TheFu said:**
> This is a wild guess, but perhaps Xwayland is crashing?
But I get the feeling that isn't the real question.  Have you considered looking at the stack trace in the crash file? Any other crash files from the same 5 min period?  Anything in the system log files?

Inside the /var/crash/ I have:
```


-rw-r----- 1 rpessoa  whoopsie 36220057 May  4 16:13 _usr_bin_gnome-shell.1000.crash
-rw-rw-r-- 1 rpessoa  whoopsie        0 May  4 16:14 _usr_bin_gnome-shell.1000.upload
-rw------- 1 whoopsie whoopsie       37 May  4 16:14 _usr_bin_gnome-shell.1000.uploaded
-rw-r----- 1 gdm      whoopsie  3698661 May  8 08:34 _usr_bin_Xwayland.121.crash
-rw-r--r-- 1 root     whoopsie        0 May  8 08:58 _usr_bin_Xwayland.121.upload
-rw------- 1 whoopsie whoopsie       37 May  8 08:58 _usr_bin_Xwayland.121.uploaded


```

Is there a specific part of the crash file I should look or paste here? Because it has a little over 500 lines :)

---

### Post by TheFu on 2020-05-08
Google found this: [https://discourse.ubuntu.com/t/a-better-way-to-debug-wayland/9176](https://discourse.ubuntu.com/t/a-better-way-to-debug-wayland/9176)
I don't use wayland.
My post above was just to ask questions which might help you to figure out the root cause. Each should be considered and follow up.

---

### Post by rpessoa on 2020-05-08
> **TheFu said:**
> Google found this: [https://discourse.ubuntu.com/t/a-better-way-to-debug-wayland/9176](https://discourse.ubuntu.com/t/a-better-way-to-debug-wayland/9176)
I don't use wayland.
My post above was just to ask questions which might help you to figure out the root cause. Each should be considered and follow up.

Thanks anyway.

I hope someone else will be able to help me. 

I am only using Wayland because it came with my 20.04 upgrade. It's my first time "using" it... true is I had no clue what it was before this issue. :p

---

### Post by TheFu on 2020-05-08
X11 has been the display server for 30 yrs now. Different forks of it have come and gone over time. Xorg is the current.  I recall XFree86 from the 1990s. All are based on the MIT project from the 1980s.  You can choose to use X11 through a pre-login choice.  There should be a "gear" icon. Click on that, see what's there.  

I haven't seen Wayland in a long time. Versions from 2 yrs ago didn't have features I needed. Just haven't bothered to keep up with it since X11 has been working well for me for a long time even with some of the crusty aspects.

---

### Post by rpessoa on 2020-05-14
I believed I solved my problem.

Wayland was enable by default on my Ubuntu 20.04

I disabled it and now, no more errors. Even the start of the login page is way faster.

How to disable it:

Find the below file:
```
/etc/gdm3/custom.conf
```

Uncomment:
```
WaylandEnable=false
```

That's it.

---

