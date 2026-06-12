---
title: "Idle time during bootup"
date: 2007-03-28
forum: General Help
---

### Post by cayamara on 2007-03-28
Hi folks!

I'm with ubuntu for almost 2 years now and I really like it! Recently I did a fresh install 6.10 install on my laptop though and it takes very long to boot up (the attached chart says 1:40). During the boot process there is a time when the progress bar doesn't move for about 40-50 seconds, so I tried to check that out with the bootchart package.

It seems that the S40networking script and dhclient in specific take so long. I can only assume that this is because I have encrypted wireless ethernet, which is managed through [NetworkManager]("http://www.gnome.org/projects/NetworkManager/"). Because of that, the dhclient script on bootup is useless, because the key is not available at boottime yet, so dhclient takes a long time to time out unsucessfully. If I am not mistaken, how would be an elegant way to disable this on bootup? Is this save to do? Also, it would seem like a common scenario for laptop users who just go online using an encrypted wireless connection.

Also, please give me other ideas if the above is not correct. I have attached the bootchart in question.

Thanks for reading, thanks for answering :)!

---

### Post by wj32 on 2007-03-28
Try using Boot-Up Manager or Services to disable it. If that doesn't work, edit it in /etc/init.d.

---

### Post by cayamara on 2007-03-28
Great! I just did a chmod -x on the networking and the wpa-ifupdown script in /etc/init.d and now I'm from 1:20 to 34 secs! And everything works since the NetworkManager takes care of it anyways.

Thanks.

---

