---
title: "Missing static IP in landscape-sysinfo"
date: 2024-05-17
forum: General Help
---

### Post by matthys on 2024-05-17
Hello, not sure where to post this but will ask here:

I recently notice that at login I do not see my static IP in the landscape-sysinfo anymore.
And I really have no clue where to find it, as the config for landscape-sysinfo is limited.

Before I had (sorry it's a bit dated):
 ```
 System information as of Sun 18 Sep 2022 07:52:38 AM CEST

  System load:  0.11                Processes:               157
  Usage of /:   71.9% of 105.94GB   Users logged in:         0
  Memory usage: 21%                 IPv4 address for enp1s0: 192.168.1.1
  Swap usage:   23%                 IPv4 address for enp3s7: 80.xx.xx.xx
```

Now:
 ```
System information as of Fri May 17 05:23:09 PM CEST 2024

  System load:  0.17                Processes:               160
  Usage of /:   40.0% of 105.94GB   Users logged in:         1
  Memory usage: 40%                 IPv4 address for enp3s7: 80.xx.xx.xx
  Swap usage:   0%
```

Did something change? I'm missing enp1s0 and it's up and running but a static IP.

Thanks,
Matthijs

---

### Post by TheFu on 2024-05-18
**ip addr**
will show all IPs on a system.  IPv4 and IPv4.

If you want a prettier report, use **inxi -ixx**.  Leave off the added 'x' if you want less information or just **inxi -i**

BTW, you should get a copy of this book and have it as a reference for questions like this: [https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php)

---

### Post by matthys on 2024-05-19
Of course "ip addr" will show the addresses (both enp1s0 and enp3s7 interfaces), but why is the enp1s0 missing from the landscape-sysinfo?
To me it seems there was/were some changes to detection in landscape-sysinfo...

---

### Post by SAH62 on 2024-08-22
I just noticed the same issue on one of my servers. It has two physical network interfaces, landscape-sysinfo used to display both, and now it's displaying only one. I recently upgraded from jammy to noble, and I didn't note if the issue appeared before the upgrade. It's definitely there now. Did something change in the Network plugin?

---

### Post by matthys on 2024-08-23
Yes, and it's a pity there is no update on this. So far I have not figured out if this is a configuration problem but I guess the static IP is removed ....

---

### Post by SAH62 on 2024-08-23
The code for the network plugin can be found at /usr/lib/python3/dist-packages/landscape/sysinfo/network.py. It appears to be able to enumerate all known interfaces. Interestingly, the man page for landscape-sysinfo includes an example with two IPv4 addresses. If I run the command with only the Network plugin it returns information for only one interface:

> $ landscape-sysinfo --sysinfo-plugins=Network
  IPv4 address for eth0: 192.168.1.253
$


---

