---
title: "installing ubuntu question"
date: 2007-10-28
forum: General Help
---

### Post by yf1208 on 2007-10-28
My Ubuntu is corrupted,is there any way to do a fix installation like Windows XP without deleting/formating the files within?

---

### Post by mojoman on 2007-10-28
> **yf1208 said:**
> My Ubuntu is corrupted,is there any way to do a fix installation like Windows XP without deleting/formating the files within?

well, there are several options with apt-get that might help you but you have to be a little more specific on what problems you have. But the option fix-broken or remove (with purge option ) and then install them again might do some good (depending on what the problem is).

---

### Post by yf1208 on 2007-10-28
the problem is,i can't even boot into the desktop part

The login screen,is as far as i could go

---

### Post by hikaricore on 2007-10-28
If you can get to the login screen I doubt anything is "corrupted".

You should still be able to reach text based tty terminals with:  Ctrl + Alt + F1 (1-6)

Perhaps you should give us more info on what you were messing with before this occured?
It sounds like a simple issue /w loading gnome to me.  Or possibly a video driver problem.

---

### Post by yf1208 on 2007-10-28
> **hikaricore said:**
> If you can get to the login screen I doubt anything is "corrupted".

You should still be able to reach text based tty terminals with:  Ctrl + Alt + F1 (1-6)

Perhaps you should give us more info on what you were messing with before this occured?
It sounds like a simple issue /w loading gnome to me.  Or possibly a video driver problem.


yes,i could get into the text based terminal

i could log in too,but it just stuck on the "loading desktop" splash screen part,refer to the image i attached.Usually,a couple of small icons will emerge on it and proceed to boot into the desktop.

Before all these happened,i did some updating,just typical system updates that pops up once and a while,and ask you to download it.
I was watching a movie that time too,but halfway through it,whole computer froze,i restarted and ran into this problem

---

### Post by hikaricore on 2007-10-28
Since you're able to get to the text terminal, you should try the following:

> sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get update
sudo apt-get upgrade

This way if you have anything have install or broke it "should" resolve the problem.

Watch for any packages being removed or anything of the like incase you need to reinstall anything.

---

### Post by yf1208 on 2007-10-28
when i type sudo dpkg --configure -a

i get this error 

> dpkg: parse error,in file '/var/lib/dpkg/available' near line 1:
Field name '-0' must be followed by colon

as for sudo apt-get upgrade 
i managed to download some files,then ran into the same error as above

---

### Post by yf1208 on 2007-10-29
bump

---

### Post by yf1208 on 2007-10-29
bump

---

