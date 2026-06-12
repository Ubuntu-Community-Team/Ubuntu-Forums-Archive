---
title: "How to Upgrade from 19.04 to either 19.10 or 20.04"
date: 2020-07-22
forum: General Help
---

### Post by jgwphd on 2020-07-22
I am at Ubuntu 19.04. I am having a great deal of difficulty finding the terminal command(s) with the proper repository pointers to allow me to upgrade my system from 19.04 to 19.10 or directly to 20.04 (I believe you can't go to 20.04 directly). The installer tool tells me Disco release no longer has a release file. Trying other commands such as sudo apt-get upgrade -y give a bunch of failed to fetch messages. su-do-release -d or -c gives error messages. 

Can someone help me with a pointer to the commands needed or please just type them into this message.

Many Thanks!

---

### Post by ActionParsnip on 2020-07-22
Ubuntu 19.10 no longer exists so you'll need to boot to the CD/USB installer of the OS and do the upgrade that way. You can then upgrade to 20.04 online as you expect.

Be sure to run a full backup of any important data before starting.

Personally I suggest you run the full backup then wipe the install off and do a clean install of 20.04. You'll have fewer issues and you can restore your user data from your backups

---

### Post by Impavidus on 2020-07-22
There is a not-officially-supported way to upgrade from 19.04 to 20.04 (via 19.10): [https://help.ubuntu.com/community/EOLUpgrades](https://help.ubuntu.com/community/EOLUpgrades)
19.10 is dead too, but the repositories may still be available as it reached end of life only 6 days ago, so that may be slightly easier.

You can also try a direct upgrade by simply changing the software sources from disco to focal, but that's even more likely to fail, so only try that if you're ready to do a fresh install after all. Most likely, you'll need it.

In fact, I suggest you try that fresh install right away.

---

### Post by jgwphd on 2020-07-22
Ok, I missed the window by 6 days   :-(     Ok, I'll do the backup and fresh install. Many thanks for the information! You guys at the Ubuntu forum are "awesome"!

---

### Post by Impavidus on 2020-07-23
You missed the window to use 19.10 by six days, you missed the window to upgrade from 19.04 to 19.10 by six months. But I would always prefer a fresh install over a double release upgrade, even if all releases concerned are still supported.

---

### Post by CatKiller on 2020-07-23
Bear in mind that you don't seem to be the kind of user that updates frequently, so the interim releases aren't a good fit for how you use your computer. If you'd chosen 18.04, or even 16.04 - rather than 19.04 - your OS would still be supported and getting security updates, since 16.04 and 18.04 are Long-Term Support releases. 20.04 is also an LTS release, so don't switch from it in a few months and then forget to upgrade again.

---

### Post by rsteinmetz70112 on 2020-07-23
You can with some effort upgrade using the Old Releases Repositories. [http://old-releases.ubuntu.com/releases/](http://old-releases.ubuntu.com/releases/)

---

