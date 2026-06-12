---
title: "apt-fast and axel..."
date: 2013-10-30
forum: General Help
---

### Post by maxfarrar on 2013-10-30
I've installed apt-fast to get parallel connections with apt-get, but I've read that axel is no longer supported and aria2c is the only available option. However, axel supported single-file split downloads, and that is what I'm trying to do (when I use apt-fast right now, the downloads aren't sped up since it's not splitting single files).

I read that there is a custom command to still use Axel but the one I found didn't work. (cat "${DLLIST}" | xargs -l1 axel -n "${_MAXNUM}" -a)

Does anyone know how to get Axel working again?

Or, does anyone know how to get aria2c splitting single files? In the manual it says it can split using -s, but I can't get it working either.

---

### Post by maxfarrar on 2013-10-31
nobody?

---

