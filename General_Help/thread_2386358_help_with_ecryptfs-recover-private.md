---
title: "help with ecryptfs-recover-private"
date: 2018-03-04
forum: General Help
---

### Post by expat778877 on 2018-03-04
This started with a GRUB update about three or four weeks ago, which rebooted my laptop and made grub disappear.   I got past that, but then couldn't boot 16.04 LTS successfully ([https://ubuntuforums.org/showthread.php?t=2385844&highlight=LUKS](https://ubuntuforums.org/showthread.php?t=2385844&highlight=LUKS)).  Now I've given up salvaging this installation, and plan to re-install, but there are a few files I'd like to copy from this old install before I reload a fresh copy.  

 I can mount the volume when booting a 16.04 LTS recovery USB, so I know the password is OK, and then I can see most of the directories but I can't access /home/(my ID).    I ran ecryptfs-recover-private and saw "INFO: Success!  Private data mounted at [/tmp/ecryptfs.xxxx]" but all I see in my /home directory is an file called Access-Your-Private-Data.desktop, which runs 'ecryptfs-mount-private'.   The icon does nothing, but running that command gives 'ERROR: Encrypted private directory is not setup properly'.

How can I mount my old /home directory?

Thanks

---

### Post by expat778877 on 2018-03-17
any ideas?

---

