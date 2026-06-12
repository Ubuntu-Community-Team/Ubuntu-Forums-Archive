---
title: "How can I add extra disk space to RAID/LVM"
date: 2005-10-02
forum: General Help
---

### Post by raphha on 2005-10-02
Hello,
I'm not quite sure if this is the best place to ask that question, if it isn't pleas redirect me :-), otherwise please give me a hand:
I will soon have to set up a small file server. Now while trying to figure out the best way to get a fast&reliable system I ended up with a RAID5 and a LVM on top to be able to create (at least) 2 partitions. One important thing for me is to be able to add more disk space later as needed, but now I couldn't find no recipe how to do that - I could of course add another RAID5 to my volume group and then increase my logical volumes, but there I'd need at least 3 new HDs - so I wonder if I couldn't maybe just add a fifth HD to my, say, four old ones, that I used to set up the RAID-array, thus increasing the physical volume and then resize the logical volumes accordingly?
Thanks for any hints, also links to good HOWTOs would be appreciated...
kind regards,
raph

---

