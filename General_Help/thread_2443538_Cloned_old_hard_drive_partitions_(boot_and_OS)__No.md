---
title: "Cloned old hard drive partitions (boot and OS)  Now Can't access Network"
date: 2020-05-16
forum: General Help
---

### Post by 777funk on 2020-05-16
I recently cloned an old hard drive using DD and put it in a laptop of the same model that the original OS (Lubuntu) was in and it works well... however, I can't access some Samba shares and it gives this error:

failed to retrieve share list from server

Could it be related to MAC address of the new hardware (or something else in the network hardware for that matter) not matching what the clone OS is spitting out?

---

### Post by TheFu on 2020-05-17
Samba doesn't care about MACs, but it may be configured to care about IP addresses.  I've never configured my samba servers to care about IPs beyond allowing traffic only from my subnets.

```
  hosts allow = 127.0.0.1 172.22.22.0/24 172.22.22.0/24
  hosts deny = 0.0.0.0/0
```

If the network device name changed, that could have modified some settings. On some versions of Ubuntu, the network device is related to the MAC.  There are ways to override that.  Talk with the systemd team who decided it was a good idea to have unique NIC devices - no more eth0.

---

