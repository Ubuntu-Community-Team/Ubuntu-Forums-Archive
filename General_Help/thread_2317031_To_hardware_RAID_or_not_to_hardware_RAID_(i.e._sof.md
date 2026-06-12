---
title: "To hardware RAID or not to hardware RAID (i.e. software)?"
date: 2016-03-12
forum: General Help
---

### Post by David_Partridge on 2016-03-12
The Adaptec ASR-51245 RAID card turned up and I've got the following attached:

SAS 4TB
SAS 4TB
SATA 750GB
[SATA 500GB]("http://www.tesco.com/direct/-/294-1003.prd")

I'm thinking to create one RAID1 from the two 4TB drives,  and another  combining the two SATA drives (as 500GB each), and then join then using  LVM.

So should I:

a) Set up the drives as just JBOD and use software RAID (Ubuntu 14.04 LTS Server), or

b) Use the card to configure the two RAID1 arrays ?

the hardware is an Intel Atom 525 with 4GB.

I'm leaning towards hardware, but am open to good reasons for not doing so.

Thanks
Dave

---

### Post by SeijiSensei on 2016-03-13
I'd take the hardware route myself, especially with a weaker processor like an Atom.  I'd probably start with the two 4GB drives and see how that works.  If you run "lsmod" do you see the aacraid driver loaded?

---

### Post by David_Partridge on 2016-03-13
Yes aacraid is loaded OK.  Thanks.

Any more thoughts from other members welcome.

Dave

---

### Post by David_Partridge on 2016-03-13
I did some tests with both software and hardware - using software raid, CPU loading was 40-50% with a moderate write workload.  Using hardware raid the CPU load was minimal.

So in this case hardware raid won.

Dave

---

