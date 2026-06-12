---
title: "When can we switch from OEM Kernel to generic or HWE"
date: 2022-01-14
forum: General Help
---

### Post by LuddDjur on 2022-01-14
To summarize the issue: We currently deploy new hardware models to our users with a oem kernel  release to enable all hardware features. But currently it is unclear  when we might switch (back) to a generic / hwe kernel release. As we  want to have not that much diversity on the currently used kernels  within all of our machines (~2500)


 I understand the difference between oem and hwe kernels. But how can I  see that a particular driver is now available in generic/hwe so we can  switch those machines to the generic ones?


 Example: we currently have some systems like Dell Precision 5560 or  XPS 9310 which required the 20.04 OEM Kernel linux-image-oem-20.04b  which is currently the 5.10.0.1052.54 but there are already newer oem  kernels (20.04c and 20.04d) and also HWE kernels that are a newer kernel  release. E.g. linux-image-generic-hwe-20.04 which current version is  5.11.0.43.47~20.04.21


 So basic question: if there is a generic / hwe kernel with a greater  version number than the currently installed oem kernel - how can we be  sure that the drivers/code was already included into the generic kernel  and all hardware features stay operational if we switch?
 
Unfortunately I neither found a documentation on that process published by Ubuntu/Canonical nor by anybody else having an insight on this.

     

I appreciate any answer that gives some more insights.

---

