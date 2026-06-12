---
title: "YouTube videos"
date: 2012-12-15
forum: General Help
---

### Post by anon_private on 2012-12-15
Hi,

I  was using the LiveCD on YouTube the other day.

When I clicked on a video, I only got a black screen where the video should play. I did not get any message regarding the absence of Flash.

Can anyone advise?

Thanks

---

### Post by zombifier25 on 2012-12-15
The LiveCD does not have Flash installed, because of legal reasons. But weird, since if there are no Flash, the HTML5 version should show up. Try going to [this link](https://www.youtube.com/html5) and choose "join the the HTML5 trial"

---

### Post by Cheesemill on 2012-12-15
You can always install flash on the Live CD.
```
sudo apt-get update && sudo apt-get install flashplugin-installer
```

---

### Post by anon_private on 2012-12-15
> **zombifier25 said:**
> The LiveCD does not have Flash installed, because of legal reasons. But weird, since if there are no Flash, the HTML5 version should show up. Try going to [this link](https://www.youtube.com/html5) and choose "join the the HTML5 trial"

I have joined. It did not require a email address. How have I joined?

Best wishes.

A

Ps. I have just been to Youtube and still cannot see the videos?

> **Cheesemill said:**
> You can always install flash on the Live CD.
```
sudo apt-get update && sudo apt-get install flashplugin-installer
```

I assume that you mean install to a pendrive. I don't think I can write to a LiveCD

---

### Post by 2F4U on 2012-12-15
You can install software in a liveCD, but it will only last until the session ends.

---

### Post by rajhanschinmay on 2012-12-16
I suggest u to create an USB bootable pen drive from ur Ubuntu .iso image.
There is option called USB disk creator.

If you do that and if u install flash plugin like the way told earlier, then the package gets stored in ur pen drive, so u don't have to install package every time.

Plus ur pen drive is more reliable than CD, because CD can get back sectors after some time. If pen drive does than, u can format it and create it again.

Hope this helps.

---

### Post by anon_private on 2012-12-16
> **2F4U said:**
> You can install software in a liveCD, but it will only last until the session ends.

Thanks for responding.

As a matter of interest what type of cd are the LiveCD's. If information can be stored are they CD-RW, but information is only stored for a session!

> **rajhanschinmay said:**
> I suggest u to create an USB bootable pen drive from ur Ubuntu .iso image.
There is option called USB disk creator.

If you do that and if u install flash plugin like the way told earlier, then the package gets stored in ur pen drive, so u don't have to install package every time.

Plus ur pen drive is more reliable than CD, because CD can get back sectors after some time. If pen drive does than, u can format it and create it again.

Hope this helps.


Thanks for responding. I am a little confused regarding bad sectors and the LiveCD. I did not think that LiveCD's could be written, but only read.

---

### Post by Cheesemill on 2012-12-16
No writing at all takes place when you use a Live CD. Instead the OS and any temporary files you create or software you install are all stored in the computers RAM. This way you can install whatever software you want (like flash) and create and edit documents but all changes are lost when you reboot.

Regarding your YouTube HTML5 query I believe that when you 'sign up' all that happens is a cookie is created in your browsers cache that instructs YouTube to use HTML5 video where available (not all videos have been transcoded to HTML5). Again this will only last until you reboot the machine as the browser cache is stored in RAM.

---

### Post by anon_private on 2012-12-16
> **Cheesemill said:**
> No writing at all takes place when you use a Live CD. Instead the OS and any temporary files you create or software you install are all stored in the computers RAM. This way you can install whatever software you want (like flash) and create and edit documents but all changes are lost when you reboot.

Regarding your YouTube HTML5 query I believe that when you 'sign up' all that happens is a cookie is created in your browsers cache that instructs YouTube to use HTML5 video where available (not all videos have been transcoded to HTML5). Again this will only last until you reboot the machine as the browser cache is stored in RAM.


Thank you.

Your explanations are entirely consistent with my understanding

Best wishes.

A

---

