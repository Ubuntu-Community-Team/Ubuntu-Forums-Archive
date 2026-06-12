---
title: "MediaInfo: Version `GLIBCXX_3.4.20' not found!"
date: 2015-01-25
forum: General Help
---

### Post by Ashfaqur Rahman on 2015-01-25
I have installed Mediainfo 0.7.72 on Ubuntu 14.04 64 Bit. But when I run MediaInfo I get following error -

 
[I]mediainfo-gui: /usr/lib/x86_64-linux-gnu/libstdc++.so.6: version GLIBCXX_3.4.20' not found (required by /usr/lib/libmediainfo.so.0)
mediainfo-gui: /usr/lib/x86_64-linux-gnu/libstdc++.so.6: versionGLIBCXX_3.4.20' not found (required by /usr/lib/libzen.so.0)
[/I]

What can I do?

 Thanks!

MediaInfo: [https://mediaarea.net/en/MediaInfo](https://mediaarea.net/en/MediaInfo)

---

### Post by mc4man on 2015-01-25
I'm not sure what you installed but probably better you use a package built for 14.04

---

### Post by Ashfaqur Rahman on 2015-01-27
What do you mean by "Package Built"? Are you suggesting to compile from source?

---

### Post by mc4man on 2015-01-27
> **Ashfaqur Rahman said:**
> What do you mean by "Package Built"? Are you suggesting to compile from source?
I mean a package (.deb) that has been built for 14.04
You linked to the mediainfo page & said you installed 0.7.72 by some unmentioned, by you, means. I'm not inclined to guess what that was.

---

### Post by Ashfaqur Rahman on 2015-01-27
I have found that libstdc++.so.6 is actually a symbolic link to  libstdc++.so.6.0.19 . I thought may be libstdc++.so.6.0.20 would solve  my problem as the required version is GLIBCXX_3.4.20 . So I searched a  little to know which version of GCC contains libstdc++.so.6.0.20 . Found this [document]("https://gcc.gnu.org/onlinedocs/libstdc++/manual/abi.html") which is indicating GCC 4.9.0 contains it. So I add this [ppa]("https://launchpad.net/~ubuntu-toolchain-r/+archive/ubuntu/test") and install GCC 4.9.0 which solved my problem.

Thanks by the way.

---

