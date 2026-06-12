---
title: "grub2 and timeout problem"
date: 2016-08-10
forum: General Help
---

### Post by michaelbr on 2016-08-10
Greetings all:
After I upgraded my Ubuntu from 14.04 to 16.04, there are several problems, one of the is the TIMEOUT variable in grub2 config file is not taking effect, I've set the timeout = 3, but when the grub2 screen came up, the timeout showing at the bottom of the screen is 10s instead of 3, where should I change? Is there any old config file still in the system? This is what I did:
```
sudo gedit /etc/default/grub
```

this is what in my file after change:
```
GRUB_DEFAULT=2
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=3
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""
```

when I tried to save the file, it gave me this error message:
```
** (gedit:5938): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-spell-enabled not supported
```

then I did ```
sudo update-grub
```

does the above error has anything to do with timeout not working? How do I fix it?

---

### Post by grahammechanical on 2016-08-10
Gedit will automatically create a backup copy of system files which may still be having an effect. The backup copy has the same file name but with the tilde character (  ~ ) prefixed to the file name. and that tilde character makes the backup file a hidden file.

If you set the file manager to view hidden files and go to /etc/default/ you may see both grub and ~grub.

Regards.

---

### Post by tsjswimmer on 2016-08-14
Personally, I've had timeout issues when hibernating on 16.04. Are you also attempting to hibernate?

Try running ```
sudo grub-editenv /boot/grub/grubenv unset recordfail
``` and see what happens.

---

### Post by michaelbr on 2016-08-18
> **tsjswimmer said:**
> Personally, I've had timeout issues when hibernating on 16.04. Are you also attempting to hibernate?

Try running ```
sudo grub-editenv /boot/grub/grubenv unset recordfail
``` and see what happens.

Sorry for the late reply, I didn't get the notification of your reply. I tried to run the above code, but nothing happened, it went straight to my prompt, What I'm supposed to see?

I just remembered reading over the net that hibernating has something to do with the slow boot up time, and I'm having problem with slow boot up time, with my previous 14.04, the boot up time was much faster, but after upgrade, the boot up time almost doubled, I'm not attempting to hibernate, how can I check it and disable if needed?

---

### Post by michaelbr on 2016-08-18
> **grahammechanical said:**
> Gedit will automatically create a backup copy of system files which may still be having an effect. The backup copy has the same file name but with the tilde character (  ~ ) prefixed to the file name. and that tilde character makes the backup file a hidden file.

If you set the file manager to view hidden files and go to /etc/default/ you may see both grub and ~grub.

Regards.
Sorry for the late reply, I forgot to check the notification (I'm sorry, I should have checked regardless this forum everyday).

I went to the /etc/default/ folder, and there are 3 grub files:
1) grub with timeout=3
2) grub.bak with timeout=10
3) grub~ with timeout=3
can I just delete the grub.bak?

---

