---
title: "My solution to Gutsy upgrade problems"
date: 2007-11-07
forum: General Help
---

### Post by AdotB on 2007-11-07
My solution to Gutsy upgrade problems

I upgraded from Feisty to Gutsy about a week ago, but found a few minor problems. My main problem was that I could not compile source code. Always getting a “C compiler cannot create executables” error. After trying a few possible solutions I found on the web I decided to try a clean install. What the heck I like a clean environment every once in a while anyway.

That was a mistake. My computer would not boot without pushing Alt+F1 then Alt+F8 and lacked the  familiar bootsplash, and after I finally got my wireless working (with an atheros card) it would always drop the signal and take forever to reconnect, if it did at all.

Here's what I did:
I did a clean install of Feisty, on first boot I upgraded to Gutsy (after upgrading the update manager a couple times). It has been about two days now, and I have found no problems yet. Everything seems to be working fine: boot, wireless, I can compile source.  If I find any problems I'll post back.

Hope this helps someone with their upgrade woes.

---

### Post by taurus on 2007-11-07
You just need to install the build-essential package.

```
sudo apt-get update
sudo apt-get instal build-essential
```

---

### Post by AdotB on 2007-11-07
That didn't work for me. I already had it installed when i upgraded, then i tried reinstalling, purge removing and installing again, none of it worked. I tried a couple of other solutions i found on the web, but they didn't work for me either.  I eventually found some reference to libbfd-2.17.50.so and libbfd-2.18.so in various error messages but wasn't able to fix it.

---

