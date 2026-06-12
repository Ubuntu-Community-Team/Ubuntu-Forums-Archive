---
title: "Firefox 2 installation over 1.5 in Ubuntu."
date: 2006-12-30
forum: General Help
---

### Post by chrispche on 2006-12-30
I downloaded Firefox 2 and want to know how I install it over the top of the pre-installed 1.5. I can run version 2 from the extracted directory, but I want it on the menubar in place of 1.5. How do I go about doing this?

Thanks.

---

### Post by tommcd on 2006-12-30
I'm not sure how to get FF 2.0 in the menubar, but here is a guide to getting all your FF plugins to work in your new FF 2.0:
[http://ubuntuforums.org/showthread.php?t=325565&highlight=firefox+2.0](http://ubuntuforums.org/showthread.php?t=325565&highlight=firefox+2.0)

---

### Post by chrispche on 2006-12-30
So it's best to wait for it to appear on the repos under synaptic?

---

### Post by tommcd on 2007-01-02
Well, I don't know if or when FF 2.0 will be in the repos in Dapper. If it's not there yet (it has been out for a while) I don't know if it will ever be. The how-to I linked to will not mess up your system in any way since you are not actually installing FF 2.0, you are just running it from your home folder. If you want FF 2.0 in your menu list I suppose you could just right-click on the applications menu and choose edit menus. You may be able to add FF 2.0 from there.

---

### Post by zanglang on 2007-01-02
Try this: Get the tar.gz from Mozilla's download page, and then unpack it at /opt so it becomes /opt/firefox or similar. Now do:
```
sudo nano /usr/bin/firefox
```
and look for the line
```
MOZ_DIST_BIN="/usr/lib/firefox"
```
and replace the /usr/lib/firefox part with "/opt/firefox". Save and close.

Now click on the old firefox launcher as usual and see if it works.

---

