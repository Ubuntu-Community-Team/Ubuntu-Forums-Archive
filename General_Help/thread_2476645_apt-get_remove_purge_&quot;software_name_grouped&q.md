---
title: "apt-get remove purge &quot;software name grouped&quot; is the same result if &quot;ungrouped&quot; ?"
date: 2022-07-01
forum: General Help
---

### Post by aug7744 on 2022-07-01
Hello.
Thanks for read.
If doing
sudo apt-get purge -y vim vim-common vim-runtime vim-tiny

have the same result if doing the commands below ?

sudo apt-get purge -y vim
sudo apt-get purge -y vim-common
sudo apt-get purge -y vim-runtime
sudo apt-get purge -y vim-tiny

The same number of files will be removed in both types of purge (grouped or ungrouped) ?

Have an good night.

---

### Post by deadflowr on 2022-07-01
Yes

---

### Post by mIk3_08 on 2022-07-02
> **aug7744 said:**
> Hello.
Thanks for read.
If doing
sudo apt-get purge -y vim vim-common vim-runtime vim-tiny

have the same result if doing the commands below ?

sudo apt-get purge -y vim
sudo apt-get purge -y vim-common
sudo apt-get purge -y vim-runtime
sudo apt-get purge -y vim-tiny

The same number of files will be removed in both types of purge (grouped or ungrouped) ?

Have an good night.
As what deadflowr said, Yes it is the same.
On how to mark this thread as solve, 
Please Click the "[COLOR=#ff0000]**Solve thread**[/COLOR]" link below. Regards and cheers.

---

