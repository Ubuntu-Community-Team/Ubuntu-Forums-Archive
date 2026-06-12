---
title: "Login Loop 16.04 LTS"
date: 2016-11-05
forum: General Help
---

### Post by gottsc332 on 2016-11-05
Hi all,

I have encountered a login loop issue with 16.04. This is not an issue with an OS upgrade but a randomly occured problem. I followed previous threads detail solutions but nothing worked. These included the backup of .Xauthority, checking permissions, reconfiguring lightdm, and finally I purged and reinstalled lightdm. The OS is updated and upgraded through the terminal upon encountering the issue, as I was hoping it was just a bug. No such luck so far. For additional information no issues were present 12 hours ago upon shutdown but occurred upon start up today, resolution appears to normal, and guest login does not work as well. I am not sure what to do from here, at a worst case scenario I will just back up my files onto an external HDD and reinstall the OS but I would prefer not to do such a drastic operation. Any help would be appreciated.

Thank you.

---

### Post by ventrical on 2016-11-05
> **gottsc332 said:**
> Hi all,

I have encountered a login loop issue with 16.04. This is not an issue with an OS upgrade but a randomly occured problem. I followed previous threads detail solutions but nothing worked. These included the backup of .Xauthority, checking permissions, reconfiguring lightdm, and finally I purged and reinstalled lightdm. The OS is updated and upgraded through the terminal upon encountering the issue, as I was hoping it was just a bug. No such luck so far. For additional information no issues were present 12 hours ago upon shutdown but occurred upon start up today, resolution appears to normal, and guest login does not work as well. I am not sure what to do from here, at a worst case scenario I will just back up my files onto an external HDD and reinstall the OS but I would prefer not to do such a drastic operation. Any help would be appreciated.

Thank you.

Did you try ...

[https://ubuntuforums.org/showthread.php?t=1965997&page=13&p=11894959#post11894959](https://ubuntuforums.org/showthread.php?t=1965997&page=13&p=11894959#post11894959)

---

### Post by gottsc332 on 2016-11-05
> **ventrical said:**
> Did you try ...

[https://ubuntuforums.org/showthread.php?t=1965997&page=13&p=11894959#post11894959](https://ubuntuforums.org/showthread.php?t=1965997&page=13&p=11894959#post11894959)

Thanks for the reply. I already moved .Xauthority before but I tried those instructions again with the command sudo service lightdm restart. It still did not work.

---

### Post by ventrical on 2016-11-05
> **gottsc332 said:**
> Thanks for the reply. I already moved .Xauthority before but I tried those instructions again with the command sudo service lightdm restart. It still did not work.

If you have nVidia proprietary driver you will have to remove it and install nouveau firmware. uhh.. There were some problems during last cycle. Do you have nVidia proprietary installed?

Regards..

btw .. what are the specs of your system..

---

### Post by gottsc332 on 2016-11-05
> **ventrical said:**
> If you have nVidia proprietary driver you will have to remove it and install nouveau firmware. uhh.. There were some problems during last cycle. Do you have nVidia proprietary installed?

Regards..

btw .. what are the specs of your system..

I was thinking that might be route I'd have to take. Unfortunately the systems is not letting me switch to it, the terminal is getting hung up. Luckily, I have nothing of value on the SDD in which the OS is installed so I am going to wipe it and reinstall the OS. Thanks for helping me trouble shoot it.

---

