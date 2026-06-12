---
title: "Ubuntu 16.04 fstab parse error after Distribution Update (distro update)"
date: 2018-02-19
forum: General Help
---

### Post by koprov on 2018-02-19
Hello,

Fellow linux users I need your help! :(

Some background:
I have made a distro update on my laptop from 14.10 to 16.04 after which I was greeted with command prompt instead of GUI. This happened before and is due to nvidia drivers. I tired to change/update the drivers but I stumbled upon an issue that some files were made as read-only...

I tried poking around on the internet and in desperation I tired going into root to remount the drive with rw permissions.

I got this message:
[https://preview.ibb.co/myYPGS/IMG_20180219_174831_HDR.jpg](https://preview.ibb.co/myYPGS/IMG_20180219_174831_HDR.jpg)



It looks like there's something wrong with the fstab, but this is beyond my abilities...

Please help!

---

### Post by Impavidus on 2018-02-19
14.10 reached end of support 2.5 years ago and you had to skip 2 other dead releases to get to 16.04. Although I'm generally happy to try release upgrades, I wouldn't have tried this one.

That aside, what's in your /etc/fstab? And did your root file system get remounted? The error only says line 9 was ignored.

---

### Post by koprov on 2018-02-20
The /etc/fstab looks like this:
[https://preview.ibb.co/ddfC5x/IMG_20180220_183600_HDR.jpg](https://preview.ibb.co/ddfC5x/IMG_20180220_183600_HDR.jpg)

But as I said, this is beyond me...

As for root access yes, as far as I could tell the file system got remounted but without networking I couldn't do much... (and simply starting network-manager does nothing :/ )

---

### Post by Impavidus on 2018-02-20
In the 9th line you see between **nodiratime** and **errors** a couple of spaces or a tab. Replace those by a comma so that it reads```
discard,noatime,nodiratime,errors=remount-ro
```

In the recovery mode menu, just above drop to a root shell, is an option to enable networking. I think it will also remount your file system read-write. Try that, then drop to a root shell and you should be able to install or remove packages.

---

### Post by DuckHook on 2018-02-20
Please don't post large graphics to the forums. This is very problematic for helpers with low speeds, who are on limited data plans, or are viewing from smartphones or small screens. It is also unnecessary to post whole screenshots in most cases. Terminal output can be highlighted with the mouse, copied with a right click and pasted into the posting box between [noparse]```
 and 
```[/noparse] tags for clarity. Or highlight the output and use the [img]http://ubuntuforums.org/images/editor/code.gif[/img] button in the *Adv Reply* toolbar.

If you must post resource-intensive images, please post them as attachments using the paperclip icon in the *Adv Reply* toolbar.

---

### Post by koprov on 2018-02-21
@Impavidus - **You are the best!** Editing fstab as you advised fixed everything! (drivers etc.) :) Thank you so much!

@DuckHook - Right, noted! I shall do that from now on.

---

