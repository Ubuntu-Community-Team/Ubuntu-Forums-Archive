---
title: "Hibernate: How to on 19.04 and 19.10 and probably others"
date: 2019-12-10
forum: General Help
---

### Post by GhX6GZMB on 2019-12-10
My system will now hibernate, both with 'sudo systemctl hibernate' and by closing the lid.
With Hibernate you can close a session quickly and restore it again. As opposed to Suspend which needs power to sustain the RAM contents, Hibernate suspends to HDD/SSD, storing the sesson indefinitely.
But getting Hibernate running on Ubuntu is hairy. Forget making a "swap file", it won't work. You need a swap partition

Here's the recipe:

1: repartition your HDD/SSD to make a swap partition that's as large or larger than your RAM. In my case it's **/dev/sda2**

2: make a swap partition using **sudo mkswap /dev/sda2**

3: execute **sudo swapon /dev/sda2**

4: verify the partition with **sudo lsblk** and **sudo blkid** and copy the UUID of **/dev/sda2**  

5: configure initramfs by creating (or editing) **/etc/initramfs-tools/conf.d/resume** to contain the following line: **RESUME=UUID=***yourswapUUID*

6: modify **/etc/default/grub** by adding **resume=UUID=***yourswapUUID* within the quotes in **GRUB_CMDLINE_LINUX_DEFAULT=**"quiet splash ..."

7: execute [B]sudo update-grub
[/B]
8: reboot

9: update policies by creating (or editing) **/etc/polkit-1/localauthority/50-local.d/com.ubuntu.enable-hibernate.pkla** with the following content:


      ```


     Re-enable hibernate by default in upower]
Identity=unix-user:*
Action=org.freedesktop.upower.hibernate
ResultActive=yes

 [Re-enable hibernate by default in logind]
Identity=unix-user:*
Action=org.freedesktop.login1.hibernate;org.freedesktop.login1.handle-hibernate-key;org.freedesktop.login1;org.freedesktop.login1.hibernate-multiple-sessions;org.freedesktop.login1.hibernate-ignore-inhibit
ResultActive=yes 


```

10: edit /etc/default/grub and add this (grub-undocumented) line: **GRUB_RECORDFAIL_TIMEOUT=$GRUB_TIMEOUT**

11: execute **sudo update-grub**

12: reboot

Hibernate is now set up and enabled, if you want to use the Lid switch it just needs to be set as such. Enjoy :)


---An oddity is, that XScreenSaver is reponsible for re-login. Apparently nobody cared about this...

---

### Post by TheFu on 2019-12-10
Isn't there a sub-forum for tutorials?

---

### Post by GhX6GZMB on 2019-12-11
My apologies, I'd missed that. Post has been copied to there.

---

### Post by TheFu on 2019-12-11
> **ml9104 said:**
> My apologies, I'd missed that. Post has been copied to there.
Could have asked an admin to move it. Perhaps one will merge these and remove my posts since they won't be useful at all then.

---

### Post by GhX6GZMB on 2019-12-11
Moving a thread is not possible, even for a thread starter.

An Admin could delete this thread, please.

---

