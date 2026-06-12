---
title: "How do I find and install VMWare in Ubuntu"
date: 2018-05-22
forum: General Help
---

### Post by waltd on 2018-05-22
Hi all, where can I find the free version of VMWare and how do I install it into Ubuntu? I've google the topic but I found the results confusing.

---

### Post by hrsetrdr on 2018-05-22
```
sudo apt-get install build-essential linux-headers-`uname -r`
```


Go to:   [https://my.vmware.com/en/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/14_0](https://my.vmware.com/en/web/vmware/free#desktop_end_user_computing/vmware_workstation_player/14_0)

There are both the  Windows and Linux versions

cd to directory where you downloaded VMware-Player-14.1.2-8497320.x86_64.bundle
```

chmod +x VMware-Player-14.1.2-8497320.x86_64.bundle
```

```
sudo ./VMware-Player-14.1.2-8497320.x86_64.bundle
```

---

