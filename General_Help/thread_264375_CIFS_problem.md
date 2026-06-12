---
title: "CIFS problem"
date: 2006-09-24
forum: General Help
---

### Post by fafek2 on 2006-09-24
Hi!

I want to mount a Samba's share (Samba's running on Ubuntu 6.06) on my computer.

I tried mount using smbfs. Any combination of iocharset and codepage didn't work (wrong characters). However, I could mount it using a hostname.

So I tried to mount using CIFS. Great! Diacritical signs works, but I have to use IP address instead of hostname to make this working (mount returns an error: "Share could not be found. TCP name myhost not found"

My router sometimes assigns various IP adresses so using IP address doesn't work always.

How can I use a hostname to mount a Samba share using CIFS?

---

