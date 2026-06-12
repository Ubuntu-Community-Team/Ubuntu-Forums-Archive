---
title: "Trevino suspend2 patched kernal, am I doing this right?"
date: 2007-08-04
forum: General Help
---

### Post by blingboi on 2007-08-04
Ok, new ubuntu user here needing suspend2

This is what I'm doing from a fresh Feisty Fawn install

-I install all updates
-I configure my ATI drivers (AIGLX)

I then go to Trevinos download [site]("http://download.tuxfamily.org/3v1deb/pool/feisty/suspend2/") of the most recent patched suspend2 kernal

I proceed to get these 3 files:

```
wget http://download.tuxfamily.org/3v1deb/pool/feisty/suspend2/linux-image-2.6.20-16-generic_2.6.20-16.29+suspend2~2.2.10+3v1ubuntu0_i386.deb
wget http://download.tuxfamily.org/3v1deb/pool/feisty/suspend2/linux-restricted-modules-common_2.6.20.5-15.20+suspend2~2.2.10+3v1ubuntu0_all.deb
wget http://download.tuxfamily.org/3v1deb/pool/feisty/suspend2/linux-headers-2.6.20-16-generic_2.6.20-16.29+suspend2~2.2.10+3v1ubuntu0_i386.deb
```

then i install them with these commands:

```
sudo dpkg -i linux-image-2.6.20-16-generic_2.6.20-16.29+suspend2~2.2.10+3v1ubuntu0_i386.deb
sudo dpkg -i linux-restricted-modules-common_2.6.20.5-15.20+suspend2~2.2.10+3v1ubuntu0_all.deb
sudo dpkg -i linux-headers-2.6.20-16-generic_2.6.20-16.29+suspend2~2.2.10+3v1ubuntu0_i386.deb
```

I reboot.  After that I get the rest of updated files and install them:

```
wget http://download.tuxfamily.org/3v1deb/pool/feisty/suspend2/acpi-support_0.95-1~3v1ubuntu0_i386.deb
sudo dpkg -i acpi-support_0.95-1~3v1ubuntu0_i386.deb

wget http://download.tuxfamily.org/3v1deb/pool/feisty/suspend2/hibernate_1.94-4~3v1ubuntu1_all.deb
sudo dpkg -i  hibernate_1.94-4~3v1ubuntu1_all.deb

wget http://download.tuxfamily.org/3v1deb/pool/feisty/suspend2/initramfs-tools-suspend2_0.5.1-0~3v1ubuntu0_i386.deb
sudo dpkg -i initramfs-tools-suspend2_0.5.1-0~3v1ubuntu0_i386.deb
```

then I reboot again.

Is this all there is to it?  Since suspend2 is patched into the kernal and everything.
I've been playing around with suspend and it seems to work.  Except I lose my wireless ability sometimes.
I just want to verify that I did it correctly, thanks.

---

### Post by blingboi on 2007-08-04
:(

---

### Post by Ptero-4 on 2007-12-31
If you're on feisty just add the repository and you're good to go. If you're on gutsy OTOH, tough luck, it seems M$ forced treviño to close shop.

---

