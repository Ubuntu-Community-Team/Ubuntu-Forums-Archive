---
title: "Help with rsync."
date: 2007-01-02
forum: General Help
---

### Post by solarwind on 2007-01-02
Hi all. I've been trying to download the Kubuntu 6.10 Edgy release for my new AMD Dual core 64 bit system. I've tried downloading it **three** times and each time yielded a different md5 sum. I'm sick of re downloading it. Can someone please tell me an rsync mirror of the Kubuntu 6.10 ISOs? I would really appreciate it!

---

### Post by solarwind on 2007-01-02
.

---

### Post by solarwind on 2007-01-02
.

---

### Post by koenn on 2007-01-02
--- forum policy violation starts here ----
Ever heard of Google ?  It takes 0.18 seconds for Google to return  632,000 search results for the keywords rsync + mirror + kubuntu ; I'm sure at least 1 of the top 10 results have what you need , and a whole lot faster than waiting 20 minutes, bump youur post, wait some  more, and so on, until someone else types in those 3 words for you and tells you the result.
---forum policy violation ends here -----

Have a look at [https://wiki.ubuntu.com/Archive](https://wiki.ubuntu.com/Archive) (and look for URL's that start with rsync://  :)  )

---

### Post by solarwind on 2007-01-02
Nevermind. Figured it out...

```
rsync -Lvv --progress rsync://releases.ubuntu.com/releases/kubuntu/6.10/kubuntu-6.10-desktop-amd64.iso kubuntu-6.10-desktop-amd64.iso
```

I used cwRsync to do the job from Windows.
[http://www.itefix.no/phpws/index.php?module=pagemaster&PAGE_user_op=view_page&PAGE_id=6&MMN_position=23:23](http://www.itefix.no/phpws/index.php?module=pagemaster&PAGE_user_op=view_page&PAGE_id=6&MMN_position=23:23)

That fixed the corrupted download instantly.

---

### Post by solarwind on 2007-01-02
> **koenn said:**
> --- forum policy violation starts here ----
Ever heard of Google ?  It takes 0.18 seconds for Google to return  632,000 search results for the keywords rsync + mirror + kubuntu ; I'm sure at least 1 of the top 10 results have what you need , and a whole lot faster than waiting 20 minutes, bump youur post, wait some  more, and so on, until someone else types in those 3 words for you and tells you the result.
---forum policy violation ends here -----

Have a look at [https://wiki.ubuntu.com/Archive](https://wiki.ubuntu.com/Archive) (and look for URL's that start with rsync://  :)  )

Thanks for being a backseat mod. I'm sure everyone appreciates it.

---

