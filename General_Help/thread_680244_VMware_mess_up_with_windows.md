---
title: "VMware mess up with windows"
date: 2008-01-27
forum: General Help
---

### Post by tempril on 2008-01-27
Hi all,
I have been using Ubuntu now for a few months and before that Mint linux, so I am really just a noob.
I setup VMware to run my windows partition as a VM.  That all seemed to work for a while.  The problem started when I didn't shut down the VM of windows, just suspended the session.  No problem.
I then wanted to output to my TV to watch a movie, so i ran windows, with an open suspended session of the same install of windows.  When I went to play windows again in the VM it just sat there with the grassy knoll after the resume of the suspend.  After a reboot into windows os all I got was a black screen after Grub, and no hard drive activity.  A reboot into Ubuntu did not even mount my sda1 anymore, and a manual mount got me this -

"Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sda2            5100        5221      979965   82  Linux swap / Solaris
/dev/sda3            5222        9729    36210510   83  Linux
guru@ORAC:~$ sudo mount /dev/sda1 /media/sda1
Trying to read non-allocated mft records (21012 > 10083): Illegal seek
ntfs_mft_record_read failed: Illegal seek
Failed to mount '/dev/sda1': Illegal seek
guru@ORAC:~$ sudo mount /dev/sda1 /media/sda1 -t ntfs
Trying to read non-allocated mft records (21012 > 10083): Illegal seek
ntfs_mft_record_read failed: Illegal seek
Failed to mount '/dev/sda1': Illegal seek
guru@ORAC:~$ "

When I go into Partition Edtior, i get the error in the attached s'cap

I have googled the errors extensively and have not found any exact results.

I had no idea where the best place to post this error in the forums was, so I thought general would be fine.

I would not like to reinstall windows again, any help is always good.
Thanks all

---

### Post by tempril on 2008-02-16
I fixed it.  I had to reinstall windoze again because the partition had died.

But now I seem to have my old 'sda1' which is empty, and 'disk' (my windows partition) that I have to enter my admin password to access it.

Can anyone tell me what is going on and how to fix it?

Thanks

---

