---
title: "Need Script"
date: 2013-05-05
forum: General Help
---

### Post by Chrys Collier on 2013-05-05
Hello Everyone,

I'm looking to create a script which executes on boot to volume that zeros all the data on the volume/partition. I was figuring I'd need to use fallocate... but I'm not sure about having execute on startup and also not sure the full fallocate script necessary to overwrite... say... 29GBs of data with 0s.

Essentially, I'm running TrueCrypt on a 32GB usb with 3 Ubuntus (dummy partition, truecrypt partition (normal volume(hidden volume))), and when one loads the normal volume, I'd like the normal volume to be filled with 0'd data causing the hidden volume to be completely overwritten but maintaining the existence of the normal volume. Ideas?

I've got like 4 scripts here that I could compile together; but, alas, my knowledge in terminal is limited to simple web usage. I've only started training encryption and data security. I'd also like any thoughts you have on how to mask the entire drive's connection (such as hidden network connection, permanently spoofing the mac address, and running TOR/VPN/Socks5) by default.

And has anyone seen a USB female cap that can copy data/erase data/format data simply on insertion? I wouldn't think you would need a large os loaded to it... ignoring the GUI and simply having a script which copies the headers and content (encrypted or not) should save needed space... thoughts?

Best Regards,

Chrys

---

