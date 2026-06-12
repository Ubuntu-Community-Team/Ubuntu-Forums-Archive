---
title: "Error after upgrade to kernel"
date: 2014-07-01
forum: General Help
---

### Post by jcllings on 2014-07-01
So I have an awesome macro gaming keyboard and also mouse from ROCCAT. Both are Linux supported. After upgrading last night, I got the following error when I load my configuration utilities:

```
Error in ioctl HIDIOCGFEATURE: No such device
```

This: [http://bit.ly/1pUlhq7](http://bit.ly/1pUlhq7)  indicates that I can fix by upgrading my kernel. Specific one mentioned is 3.14.10-031410-generic but I don't see it available.  
Is there a software source where I can get this?  I default to upgrading rather than downgrading but the later is also an option and an easily testable one at that.

OK... now I've tried downgrading and it works. The problem kernel is 3.13.0-30-generic.  I would still prefer an upgrade to a downgrade.

---

### Post by jcllings on 2014-07-01
Nailed it. Procedure was:

```

cd ~/
mkdir ~/3.14-trusty-temp
cd 3.14-trusty
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-trusty/linux-headers-3.14.0-031400-generic_3.14.0-031400.201403310035_amd64.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-trusty/linux-headers-3.14.0-031400_3.14.0-031400.201403310035_all.deb
wget http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.14-trusty/linux-image-3.14.0-031400-generic_3.14.0-031400.201403310035_amd64.deb
sudo dpkg -i *.deb
cd ..
#rm -rf ~/3.1.4-trusty-temp 

```

rm -rf disabled for newb safety. ;-)

---

