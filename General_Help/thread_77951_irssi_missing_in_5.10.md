---
title: "irssi missing in 5.10?"
date: 2005-10-17
forum: General Help
---

### Post by shubjero on 2005-10-17
Hey guys, loving the Breezy Badger so far.

I used irssi on 5.04 and loved it compared to BitchX.  But 'sudo apt-get install irssi' gives me a no go.  I have tried to download the latest version and compile it from the source but I am having compile problems.

Anyone know if there will be a 'apt-get install irssi' soon for 5.10?

Thanks guys!

---

### Post by KingBahamut on 2005-10-17
Do you have all your respositories enabled in sources.list? 

Do that , then retry apt-get install irssi , if not find it then.....

apt-cache search irssi , find the package and install it.

---

### Post by ecobuntu on 2005-10-17
It's:
sudo apt-get install irssi-text

That should get it for you!  That's how i installed it.

---

