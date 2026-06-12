---
title: "Simple VMware Questions"
date: 2008-05-28
forum: General Help
---

### Post by IHATEDLINK on 2008-05-28
hey
I'm dual-booting with Vista (Sad Smiley) because I can't get Dlink's DWA-110 to work with Ubuntu.
I'm thinking of VMware but I have a few doubts about it. Like:

MAIN QUESTION: Am I able to use Dlink's driver FROM Windows and get the connection to work in Ubuntu?
2. Do I have to split my RAM? Cause I only have 512mb..
3. Can I use VMware with my existing Vista installation?

Thanks.

---

### Post by Keithel on 2008-07-01
> **IHATEDLINK said:**
> MAIN QUESTION: Am I able to use Dlink's driver FROM Windows and get the connection to work in Ubuntu?
Yes, VMware will create a virtual network device that will map to the windows network driver -- Either using bridged networking, or via NAT provided by VMware.  (There is also 'host only networking' which will make a network that is just between the VM and your host -- without any outside connection -- but this doesn't accomplish what you're looking for.)

> **IHATEDLINK said:**
> 2. Do I have to split my RAM? Cause I only have 512mb..
Yes.  You will configure the virtual machine so that it will have a certain portion of your RAM.  -- how much of it is used at any given time, however, will generally be less IIRC.  I'd recommend getting more RAM if you're going to use VMware or any other virtualization technology.  These days, it's not tremendously expensive.

> **IHATEDLINK said:**
> 3. Can I use VMware with my existing Vista installation?
I believe so, however I cannot say firsthand.  Personally, I stay away from Vista.  Check the VMware site -- [http://www.vmware.com/](http://www.vmware.com/)

---

### Post by soccerboy on 2008-07-01
i had used vmware with Vista a few months ago.  It works (although terribly slowly) probably a RAM issue though.

---

