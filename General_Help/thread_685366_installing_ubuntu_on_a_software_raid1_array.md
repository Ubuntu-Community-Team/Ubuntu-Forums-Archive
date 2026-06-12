---
title: "installing ubuntu on a software raid1 array"
date: 2008-02-02
forum: General Help
---

### Post by jarthel on 2008-02-02
Someone has mentioned to me that I can setup a RAID1 array using linux even though the chip where the drives are connected isn't RAID capable.

My question is: can I setup a **encrypted** RAID1 array? I have been installing ubuntu 7.10 alternate CD on my wife's laptop and the options when manually partitioning the drive led me to believe encrypted RAID1 is not possible.

can you some confirm?

thank you.

---

### Post by fjgaude on 2008-02-02
The raid1 isn't the boot array, is it?

If it is not I see no reason why the array cannot be encrypted.

Software raid is handled by a program called mdadm, and that works with the kernel module called md.

Let us know if you have any further issues.

---

### Post by jarthel on 2008-02-02
> **fjgaude said:**
> The raid1 isn't the boot array, is it?

If it is not I see no reason why the array cannot be encrypted.

Software raid is handled by a program called mdadm, and that works with the kernel module called md.

Let us know if you have any further issues.

would there be an issue if the array is the boot array as well?

thanks again

---

