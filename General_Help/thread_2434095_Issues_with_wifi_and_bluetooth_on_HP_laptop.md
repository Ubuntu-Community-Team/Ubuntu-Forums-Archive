---
title: "Issues with wifi and bluetooth on HP laptop"
date: 2019-12-30
forum: General Help
---

### Post by saurian2 on 2019-12-30
Hello,

I got an HP laptop without knowing that it has its issues with Ubuntu. So my main issues are connected to wifi and bluetooth. When I installed Ubuntu 18.04.3 the OS didn't see any wifi and bluetooth. For wifi I compiled and used the driver from [here]("https://github.com/lwfinger/rtlwifi_new"). I use my phone as a hotspot so if I go to a different room Ubuntu loses connection. Also sometimes it loses connection with the phone being near the laptop and I have to wait to reconnect. On my old laptop with Ubuntu 16 I didn't have any issues. Is there any other better solution? I used first 5 steps from [here]("http://ubuntuhandbook.org/index.php/2018/08/no-wifi-adapter-found-hp-laptops-ubuntu-18-04/") to build and use the driver.

Now regarding bluetooth there is a different story. I wasn't able to make it work in any way. I mean even running `rfkill` command I get:

```
sudo rfkill list

0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

```

Can anyone help? Thanks in advance.

---

### Post by dvpdesigns on 2019-12-30
Also having the same issue with no bluetooth. When I do rfkill list I get the same... no mention of bluetooth. I'm using an HP Spectre on Ubuntu 19.10. Can anyone help us?

---

