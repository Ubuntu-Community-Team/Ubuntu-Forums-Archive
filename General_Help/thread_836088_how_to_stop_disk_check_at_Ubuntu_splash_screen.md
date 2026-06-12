---
title: "how to stop disk check at Ubuntu splash screen"
date: 2008-06-21
forum: General Help
---

### Post by Tucatts on 2008-06-21
Good morning all,
Well, I installed KDE desktop but didn't like it and uninstalled it with no real problems. However, it has left a "disk check" program that wants to run when the Ubuntu screen come up. I have to click esc to stop it and it's a bit of a bother to say the least. Is there anyway to stop this from starting in the first place? Hardy seems to be real stable, I have played around a lot and installed and removed many many programs to try stuff out and it really ain't broke yet. lol. AND my scanner works! Anyway thanks for the help.

---

### Post by Nikitas350 on 2008-06-21
Run this command in terminal:
sudo tune2fs -c 0 /dev/sdax
(/dev/sdax is your hard disk)

---

### Post by Tucatts on 2008-06-21
OK, I have set it to my HD as you indicated and then I see this in terminal " setting maximal mount count to - 1" Am I to change the count perhaps? When I rebooted I still had the disk check running again. Anyway, thanks for the help!

---

### Post by nvteighen on 2008-06-21
> **Nikitas350 said:**
> Run this command in terminal:
sudo tune2fs -c 0 /dev/sdax
(/dev/sdax is your hard disk)
That will change when disk checking is performed by fsck at boot... Absolutely unsecure. Run that command again but replace 0 by 31 (which is the default), so fsck checks your filesystem each 31th mount.

If there's a KDE application left, you could do:
```

sudo apt-get autoremove

```

That will let you remove any non-needed automatically installed package.

---

### Post by sdennie on 2008-06-21
I agree with nvteighen in that it's not a good idea to disable disk checking.  I don't think it's KDE that is causing your disk check but instead just the fact that you've rebooted your machine 30 times.  If you let the disk checks run to completion, it won't pester you again for 30 more reboots.

---

### Post by drs305 on 2008-06-21
There is a program called autofsck which provides a gui-based method of setting the time between disk checks. 

Although I am a CLI supporter and like tune2fs, autofsck also allows you to set whether you want it to check your system at startup or shutdown. Since I prefer the checks to run after I'm through with the computer, I find this option appealing.

Install it with:
```
sudo aptitude install autofsck
```

In the menus, it's located in System, Admin, Periodic Disk Checking.

For more information:
[URL="https://wiki.ubuntu.com/AutoFsck/Doc"]https://wiki.ubuntu.com/AutoFsck/Doc
[/URL]

---

### Post by Tucatts on 2008-06-21
Thank you everyone! Problem solved! It seems I also had a bad file that was causing some additional problems but after running the suggested command and then letting it go through disk check I was able to repair the bad file and now it's fine. So thanks again and I hope everyone has a great weekend. My wife has me painting the spare bedroom today so I have been working on this between coats of paint, lol.

---

### Post by nvteighen on 2008-06-21
***EDIT* Ignore this post... You've already solved this. Glad to hear it worked!**

Tucatts: A question, that disk checker runs after you login or before?? 

If it's before logging in, we're talking about fsck, and you are highly recommended to let it there. It not only checks but also repairs disk damage if something bad occurs.

But, if it's after logging in, how is that program called? I have never heard of a disk checker working in KDE or any desktop environment before, but I don't know everything :)!

---

