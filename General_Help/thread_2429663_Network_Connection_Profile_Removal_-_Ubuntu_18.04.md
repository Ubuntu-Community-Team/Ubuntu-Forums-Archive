---
title: "Network Connection Profile Removal - Ubuntu 18.04"
date: 2019-10-21
forum: General Help
---

### Post by erudes91 on 2019-10-21
Hello everyone,

Just installed Ubuntu 18.04 to act as a file server with SAMBA, computer is joined to the AD Domain and it works super fine.

However, whenever I reboot the server, I need to select a different network profile which is NOT managed, in order to get connection.

As you can see on the attachment I have two profiles: ifupdown (enp3s0) which is unmanaged (I cant configure it) and the netplan-enp3s0. The first one is the one that should remain, and start along with the system without having to select it in order to get connectivity.

What should I do in order to get that one only available, and active everytime the system boots up?

Many thanks!

---

### Post by Skaperen on 2019-10-21
highlight (move the blue bar down) the profile to remove and click on the "-" button in the lower left.

---

### Post by erudes91 on 2019-10-22
That doesn't work, the deleted profile gets automatically created each time. The one I want to use is the one that's unmanaged :/

---

### Post by erudes91 on 2019-10-22
[FONT=courier new][/FONT]Close this please, I re installed the OS and now it's fine

---

