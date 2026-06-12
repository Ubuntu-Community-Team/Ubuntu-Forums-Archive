---
title: "Reinstall VMware server"
date: 2007-04-16
forum: General Help
---

### Post by trcduong on 2007-04-16
Hello there,
I have problem to reinstall the VMware, after I remove the VMware server, reboot the computer and try to reinstall the VMware server, I received the message the computer can not install the VMware server because already install in this computer, please help me, Thank you very much.

---

### Post by thelinuxguy on 2007-04-16
> **trcduong said:**
> Hello there,
I have problem to reinstall the VMware, after I remove the VMware server, reboot the computer and try to reinstall the VMware server, I received the message the computer can not install the VMware server because already install in this computer, please help me, Thank you very much.

Take a look here: [http://ubuntuforums.org/showpost.php?p=2404305&postcount=3](http://ubuntuforums.org/showpost.php?p=2404305&postcount=3)

---

### Post by beerorkid on 2007-04-16
i have ran into this a few different times in player or server while trying to install the other.

Make sure you have you created VM's somewhere safe (mine are in my home dir) and ```
sudo rm -rf /etc/vmware
```

that will allow you to start over fresh.

---

