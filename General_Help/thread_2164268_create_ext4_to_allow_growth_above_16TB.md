---
title: "create ext4 to allow growth above 16TB"
date: 2013-07-30
forum: General Help
---

### Post by joerg_ac on 2013-07-30
Hi,

Recently there were a lot of discussions about using ext4 above 16TB. I understand that an ext4 that was crated below 16TB cannot be resized to above 16TB because the addressing used when the filesystem was created was too small and longer addresses are needed for operation above 16TB. 

Is it possible to enforce the usage of long addresses already at creation of an ext4 filesystem even if it is created with a size below 16TB? Would in that case resizng across the 16TB border work?

I am running Ubuntu 13.04 with the respective Kernel 3.8.

I ask, because I want to create a RAID array that will still be smaller than 16TB at creation but I know that I will sooner or later extend beyond 16TB. And I would like to be able to resizing the Filesystem rather than being forced to delete and re-create it.

best regards, Jörg

---

### Post by launchpad-washuu on 2013-07-31
[quote=EXT4 Wiki]
The code to create file systems bigger than 16 TiB is, at the time of  writing this article, not in any stable release of e2fsprogs. It will be  in future releases.[/quote]
The above was posted in April this year ([linky]("https://ext4.wiki.kernel.org/index.php/Ext4_Howto"))

---

### Post by joerg_ac on 2013-07-31
Hi,

Thanks for the warning. I read this already and a lot of other articles before asking this question here. My impression is that the code was very unstable last year, but it has stabilized a lot in the meantime. 
However, even if it is unstable I would like know if and how it would work. What are the relevant commands and options to be used in order to create an ext4 filesystem below 16TB that can be resized across the 16TB border.

best regards, Jörg

---

