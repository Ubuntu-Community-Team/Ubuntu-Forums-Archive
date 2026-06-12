---
title: "clonezilla image 24x larger than original files ?"
date: 2014-04-24
forum: General Help
---

### Post by fkkroundabout on 2014-04-24
yes i used clonezilla to clone a full hard drive, fresh ubuntu install, which was mostly one ext4 partition with approx 5 GB on it. however the clone image is 120 GB. the original hard drive is approx 300 GB.

from what i understand, clonezilla uses dd for ext4, because ext4 is not fully supported yet. so if i wrote zeros to the hard drive's free space before cloning, would the image be much smaller ? or is there a way to make the 120 GB image i have made already, smaller ?

edit: just discovered how to tar backup, may not need to worry about clonezilla

---

### Post by ajgreeny on 2014-04-24
Does clonezilla clone the whole disk or partition, including empty space?  I think it may do but have never used it, so I'm not 100% sure.

---

