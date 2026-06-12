---
title: "Looking for a black widow..."
date: 2006-11-13
forum: General Help
---

### Post by TheeMahn2003 on 2006-11-13
I am looking for a program similar to that of windows counterpart of Black Widow which mirrors a copy of a website to your hard disk.  Does such a program exist for Ubuntu?  I am not talking rsync I don't own the website and I'm not wanting to mirror Microsoft :)  I have searched google and cannot find a posting of such a program without digging through 1+ million results none of which of what I seen mean squat to what I'm looking for.  Thanks in advance.

---

### Post by aysiu on 2006-11-13
I don't see how this is Feisty-related, so I'm moving it to General Help.

The program you're looking for is *wget*:

```
wget -r http://www.nameofsite.com
```

---

### Post by yabbadabbadont on 2006-11-13
> **aysiu said:**
> I don't see how this is Feisty-related, so I'm moving it to General Help.

The program you're looking for is *wget*:

```
wget -r http://www.nameofsite.com
```
Wouldn't "wget --mirror http://www....." work better?

---

### Post by aysiu on 2006-11-13
> **yabbadabbadont said:**
> Wouldn't "wget --mirror http://www....." work better?
Good point. I didn't know about that.

---

### Post by TheeMahn2003 on 2006-11-13
> **yabbadabbadont said:**
> Wouldn't "wget --mirror http://www....." work better?

Thanks and apologize for where it was posted the --mirror did the trick, thanks

---

### Post by TheeMahn2003 on 2006-11-13
Well I thought it did the trick it is downloading all the webpages and faster then I can read it, but not grabbing the rest is there a switch that will tell it to grab all?  Getting quite a few 404's as well I can understand why wget does not use friendly etiquette it is beating the website to death :)  Perhaps a run through man wget.  Thanks again for the point in the right direction.

---

### Post by cevans on 2006-11-13
man wget is woefully inadequate (and doesn't include what you are looking for, even though it exists), since the main documentation for wget is in texinfo format. So you will want to look at "info wget" instead.

---

### Post by yabbadabbadont on 2006-11-13
Try adding '-p'.  (page requisites)  Also, some websites don't mirror well with wget since they require the referring URL to be a specific value before they will let you view the next page.

(I've got over 50,000 wallpapers, so I've had a lot of practice using wget, curl, and whatnot ;))

---

### Post by roadboy on 2006-11-14
apt-get install httrack

---

### Post by yabbadabbadont on 2006-11-15
> **roadboy said:**
> apt-get install httrack

That looks very good.  Thank you for the information.

---

