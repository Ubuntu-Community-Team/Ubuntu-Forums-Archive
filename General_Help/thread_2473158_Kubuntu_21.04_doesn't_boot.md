---
title: "Kubuntu 21.04 doesn't boot"
date: 2022-03-25
forum: General Help
---

### Post by allen2 on 2022-03-25
Edit: running recovery console dpkg to fix broken packages seemed to fix the problem for now.  Not sure what went wrong or what it fixed (had listed a lot of packages that it was going to re-do).

---

### Post by Impavidus on 2022-03-26
Keep in mind that Kubuntu 21.04 (like all flavours of that release) reached end of life last January. Consider moving to a supported release as soon as you can.

---

### Post by guiverc on 2022-03-26
> As of January 20, 2022, Ubuntu 21.04 is no longer supported. No more  package updates will be accepted to 21.04, and it will be archived to  old-releases.ubuntu.com in the coming weeks. 

[https://fridge.ubuntu.com/2022/01/21/ubuntu-21-04-hirsute-hippo-end-of-life-reached-on-january-20-2022/](https://fridge.ubuntu.com/2022/01/21/ubuntu-21-04-hirsute-hippo-end-of-life-reached-on-january-20-2022/)


I'd likely
- boot *live* media,
- check out your data is there,
- then back it up, or more likely ensure you have it all backed up correctly.

Then I'd install a *supported* release of Kubuntu 21.10 over your existing install (*without format*).

This type of install (*triggered by the lack of format*) will
- note your *manually installed packages*,
- erase system directories, install the new system,
- re-install (*where available in Ubuntu repositories for your new release*) the *manually installed* packages noted earlier IF internet is available during install
- but won't touch user files/data (*unless saved in system directories*), which you confirm when you reboot on being asked.

When 21.04 reached EOL, and I had no reason to keep the 21.04/*hirsute* system I kept for support purposes, I used this type of install to *move* it to *jammy* (*or what will be 22.04 on release*), as I had no need for a *impish* or 21.10 install (*my 20.10 install became 21.10 on 20.10 reaching EOL months earlier using this method of upgrade*). This install does not touching any user file (eg. my music), and my additional apps get re-installed (*eg. my music playlists continued in my chosen non-standard music player post-install*).  My altered settings also survive re-install.

There are additional complications to consider if you're using 3rd party software; but you've provided no details...  But I'd re-install in your case.

---

