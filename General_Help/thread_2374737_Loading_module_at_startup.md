---
title: "Loading module at startup"
date: 2017-10-18
forum: General Help
---

### Post by andrew772 on 2017-10-18
Hello. I have a module dvb-usb-rtl28xxu which I want to add to my startup sequence (currently I need to do modprobe dvb-usb-rtl28xxu in a terminal each time).

I have tried adding it to /etc/modules but it's still not loading. I have checked /var/log/boot.log and dmesg and there is no mention of it.

Any help would be greatly appreciated. Thanks.

---

### Post by DuckHook on 2017-10-18
It sounds like this may be one of those peripherals that aren't yet fully powered up/initiated when /etc/modules is called. Try the second answer in [this]("https://askubuntu.com/questions/766022/ubuntu-16-04-auto-load-usb-dvb-t-dongle-module") thread. The OP in that thread seems to have the same problem as yours with the same piece of HW.

---

