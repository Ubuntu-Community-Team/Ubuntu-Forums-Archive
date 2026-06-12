---
title: "Downgrading from 22.04 LTS to 20.04 LTS. Any special issues to watch for?"
date: 2022-11-13
forum: General Help
---

### Post by ne29914 on 2022-11-13
Setup:
/ 30 GB
/home 400+ GB

I'll only be manipulating / by formating and doing a new install of 20.04.3 LTS.
Is there anything special to look out for? I'm mainly concerned with the hidden configuration files in $HOME, but perhaps also elsewhere on the /home partition.

TIA.

---

### Post by Raging_Cascadoo on 2022-11-13
I have never done a downgrade before but what I suggest is when performing the 20.04 installation, make sure to uncheck the format option when adding the /home partition so that it will remain untouched for the installation. As an additional measure, you should probably back up your data on /home somewhere else before the installation.

---

### Post by Impavidus on 2022-11-14
Your configuration files in your home directory that have been used (more specifically, written) under 22.04, along with any modified documents, will use the formats of the versions of software used on 22.04. This may be different from the versions on 20.04 and in some cases the software on 20.04 may fail to process these files.

---

### Post by ne29914 on 2022-11-14
All went well.
The downgrade went without a hitch, the most difficult part was getting the old UUIDs set right.
A 20.04.2 install and a Timeshift restore of an old 20.04 image, and everything is fine.
My laptop now works perfectly again, including all the stuff that 22.04 broke (audio, screen brightness, wireless etc.).
Support or no support, I'll stay with 20.04 until 22.04 gets its act together finally.

Thanks.

---

### Post by Ars_Ivci on 2022-11-14
> **ne29914 said:**
> Setup:
/ 30 GB
/home 400+ GB

I'll only be manipulating / by formating and doing a new install of 20.04.3 LTS.
Is there anything special to look out for? I'm mainly concerned with the hidden configuration files in $HOME, but perhaps also elsewhere on the /home partition.

TIA.

It's best to create a new user at install time. Your old user files at home will be kept under /home/old_user and you'll have a clean slate under /home/new_user. You can then move all your files to new_user. Two issues: firefox and thunderbird. FF is easy: create a FF account, then sync. Thunderbird could be tricky, though; if 20.04 uses the same version with 22.04, copying the .thunderbird file will suffice. If there is a version mismatch, I do not know how to do it.

---

