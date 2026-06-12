---
title: "VLC plugin?"
date: 2016-02-27
forum: General Help
---

### Post by Evil Wayz on 2016-02-27
I installed the vlc browser plugin, but it doesn't appear within Chromes plugin page.  Does Chrome no longer support the vlc plugin?

---

### Post by sandyd on 2016-02-27
I'm guessing that the VLC plugin uses NPAPI, and since [chrome no longer allows NPAPI plugins]("https://support.google.com/chrome/answer/6213033?hl=en"), it no longer works.

See [https://trac.videolan.org/vlc/ticket/14484](https://trac.videolan.org/vlc/ticket/14484)

---

### Post by bizhat on 2016-02-28
Chome, when it was supporting, it was so buggy, it cashed all the time for me. I have a media library software, that use browser plugin to play media, i use Firefox for it and works well.

---

### Post by Evil Wayz on 2016-03-01
> **bizhat said:**
> I have a media library software, that use browser plugin to play media, i use Firefox for it and works well.

Which one?

---

### Post by bizhat on 2016-03-01
It is coded by me. You can see source code at 

[https://github.com/HostOnNet/medialib](https://github.com/HostOnNet/medialib)

It use VLC to play video

[https://github.com/HostOnNet/medialib/blob/master/app/views/watch/show.blade.php#L27](https://github.com/HostOnNet/medialib/blob/master/app/views/watch/show.blade.php#L27)

---

### Post by Evil Wayz on 2016-03-01
Oh ok it only works on servers.  I suck at compling things but thanks anyways.

---

### Post by bizhat on 2016-03-01
> **Evil Wayz said:**
> Oh ok it only works on servers.  I suck at compling things but thanks anyways.

It work on my local PC, you need apache/mysql installed for it. Media is accessed from local folder with file://

It can be installed on remote server if required.

---

