---
title: "Can't write to ext4 drives on fresh install 14.04.02"
date: 2015-07-12
forum: General Help
---

### Post by Excuse_Me on 2015-07-12
I have this problem where I can't copy or drag anything to my ext4 drives in a new install of ubuntu. When I click permission it says I don't have permission because I'm not root. I googled it and tried these commands

sudo chgrp adm
sudo chmod g+w
chmod 777

None of them worked I still can't write on the drives or the partition of my root drive that isn't root. I guess it's a quick fix somewhere but I can't find it. Very thankful for any help!

---

### Post by dino99 on 2015-07-12
> **Excuse_Me said:**
> I have this problem where I can't copy or drag anything to my ext4 drives in a new install of ubuntu. When I click permission it says I don't have permission because I'm not root. I googled it and tried these commands

sudo chgrp adm
sudo chmod g+w
chmod 777

None of them worked I still can't write on the drives or the partition of my root drive that isn't root. I guess it's a quick fix somewhere but I can't find it. Very thankful for any help!

its a bad, very bad idea to modify the default system settings: for example, chmod 777 let the whole wild world seeing/modifying/erasing/raping/.... your system/personal data/..... (the nsa & the likes will be happy ;) )
if your ubuntu is standard, then there is no need to change the configuration.

---

### Post by Excuse_Me on 2015-07-12
never mind this command did it
sudo chmod -R a+rw

---

### Post by Excuse_Me on 2015-07-12
> **dino99 said:**
> its a bad, very bad idea to modify the default system settings: for example, chmod 777 let the whole wild world seeing/modifying/erasing/raping/.... your system/personal data/..... (the nsa & the likes will be happy ;) )
I did read about that but I wanted to write on the drive more than I wanted the nsa not to mess with it. Anyway all the commands involving chmod 777 I found returned various error messages?

My Ubuntu is "standard" I guess it's a totally fresh install I've downloaded a couple of apps from software center but haven't messed with anything else for some reason my drives and partitions was read only after formatting them in ext4?

---

