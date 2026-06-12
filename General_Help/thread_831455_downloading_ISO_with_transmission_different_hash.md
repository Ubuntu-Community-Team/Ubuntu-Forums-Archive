---
title: "downloading ISO with transmission: different hash?"
date: 2008-06-16
forum: General Help
---

### Post by kstella on 2008-06-16
I can't seem to get a xubuntu ISO with the right hash (alternate for Intel desktop). I've lost count of my attempts to download it - I've tried with two different download managers and now with the Transmission client in Hardy. I've been trying for days now.

When I click on 'Details' in Transmission, I see that the file it's downloading already has a hash that looks nothing like the correct one. Is that normal? If not, why can't I seem to get a good CD image?

I need to install it in an older computer by the end of the week so that we can donate it to a less fortunate school in the community. It's really frustrating to wait so long for that huge file, only for it to be defective. :(

---

### Post by avtolle on 2008-06-16
If possible, choose a different mirror for the next attempt.

---

### Post by plucky on 2008-06-17
> When I click on 'Details' in Transmission, I see that the file it's downloading already has a hash that looks nothing like the correct one. Is that normal? If not, why can't I seem to get a good CD image?


I just tried this with a known good iso on my system and the hash was different.Open a terminal and ```
cd <path to iso>
md5sum <name of iso>
``` and see what you get.Compare it to the one in the file on the mirror you downloaded from.The chances are it is correct.


Good Luck

---

### Post by hyper_ch on 2008-06-17
Did you download the torrent file from here? [http://torrent.ubuntu.com:6969/](http://torrent.ubuntu.com:6969/)

If you download it from there then once it's downloaded and hash checked it should all be fine.

---

### Post by geirha on 2008-06-17
> **kstella said:**
> 
When I click on 'Details' in Transmission, I see that the file it's downloading already has a hash that looks nothing like the correct one. Is that normal? If not, why can't I seem to get a good CD image?


Yes, the hash you see in transmission is a completely different one than the md5sum of the downloaded file. When the file is downloaded, run md5sum on it in a terminal.

EDIT:
Something like this should tell you if your image is good.
```
cd Desktop # or wherever you've downloaded the iso to
wget -q -O- http://cdimages.ubuntu.com/xubuntu/releases/hardy/release/MD5SUMS | md5sum -c

```

It will check the hash of all four xubuntu-isos, so you should get a failure on the three you didn't download, and an OK on the one you did.

---

### Post by kstella on 2008-06-19
> **geirha said:**
> Yes, the hash you see in transmission is a completely different one than the md5sum of the downloaded file. When the file is downloaded, run md5sum on it in a terminal.

Thank you! :) And to everyone else, too - thanks! That cleared it up for me.

---

