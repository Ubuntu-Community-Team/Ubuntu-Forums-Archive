---
title: "Ubuntu 12.10 to 14.04 release."
date: 2014-03-29
forum: General Help
---

### Post by Catalys on 2014-03-29
Dear,


Perhaps a weird question but when 14.04 releases, can I do a direct upgrade to 14.04 from 12.10? (server).

---

### Post by oldos2er on 2014-03-29
No. You can update from LTS to LTS, i.e. from 12.04 to 14.04; but from a non-LTS release you need to go to the next higher version and so on. 12.10 to 13.04 (which is [EOL]("https://help.ubuntu.com/community/EOLUpgrades")) to 13.10 to 14.04.

---

### Post by Catalys on 2014-03-29
Will this break my apache, postfix mysql and other configs? and will it create like new configs over the old ones, maybe creating security holes? Since 3-4 upgrades seems like alot.

---

### Post by oldos2er on 2014-03-29
System config files will be updated, so make backup copies of anything important. I have no idea about "security holes" from an upgrade though.

---

### Post by 3rdalbum on 2014-03-29
When the updater is installing new packages it will ask you if you want to keep the old config files or replace them. But you should do a clean install of 14.04 because it will be quicker and easier and safer than two/three upgrades.

---

