---
title: "Updating ipw2200"
date: 2006-11-15
forum: General Help
---

### Post by k_smolka on 2006-11-15
Hi All

I have been having problems connecting to a WPA-PSK network in edgy which worked fine in dapper.

I have been looking for a answer for a while now and was thinking it might be a good idea to check i have the latest ipw2200 driver.

when  dmesg | grep ipw2200


[17179595.132000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
[17179595.132000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179595.132000] Driver 'ipw2200' needs updating - please use bus_type methods
[17179595.132000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179595.368000] ipw2200: Detected geography ZZR (14 802.11bg channels, 0 802.11a channels)

So  it looks like my driver needs updating. But i dont know how to do it. 

Any info on tutorials or posts would be most appreciated. Or if anyone has any other ideas i would love to hear.

Regards 

Karl

---

### Post by coffeecat on 2006-11-15
Karl, I'm posting from Edgy now, on my laptop using the Intel ipw2200 with WPA-PSK. dmesg | grep ipw2200 here gives me:

> [17179607.492000] ipw2200: Intel(R) PRO/Wireless 2200/2915 Network Driver, 1.1.2kmprq
[17179607.492000] ipw2200: Copyright(c) 2003-2006 Intel Corporation
[17179607.492000] Driver 'ipw2200' needs updating - please use bus_type methods
[17179607.652000] ipw2200: Detected Intel PRO/Wireless 2200BG Network Connection
[17179608.060000] ipw2200: Detected geography ZZD (13 802.11bg channels, 0 802.11a channels)

But for me it connects reliably (using network-manager-gnome)  on every boot - so far :wink: - so it looks as though that 'needs updating' message can be ignored.

I'm afraid I've got no suggestions beyond using network-manager if you are not already.

---

