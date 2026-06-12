---
title: "Another slow boot up issue"
date: 2007-12-13
forum: General Help
---

### Post by InnoIH on 2007-12-13
I've recently started having to wait for ages for ubuntu to boot up - it lags right at the start. I don't think it's being caused by anything caused in the other threads, but I could be wrong.

I've attached the bootchart output would really appreciate some help analyzing it - and maybe some troubleshooting advice. Cheers.

---

### Post by FakeOutdoorsman on 2007-12-13
I don't know what is going on there, but did you try to [re-profile your boot]("http://ubuntuforums.org/showpost.php?p=3302592&postcount=21")?  You can also try to disable usplash.  This will remove the Ubuntu logo when booting and allow you too see what is currently being loaded.  Remove the words **quiet** and **splash** from your kernel line in /boot/grub/menu.lst.

---

### Post by InnoIH on 2007-12-13
Thanks. I'll try both of those.. but I'm not sure they'll put much of a dent in a 2-3 min boot... fingers crossed anyways.

---

