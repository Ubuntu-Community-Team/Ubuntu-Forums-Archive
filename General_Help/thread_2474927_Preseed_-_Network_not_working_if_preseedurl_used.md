---
title: "Preseed - Network not working if preseed/url used"
date: 2022-05-11
forum: General Help
---

### Post by jakubfranek on 2022-05-11
In custom image I use preseed/url. I boot from a flash drive. I boot from USB, and use preseed/url.


The official documentation says that it should be enough to create a file with content **kill-all-dhcp; netcfg; **and add to the preseed **d-i preseed/run string file.sh**. However, this does not seem to work in ubuntu 22.04 (I don't know if this works in earlier versions of ubuntu).
Is there any way to restart the network after downloading the preseed settings if the above commands do nothing? Thanks


Official documentation link: [https://help.ubuntu.com/20.04/installation-guide/amd64/apbs04.html#preseed-network](https://help.ubuntu.com/20.04/installation-guide/amd64/apbs04.html#preseed-network)

---

