---
title: "Ubuntu 21.04 Encrypted ZFS - GPT 1TB SSD - Will not automatically import bpool rpool"
date: 2021-09-12
forum: General Help
---

### Post by j.kemp on 2021-09-12
I have an issue after installing Ubuntu 21.04 with UEFI, ZFS, and  encryption. 

Everything seems to go okay, except when I restarted. The  system would not boot. It drops to the initramfs prompt. After doing  some reading, I discovered I could use 'zpool import' That showed bpool  and rpool ONLINE.

So I ran: 
zpool import
zpool import bpool
zpool import rpool
exit

That brought up the prompt for the passphrase. It responded 'successful' and the system came up quick. 

However, due to the system  needing to be configured, I rebooted several times, having to import the  pools manually each restart.

What do I need to do to have the system import the pools  automatically, and then prompt me for the passphrase? 

I have another system that imports the zpools automatically. (although that system is legacy boot)

Thank you, help would be greatly appreciated.

P.S. I asked this question over on Ask Ubuntu a few days ago, with no responses thus far.

---

