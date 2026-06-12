---
title: "Boot up sequence question....."
date: 2007-03-29
forum: General Help
---

### Post by rayj00 on 2007-03-29
It seems to me that Ubuntu 6.10 used to boot up quicker then it does now.
It takes about 2 minutes on a Dell Duo Core machine to boot up to login request.

Could the highlighted syslog entry below be a problem?

Mar 29 07:34:34 Ubuntu-Pentest kernel: [17179669.864000] lo: Disabled Privacy Extensions
Mar 29 07:34:34 Ubuntu-Pentest kernel: [17179669.868000] ADDRCONF(NETDEV_UP): eth0: link is not ready
Mar 29 07:34:34 Ubuntu-Pentest kernel: [17179669.868000] IPv6 over IPv4 tunneling driver
[B]Mar 29 07:34:38 Ubuntu-Pentest gconfd (rayj-4653): Resolved address "xml:readwrite:/home/rayj/.gconf" to a writable configuration source at position 0
Mar 29 07:36:25 Ubuntu-Pentest kernel: [17179780.460000] /dev/vmnet: open called by PID 4835 (vmware-vmx)[/B]
Mar 29 07:36:25 Ubuntu-Pentest kernel: [17179780.460000] device eth0 entered promiscuous mode
Mar 29 07:36:25 Ubuntu-Pentest kernel: [17179780.460000] audit(1175178985.036:2): dev=eth0 prom=256 old_prom=0 auid=4294967295
Mar 29 07:36:25 Ubuntu-Pentest kernel: [17179780.460000] bridge-eth0: enabled promiscuous mode
Mar 29 07:36:25 Ubuntu-Pentest kernel: [17179780.460000] /dev/vmnet: port on hub 0 successfully opened
Mar 29 07:36:25 Ubuntu-Pentest kernel: [17179781.052000] /dev/vmmon[4841]: host clock rate change request 0 -> 19
Mar 29 07:36:29 Ubuntu-Pentest kernel: [17179785.292000] /dev/vmmon[4841]: host clock rate change request 19 -> 83

Thanks,

Ray

---

