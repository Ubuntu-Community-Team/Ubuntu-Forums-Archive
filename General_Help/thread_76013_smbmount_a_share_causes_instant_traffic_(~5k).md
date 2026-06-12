---
title: "smbmount a share causes instant traffic (~5k)"
date: 2005-10-14
forum: General Help
---

### Post by dave1111 on 2005-10-14
When I mount a share via 
mount -t smbfs //host/share /mnt 
there is an ongoing network traffic and the samba sends out QUERY_PATH_INFO Packets for the dir "\". This causes about 5 kB/s traffic.
I recorded it with ethereal.

Where is the problem? I don't think this is normal or is it?

---

### Post by unclben on 2005-10-19
I'm having a similar issue. I don't know the packet type, but EtherApe verifies that it's Samba traffic. In my case, there is a Samba share from Ubuntu mounted on a WinXP Pro box. Traffic starts and stops about every thirty seconds. When it's 'on' I see about 250 kbps from Breezy to XP, with very little or none moving in the other direction.

---

