---
title: "Help needed to resize ext4 file system to &gt; 16TB in mythbuntu 14.04"
date: 2017-06-11
forum: General Help
---

### Post by rramesh2 on 2017-06-11
Hi,

 I have mythbuntu 14.04.5 LTS release with kernel 3.13.0. I have  e2fsprogs version 1.42.9. With this, is it possible to resize my ext4  RAID6 array beyond 16TB limit?

  I googled and tried everything that seem to be available. First I  simply tried resize2fs and go the error "resize2fs: New size too large  to be expressed in 32 bits". After that I did "tune2fs -O  extents,uninit_bg,dir_index /dev/md0" as suggested in many articles. I  still have the same error. More reading revealed that I need to make  ext4 to use 48bit block addressing or some such thing with -O 64bit  while creating the file system. This really does not help as I already  have the file system and I am not creating one. However, the same  article mentioned that the file system becomes unsupported in older  kernel and by older release of e2fsprogs. So, I am not sure if my system  can handle the changes. Can some one knowledgeable explain to me if I  really need to upgrade my ubuntu release before I see all of the 24TB in  my /dev/md0? If it is possible with the release I have by upgrading  packages, please help me decipher the steps.

Thanks
Ramesh

---

### Post by Irihapeti on 2017-06-11
I've removed a duplicate post in another forum. Please don't make multiple posts on the same issue. It causes confusion and dilutes community effort.
Thanks.

---

### Post by rramesh2 on 2017-06-11
Thanks for deleting the duplicate. Soon after I posted there, I was told to post here as that was supposed to be chat and this is supposed to be for technical questions. So, I did. I did not know how to move or delete the old post. So, I thought it is something only admin can do. 

Ramesh

---

### Post by Irihapeti on 2017-06-14
Sorry, I've only just now seen your post.

You can use the Report Post button to ask a staff member to move the post for you. It's not just for reporting spam or offensive posts.

---

