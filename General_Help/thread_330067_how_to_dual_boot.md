---
title: "how to dual boot"
date: 2007-01-02
forum: General Help
---

### Post by pearlygate on 2007-01-02
Hi all,

I've been using ubuntu for almost 1 month but now I find it's necessary to also have windows in my computer. I want to install windows on my computer without having to format and partition my hard drive. Is it possible to do that?

If not, is there a way to partition my hard drive without having to format my ubuntu. I seriously won't want to reinstall linux from scratch again. 

Can anyone help?

Thanks

---

### Post by earobinson on 2007-01-02
see sig ... [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by bodhi.zazen on 2007-01-02
> **pearlygate said:**
> Hi all,

I've been using ubuntu for almost 1 month but now I find it's necessary to also have windows in my computer. I want to install windows on my computer without having to format and partition my hard drive. Is it possible to do that?

If not, is there a way to partition my hard drive without having to format my ubuntu. I seriously won't want to reinstall linux from scratch again. 

Can anyone help?

Thanks

Should be no problem.

Boot to a live CD (Ubuntu or Gparted)

Use Gparted to re-size (make smaller) your ubuntu partition.

Install Windows into the free space.

**note:**Windows will want to be on a primary partition and you will need to restore grub in order to boot:

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

