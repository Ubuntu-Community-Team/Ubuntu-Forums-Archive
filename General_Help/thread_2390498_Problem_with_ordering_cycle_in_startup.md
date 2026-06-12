---
title: "Problem with ordering cycle in startup"
date: 2018-04-29
forum: General Help
---

### Post by David_Partridge on 2018-04-29
During system startup I see the following in syslog:

```
Apr 29 14:19:28 Charon systemd[1]: lvm2-activation-net.service: Found dependency on dbus.service/start
Apr 29 14:19:28 Charon systemd[1]: lvm2-activation-net.service: Found dependency on basic.target/start
Apr 29 14:19:28 Charon systemd[1]: lvm2-activation-net.service: Found dependency on paths.target/start
Apr 29 14:19:28 Charon systemd[1]: lvm2-activation-net.service: Found dependency on acpid.path/start
Apr 29 14:19:28 Charon systemd[1]: lvm2-activation-net.service: Found dependency on sysinit.target/start
Apr 29 14:19:28 Charon systemd[1]: lvm2-activation-net.service: Found dependency on mt-st.service/start
Apr 29 14:19:28 Charon systemd[1]: lvm2-activation-net.service: Found dependency on remote-fs.target/start
Apr 29 14:19:28 Charon systemd[1]: lvm2-activation-net.service: Found dependency on remote-fs-pre.target/start
Apr 29 14:19:28 Charon systemd[1]: lvm2-activation-net.service: Found dependency on lvm2-activation-net.service/start
Apr 29 14:19:28 Charon systemd[1]: lvm2-activation-net.service: Breaking ordering cycle by deleting job open-iscsi.service/start
Apr 29 14:19:28 Charon systemd[1]: open-iscsi.service: Job open-iscsi.service/start deleted to break ordering cycle starting with lvm2-activation-net.service/start
```

What do I need to do so that the open-iscsi service will actually be started correctly?

Thanks David

---

### Post by David_Partridge on 2018-04-30
I just upgraded to kernel 4.15  and now I see this in dmesg:

```
[    9.393232] systemd[1]: NetworkManager.service: Found ordering cycle on NetworkManager.service/start
[    9.397204] systemd[1]: NetworkManager.service: Found dependency on dbus.service/start
[    9.401088] systemd[1]: NetworkManager.service: Found dependency on basic.target/start
[    9.404879] systemd[1]: NetworkManager.service: Found dependency on paths.target/start
[    9.408608] systemd[1]: NetworkManager.service: Found dependency on acpid.path/start
[    9.412288] systemd[1]: NetworkManager.service: Found dependency on sysinit.target/start
[    9.415892] systemd[1]: NetworkManager.service: Found dependency on mt-st.service/start

```

and in syslog I see:

```
Apr 30 10:12:28 Charon systemd[1]: network.target: Found ordering cycle on network.target/start
Apr 30 10:12:28 Charon systemd[1]: network.target: Found dependency on NetworkManager.service/verify-active
Apr 30 10:12:28 Charon systemd[1]: network.target: Found dependency on sysinit.target/start
Apr 30 10:12:28 Charon systemd[1]: network.target: Found dependency on mt-st.service/start
Apr 30 10:12:28 Charon systemd[1]: network.target: Found dependency on remote-fs.target/start
Apr 30 10:12:28 Charon systemd[1]: network.target: Found dependency on remote-fs-pre.target/start
Apr 30 10:12:28 Charon systemd[1]: network.target: Found dependency on nfs-server.service/start
Apr 30 10:12:28 Charon systemd[1]: network.target: Found dependency on network.target/start
Apr 30 10:12:28 Charon systemd[1]: network.target: Breaking ordering cycle by deleting job NetworkManager.service/verify-active
Apr 30 10:12:28 Charon systemd[1]: NetworkManager.service: Job NetworkManager.service/verify-active deleted to break ordering cycle starting with network.target/start
Apr 30 10:12:28 Charon systemd[1]: network.target: Found ordering cycle on network.target/start
Apr 30 10:12:28 Charon systemd[1]: network.target: Found dependency on NetworkManager.service/start
Apr 30 10:12:28 Charon systemd[1]: network.target: Found dependency on sysinit.target/start
Apr 30 10:12:28 Charon systemd[1]: network.target: Found dependency on mt-st.service/start
Apr 30 10:12:28 Charon systemd[1]: network.target: Found dependency on remote-fs.target/start
Apr 30 10:12:28 Charon systemd[1]: network.target: Found dependency on remote-fs-pre.target/start
Apr 30 10:12:28 Charon systemd[1]: network.target: Found dependency on nfs-server.service/start
Apr 30 10:12:28 Charon systemd[1]: network.target: Found dependency on network.target/start
Apr 30 10:12:28 Charon systemd[1]: network.target: Breaking ordering cycle by deleting job sysinit.target/start
Apr 30 10:12:28 Charon systemd[1]: sysinit.target: Job sysinit.target/start deleted to break ordering cycle starting with network.target/start

```

Clearly something is amiss, so what needs to be changed to resolve these issues?

Thanks
David

---

