---
title: "Automatically mount Veracrypt Windows partition and link to folders"
date: 2022-04-19
forum: General Help
---

### Post by Monsuco on 2022-04-19
I have a dual boot laptop. When 22.04 LTS comes out I plan to upgrade Ubuntu.

I currently use LUKS to encrypt the Linux partition. I would like to use Veracrypt to encrypt the Windows partition and then have Linux set up to automatically mount the Windows partition at startup every time I boot into Linux. I would also like to use links to then map some folders to other folders. For example, mapping C:\Users\monsuco\Documents to /home/monsuco/Documents. 

How would I set up Veracrypt to automatically mount the Windows partition?

If I want to map the folders like that would I use symlinks or hard links? Naturally the Windows directory would be using NTFS and Linux would be using Ext4.

---

### Post by Monsuco on 2022-04-30
Bump. I really am curious how to do this.

---

