---
title: "Booting into an initramfs prompt"
date: 2015-09-30
forum: General Help
---

### Post by pcvonz on 2015-09-30
I have a strange issue,

When I first installed Kubuntu on this computer, it was actually along side another hard drive with an older version of Kubuntu on it. Launching the new Kubuntu wouldn't work, instead it would display the old Kubuntu logo and hang there forever. My workaround at this point was to go into my current Linux's recovery mode and then continue booting from there. I got tired of this though and decided to try and fix it. I was told to try: 

```

update-initramfs -u -k all
update-grub

```

I tried that and I noticed that it was still showing the older version of Kubuntu. So, I deleted all the folders in my old Kubuntu except the home folder (I need that). I then repeated the above commands. This seemed to solve the issue of the strange old kubuntu logo showing up when I try booting into newer Kubuntu, but now it hangs on a black screen. If I select recovery mode it'll drop me into a busy box prompt and display:


```
 (initramfs) 
```


from here I can ctrl+d and then remount the drive as writeable then startx. This is kind of a lot of work to start my machine and I'd really like if I could just boot normally again. ](*,)

---

