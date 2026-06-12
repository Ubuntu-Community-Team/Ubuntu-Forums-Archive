---
title: "please help, blue screen when booting!!"
date: 2007-04-11
forum: General Help
---

### Post by jputman01 on 2007-04-11
someone please help me, i must have mispelled something in my xorg.conf, i was trying to update my driver info for my touchpad, now when i boot the nvidia splash screen comes up and then just a blue screen, is there any way to edit it without booting X????

---

### Post by heimo on 2007-04-11
Sure. Hit ctrl+alt+F1 to go to virtual console. Then reconfigure or edit directly.

A) Reconfigure
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

B) edit directly
```
sudo nano /etc/X11/xorg.conf
```

Start gdm:
```
sudo /etc/init.d/gdm start
```

---

### Post by jputman01 on 2007-04-11
> **heimo said:**
> Sure. Hit ctrl+alt+F1 to go to virtual console. Then reconfigure or edit directly.

A) Reconfigure
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

B) edit directly
```
sudo nano /etc/X11/xorg.conf
```

Start gdm:
```
sudo /etc/init.d/gdm start
```


when do i hit ctrl+alt+F1? i cant boot into anything but a blue screen, do i hit it while its loading but before the blue screen? thanks for you help!

---

### Post by heimo on 2007-04-11
I'm not exactly sure what kind of blue screen you're getting. But I'd try after the "blue screen" shows up. If ctrl+alt+F1 doesn't work, hit ctrl+alt+backspace first. Or you could choose recovery mode in boot manager. I'm not sure if you'll have to press some button at the beginning of the boot to see this boot menu (with all those lines of "Ubuntu, kernel 2.6.20-9-386 (recovery)" and stuff. :)

---

### Post by jputman01 on 2007-04-11
> **heimo said:**
> I'm not exactly sure what kind of blue screen you're getting. But I'd try after the "blue screen" shows up. If ctrl+alt+F1 doesn't work, hit ctrl+alt+backspace first. Or you could choose recovery mode in boot manager. I'm not sure if you'll have to press some button at the beginning of the boot to see this boot menu (with all those lines of "Ubuntu, kernel 2.6.20-9-386 (recovery)" and stuff. :)


alright, ill try hitting it when the blue screen comes up. all that happens is i get my nvidia splash screen then a blue screen and then nothing happens, i never actually get into X

---

### Post by jputman01 on 2007-04-11
also can a use a text editor without booting into X? can i edit the file in a terminal?

---

### Post by heimo on 2007-04-11
> **jputman01 said:**
> also can a use a text editor without booting into X? can i edit the file in a terminal?

Yes. Go to recovery mode and use nano as your text editor.
[https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)

---

### Post by jputman01 on 2007-04-11
thanks for that link! i cant boot into recovery mode either, it hangs on the "loading hardware drivers" part, maybe because i messed up on one of the drivers in xorg?? but i did see a link on the page you gave me that explained how to use a live disc to mount my partition, maybe if i do that i can edit my xorg.conf file that way??? ill give it a try when i get home and report what happens, thanks again!

---

### Post by heimo on 2007-04-11
Is there some text on that blue screen? I can't think of anything else than Xorg not starting, then it'll show some errors on a text screen. But usually you can exit that by pressing enter couple times.

---

### Post by jputman01 on 2007-04-11
> **heimo said:**
> Is there some text on that blue screen? I can't think of anything else than Xorg not starting, then it'll show some errors on a text screen. But usually you can exit that by pressing enter couple times.


i just tried again, all i am getting is a blank blue screen, I let it sit for a couple minutes this past time and nothing ever happened. then i hit ctrl+alt+F1 and the screen went black and never loaded a terminal, just a black screen, i let that sit for a few minutes and then did a hard shutdown.

---

### Post by jputman01 on 2007-04-11
i fixed it, thanks for your help, that link helped me a lot. i ended up booting the live cd, mounting sda3, and editing the xorg file from there. thanks again!

---

