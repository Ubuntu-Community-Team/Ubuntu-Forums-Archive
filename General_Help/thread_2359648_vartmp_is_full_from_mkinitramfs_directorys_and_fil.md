---
title: "/var/tmp is full from mkinitramfs directorys and files with last use date = today"
date: 2017-04-26
forum: General Help
---

### Post by tezenast on 2017-04-26
Hello everyone and thanks for reading this =D


Lately, each time I boot i have a warning about /var/tmp being full so today I tried to see what I can do in order to solve this. 
I saw online that /var/tmp purpose is to containt tmp files that should have a longer life than tmp which is erased at each reboot. 
So what i did what to search for the last use of the files to see the olds ones and remove them. 
Here is the detail on what i have in my /var/tmp : 

```

ls -luh
total 216K
drwxr-xr-x 12 root     root     4,0K avril 26 10:08 mkinitramfs_0Or8fY
drwxr-xr-x 12 root     root     4,0K avril 26 10:08 mkinitramfs_5nt0hQ
drwxr-xr-x 12 root     root     4,0K avril 26 10:08 mkinitramfs_6EIaAm
drwxr-xr-x 12 root     root     4,0K avril 26 10:08 mkinitramfs_77pbRm
drwxr-xr-x 12 root     root     4,0K avril 26 10:07 mkinitramfs_7aKqgZ
drwxr-xr-x 12 root     root     4,0K avril 26 10:07 mkinitramfs_7qp1UZ
drwxr-xr-x 12 root     root     4,0K avril 26 10:07 mkinitramfs_7S6IrB
drwxr-xr-x 12 root     root     4,0K avril 26 10:07 mkinitramfs_8j6UT1
drwxr-xr-x 12 root     root     4,0K avril 26 10:08 mkinitramfs_a9HOZq
drwxr-xr-x 12 root     root     4,0K avril 26 10:08 mkinitramfs_CBpMZp
drwxr-xr-x 12 root     root     4,0K avril 26 10:07 mkinitramfs_cfsChv
drwxr-xr-x 12 root     root     4,0K avril 26 10:08 mkinitramfs_Cs1xWL
drwxr-xr-x 12 root     root     4,0K avril 26 10:08 mkinitramfs_FnHvGc
-rw-------  1 root     root        0 avril  5 04:12 mkinitramfs-FW_1tiv2c
-rw-------  1 root     root        0 avril  3 12:04 mkinitramfs-FW_4kecWc
-rw-------  1 root     root        0 févr.  8 14:07 mkinitramfs-FW_4LyHm0
-rw-------  1 root     root        0 mars   2 09:54 mkinitramfs-FW_78SooK
-rw-------  1 root     root        0 févr. 22 09:50 mkinitramfs-FW_AewEB0
-rw-------  1 root     root        0 mars   6 16:18 mkinitramfs-FW_b7ozoR
-rw-------  1 root     root        0 avril 12 09:13 mkinitramfs-FW_BvZPCe
-rw-------  1 root     root        0 févr. 16 08:58 mkinitramfs-FW_DxXxnt
-rw-------  1 root     root        0 févr.  7 09:55 mkinitramfs-FW_fRp5Rf
-rw-------  1 root     root        0 févr. 17 08:49 mkinitramfs-FW_fwLFOF
-rw-------  1 root     root        0 févr.  9 08:51 mkinitramfs-FW_iIMG8o
-rw-------  1 root     root        0 avril 25 12:23 mkinitramfs-FW_IzLWhq
-rw-------  1 root     root        0 mars   6 16:06 mkinitramfs-FW_jCbIn0
-rw-------  1 root     root        0 févr. 17 08:50 mkinitramfs-FW_jVTdg8
-rw-------  1 root     root        0 avril  7 10:16 mkinitramfs-FW_jY4zdZ
-rw-------  1 root     root        0 févr. 13 09:08 mkinitramfs-FW_LVjvQQ
-rw-------  1 root     root        0 avril  7 10:17 mkinitramfs-FW_Lz4PpN
-rw-------  1 root     root        0 avril  5 04:12 mkinitramfs-FW_nCOXuO
-rw-------  1 root     root        0 mars  14 10:54 mkinitramfs-FW_NjU1AJ
-rw-------  1 root     root        0 avril 12 09:13 mkinitramfs-FW_Nz2wFE
-rw-------  1 root     root        0 mars   8 14:53 mkinitramfs-FW_pxTAuv
-rw-------  1 root     root        0 mars   6 16:18 mkinitramfs-FW_qjlysj
-rw-------  1 root     root        0 mars  15 13:57 mkinitramfs-FW_SnJV88
-rw-------  1 root     root        0 mars   1 09:37 mkinitramfs-FW_tRrZ0B
-rw-------  1 root     root        0 mars   6 16:10 mkinitramfs-FW_Vh55Ee
-rw-------  1 root     root        0 mars   6 09:41 mkinitramfs-FW_W2ELEi
-rw-------  1 root     root        0 févr. 13 09:09 mkinitramfs-FW_w4jVzc
-rw-------  1 root     root        0 févr. 16 08:57 mkinitramfs-FW_xUMNW3
drwxr-xr-x 12 root     root     4,0K avril 26 10:07 mkinitramfs_GQ5YTP
drwxr-xr-x 12 root     root     4,0K avril 26 10:08 mkinitramfs_gqXLYN
drwxr-xr-x 12 root     root     4,0K avril 26 10:08 mkinitramfs_he7zdf
drwxr-xr-x 12 root     root     4,0K avril 26 10:07 mkinitramfs_huEs6q
drwxr-xr-x 12 root     root     4,0K avril 26 10:07 mkinitramfs_N5SWOi
drwxr-xr-x 12 root     root     4,0K avril 26 10:08 mkinitramfs_NaKZeM
drwxr-xr-x 12 root     root     4,0K avril 26 10:08 mkinitramfs_nIL9yG
-rw-------  1 root     root        0 mars   6 16:18 mkinitramfs-OL_0zFSx5
-rw-------  1 root     root        0 févr. 17 08:50 mkinitramfs-OL_17qhhq
-rw-------  1 root     root        0 avril  3 12:04 mkinitramfs-OL_1ChLGw
-rw-------  1 root     root        0 avril 12 09:13 mkinitramfs-OL_2zdd2g
-rw-------  1 root     root        0 mars   6 16:10 mkinitramfs-OL_3IYYH2
-rw-------  1 root     root        0 mars   1 09:37 mkinitramfs-OL_7ghWkf
-rw-------  1 root     root        0 févr.  8 14:07 mkinitramfs-OL_7rzfvt
-rw-------  1 root     root        0 févr. 13 09:09 mkinitramfs-OL_eHlQFe
-rw-------  1 root     root        0 avril  7 10:16 mkinitramfs-OL_er19lo
-rw-------  1 root     root        0 févr. 17 08:49 mkinitramfs-OL_EVtehU
-rw-------  1 root     root        0 mars   2 09:54 mkinitramfs-OL_fG6qQ1
-rw-------  1 root     root        0 févr. 16 08:57 mkinitramfs-OL_hTc84B
-rw-------  1 root     root        0 févr. 16 08:58 mkinitramfs-OL_Htvh0j
-rw-------  1 root     root        0 févr.  7 09:55 mkinitramfs-OL_IRtyJ9
-rw-------  1 root     root        0 avril 12 09:13 mkinitramfs-OL_Jnb5nx
-rw-------  1 root     root        0 mars  15 13:57 mkinitramfs-OL_Lx5loK
-rw-------  1 root     root        0 avril  7 10:17 mkinitramfs-OL_MutndG
-rw-------  1 root     root        0 avril 25 12:23 mkinitramfs-OL_OTKik7
-rw-------  1 root     root        0 mars  14 10:54 mkinitramfs-OL_pimjwE
-rw-------  1 root     root        0 mars   6 09:41 mkinitramfs-OL_qxiZcD
-rw-------  1 root     root        0 avril  5 04:12 mkinitramfs-OL_tT2c7F
-rw-------  1 root     root        0 avril  5 04:12 mkinitramfs-OL_TVCcqX
-rw-------  1 root     root        0 mars   8 14:53 mkinitramfs-OL_u38uDJ
-rw-------  1 root     root        0 févr. 22 09:50 mkinitramfs-OL_Ug5PgN
-rw-------  1 root     root        0 févr. 13 09:08 mkinitramfs-OL_uTpr8G
-rw-------  1 root     root        0 mars   6 16:06 mkinitramfs-OL_WgBI10
-rw-------  1 root     root        0 mars   6 16:18 mkinitramfs-OL_YSsNG7
-rw-------  1 root     root        0 févr.  9 08:51 mkinitramfs-OL_z35CZd
drwxr-xr-x 12 root     root     4,0K avril 26 10:07 mkinitramfs_Pu5slH
drwxr-xr-x 12 root     root     4,0K avril 26 10:08 mkinitramfs_QcsJgu
drwxr-xr-x 12 root     root     4,0K avril 26 10:07 mkinitramfs_QZXaDm
drwxr-xr-x 12 root     root     4,0K avril 26 10:08 mkinitramfs_SxvcGF
drwxr-xr-x 12 root     root     4,0K avril 26 10:07 mkinitramfs_VwbcPD
drwxr-xr-x 12 root     root     4,0K avril 26 10:07 mkinitramfs_W4ww6c
drwxr-xr-x 12 root     root     4,0K avril 26 10:07 mkinitramfs_xnAkNO
drwxr-xr-x 12 root     root     4,0K avril 25 12:23 mkinitramfs_Y3gEHO
drwx------  3 root     root     4,0K avril 26 10:41 systemd-private-12498a67a3454739b367ce87c74f6f38-colord.service-Jf5sOf
drwx------  3 root     root     4,0K déc.   7 08:14 systemd-private-12498a67a3454739b367ce87c74f6f38-redis-server.service-3dY8rh
drwx------  3 root     root     4,0K déc.   7 08:15 systemd-private-12498a67a3454739b367ce87c74f6f38-rtkit-daemon.service-jMhKrO
drwx------  3 root     root     4,0K déc.   6 09:32 systemd-private-32161ff705074a0f89cb9358ef3770d0-colord.service-blZUCS
drwx------  3 root     root     4,0K déc.   6 09:32 systemd-private-32161ff705074a0f89cb9358ef3770d0-redis-server.service-nQFqsX
drwx------  3 root     root     4,0K déc.   6 09:32 systemd-private-32161ff705074a0f89cb9358ef3770d0-rtkit-daemon.service-V91wqH
drwx------  3 root     root     4,0K janv. 14 19:34 systemd-private-5b0359807b3944ebaaa0a58cbc8f579e-colord.service-mulHKp
drwx------  3 root     root     4,0K janv. 14 19:34 systemd-private-5b0359807b3944ebaaa0a58cbc8f579e-redis-server.service-YMhxqG
drwx------  3 root     root     4,0K janv. 14 19:34 systemd-private-5b0359807b3944ebaaa0a58cbc8f579e-rtkit-daemon.service-IVHiFh
drwx------  3 root     root     4,0K févr. 17 12:01 systemd-private-97f4b1733f9c45f1a6385368f17409ad-colord.service-NnAJAT
drwx------  3 root     root     4,0K févr. 17 12:01 systemd-private-97f4b1733f9c45f1a6385368f17409ad-redis-server.service-hjki8W
drwx------  3 root     root     4,0K févr. 17 12:02 systemd-private-97f4b1733f9c45f1a6385368f17409ad-rtkit-daemon.service-hWvLOX
drwx------  3 root     root     4,0K avril 26 10:30 systemd-private-af1b6dbb6531469aae4dfc81c3294f2b-colord.service-ghusDA
drwx------  3 root     root     4,0K avril 26 10:30 systemd-private-af1b6dbb6531469aae4dfc81c3294f2b-redis-server.service-kFoKvT
drwx------  3 root     root     4,0K avril 26 10:31 systemd-private-af1b6dbb6531469aae4dfc81c3294f2b-rtkit-daemon.service-omdjOa
drwx------  3 root     root     4,0K mars   7 09:34 systemd-private-e46552bd44fc45ba8f0a5a59b3bb1445-colord.service-hyc88M
drwx------  3 root     root     4,0K mars   7 09:34 systemd-private-e46552bd44fc45ba8f0a5a59b3bb1445-redis-server.service-5fdvsU
drwx------  3 root     root     4,0K mars   7 09:35 systemd-private-e46552bd44fc45ba8f0a5a59b3bb1445-rtkit-daemon.service-1hWVR7
drwx------  3 root     root     4,0K mars   9 09:20 systemd-private-eb0255bde0ab44809cec2c66b2c5203b-colord.service-bgeexE
drwx------  3 root     root     4,0K mars   9 09:20 systemd-private-eb0255bde0ab44809cec2c66b2c5203b-redis-server.service-JwpHhh
drwx------  3 root     root     4,0K mars   9 09:20 systemd-private-eb0255bde0ab44809cec2c66b2c5203b-rtkit-daemon.service-7ot7p7


```

Please note that for an unknown reason when the size printed in ls -luh is equal to 4k Nautilus anouces around 130Mo for the directories. I suspect that my command does not show the size of the elements but only of the directory ? 
Using df which print the following code, it's pretty clear that my disk is full : 

```

Sys. de fichiers         blocs de 1K  Utilisé Disponible Uti% Monté sur
udev                         8150408        0    8150408   0% /dev
tmpfs                        1635120     9728    1625392   1% /run
/dev/mapper/vg00-lv_root     3997376  1175332    2595948  32% /
/dev/vg00/lv_usr            41153856 21506668   17533652  56% /usr
tmpfs                        8175596      212    8175384   1% /dev/shm
tmpfs                           5120        4       5116   1% /run/lock
tmpfs                        8175596        0    8175596   0% /sys/fs/cgroup
/dev/mapper/vg00-lv_tmp      1998672     3332    1874100   1% /tmp
/dev/mapper/vg00-lv_var      5029504  4616260     134716  98% /var
/dev/sda1                     243823   139617      87310  62% /boot
/dev/mapper/vg00-lv_data   896738848 20846636  830317456   3% /localdata
tmpfs                        1635120       56    1635064   1% /run/user/113549

```


Please note that my /boot partition in only doing 256Mo and I believe that this is linked to my issue. 
Why is it linked ?  Because I found this : [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1597661](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/1597661)
In short it's explaning that when /boot has not enough empty space, mkinitramfs uses /var/tmp

Last but not least, if you look carefully, you will see that all mkinitramfs directories has been last used today. The issue is that their size is equal 28*130Mo so it should weight around 3Go. I have nothing against the fact that mkinitramfs might use some space each  day butmay be not 3Go ?? 
For the systemd private, 4 have been modified today ( which is still around 500Mo ) but all the others are older.

I believe this is all I know about my issue. 
Now come my questions : 
- can i safely erase the old systemd even thought thoses are "systemd-private" files that i can't even see what's inside as root ?
- do you have an idee about what I could/should do for all thoses mkinitramfs files ? 

Thanks a lot to reading this post up until now =D
And thanks to anyone that have any idee of things i can try ;)

---

