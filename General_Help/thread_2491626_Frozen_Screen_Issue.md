---
title: "Frozen Screen Issue"
date: 2023-10-15
forum: General Help
---

### Post by exiort on 2023-10-15
Hi everyone!
I am currently using Ubuntu 22.04 and I am having frozen screen issue. The problem occurs like this. When I using laptop suddenly screen freeze and goes and infinite loop of sound that played right now. It continious until I forced shut down. When I looked dmesg I found that:
[   24.228358] [drm:nv_drm_master_set [nvidia_drm]] *ERROR* [nvidia-drm] [GPU ID 0x00000100] Failed to grab modeset ownership
This message repeated several times. I thought it would be cause of the error. I shared my detailed system info to:[COLOR=#000000][FONT=inter][https://file.io/m9Y4ctgaeAMR](https://file.io/m9Y4ctgaeAMR)[/FONT][/COLOR]

---

### Post by Autodave on 2023-10-15
First off, your link doesn't work.  So, let's try this: what nVidia driver are you using and where did you get the driver from?

---

### Post by exiort on 2023-10-16
I am sorry to hear that. How can I share this information properly? I am currently using nvidia-driver-535 which is installed from additional drivers. But I have tried other drivers from there as well.

---

