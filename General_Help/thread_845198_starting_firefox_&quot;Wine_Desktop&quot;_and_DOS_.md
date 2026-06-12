---
title: "starting firefox: &quot;Wine Desktop&quot; and DOS problems??"
date: 2008-06-30
forum: General Help
---

### Post by pixelstuff on 2008-06-30
edit: This is about the Linux version of Firefox!

hello all,
I got my firefox together with a recent fresh install of Ubuntu Studio. The weird thing is that when Firefox starts the wine "Virtual Desktop" flashes up and then the firefox window opens. After that, the "Virtual Desktop" is gone again. When I start firefox from a terminal I get exactly the same funny DOS errors that I get when running something on wine:
```
klaudia@compi:~$ firefox
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
klaudia@compi:~$ firefox
preloader: Warning: failed to reserve range 00000000-60000000
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report
preloader: Warning: failed to reserve range 00000000-60000000
err:dosmem:setup_dos_mem Cannot use first megabyte for DOS address space, please report

```
:confused: whats going on? Firefox does not crash more often than with previous versions and everything seems to work but I'd really like to know what that funny behavior is about :o

---

### Post by DJ_Peng on 2008-06-30
Why are you running Firefox with WINE? There are native Linux versions of Firefox and they come in Ubuntu by default (Hopefully even Ubuntu Studio) so I'm not sure why you're getting a WINE Virtual Desktop at all.

---

### Post by pixelstuff on 2008-06-30
I'll try to make it even clearer in the title, hope I can edit that: I did not install/download a Windows Version, it is the Linux Version behaving like this.

---

### Post by DJ_Peng on 2008-06-30
I'm still at a loss for why WINE is getting started as Firefox is launched. I've never had that happen, even when checking out the Firefox included with Ubuntu.

---

### Post by nikgare on 2008-06-30
What happens when you run this command:

/usr/bin/firefox

---

### Post by pixelstuff on 2008-06-30
nikgare: The same things happen when I start from usr/bin/firefox :o
DJ_Peng: This is why I came to ask, because it is pretty weird :D

---

### Post by nikgare on 2008-06-30
In the Applications menu in the wine sub catagory is Firefox listed?
Maybe you should remove --purge firefox, check that /usr/bin/firefox is really gone and then reinstall.
If you select firefox from the application->internet menu, does the same thing happen?
What's your Ubuntu version, and which firefox are we talking about, 2 or 3?

---

### Post by pixelstuff on 2008-06-30
> **nikgare said:**
> In the Applications menu in the wine sub catagory is Firefox listed?
Maybe you should remove --purge firefox, check that /usr/bin/firefox is really gone and then reinstall.
If you select firefox from the application->internet menu, does the same thing happen?
What's your Ubuntu version, and which firefox are we talking about, 2 or 3?

From the application menu it does the same thing and its Ubuntustudio 2.6.24-19-rt and Firefox 3
This time, unlike with the normal hardy before, I have no wine entry in the menu, also no invisible ones in the edit menu mode.
I tried to remove firefox and all bin things were gone but I did not remove my personal settings of course, but nothing has changed.

---

### Post by nikgare on 2008-06-30
Does this happen just for your account, or for all users?
Is this firefox 3 from the repos, or have you downloaded it yourself?

---

### Post by pixelstuff on 2008-07-02
> **nikgare said:**
> Does this happen just for your account, or for all users?
Is this firefox 3 from the repos, or have you downloaded it yourself?

now thats a surprise! i made another user and from there no wine-behaviour! 
and now? :o i tried reinstalling it before? It is the repos firefox btw.

---

### Post by nikgare on 2008-07-02
Download directly from mozilla.com and see if that will run.

---

### Post by DJ_Peng on 2008-07-02
> **pixelstuff said:**
> now thats a surprise! i made another user and from there no wine-behaviour! 
and now? :o i tried reinstalling it before? It is the repos firefox btw.
It sounds like you might have some corruption in your profile. Have you tried starting in [safe mode]("http://kb.mozillazine.org/Safe_Mode")?

---

### Post by pixelstuff on 2008-07-04
:) Now I am almost there... Following the suggestion at the link about safe-mode I created a new Firefox-profile ```
:~$ firefox -profilemanager

```and there are no problems in it - now I have to transfer some data from the old profile. But it is worth it - much quicker startup without that glass of wine at the beginning :lolflag:

---

