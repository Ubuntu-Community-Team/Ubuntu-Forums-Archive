---
title: "Xrdp not working - Ubuntu 22.04"
date: 2023-04-19
forum: General Help
---

### Post by michael351 on 2023-04-19
It use to work .....

I have 22.04 installed and xrdp configured. Somewhere in the updating process, xrdp broke.
I tend to access this Ubuntu computer from my windows 10 desktop. I would initiate an xrdp session and log in. Lately, this no longer works
The session seems to start, the screen goes from green to black just before loading the desktop, but not it dies. The session and xrdp window disappears.
I can login in using Putty and the log shows:


> 2:26 PM

[ERROR] sesman_main_loop: trans_check_wait_objs failed, removing transxrdp-sesman
2:26 PM
[ERROR] sesman_data_in: scp_process_msg failedxrdp-sesman
2:26 PM
[ERROR] Sending [ITU T.125] DisconnectProviderUltimatum failedxrdp
2:26 PM
[ERROR] xrdp_iso_send: trans_write_copy_s failedxrdp
2:26 PM
[ERROR] xrdp_process_main_loop: libxrdp_process_incoming failedxrdp
2:26 PM
[ERROR] xrdp_rdp_incoming: xrdp_sec_incoming failedxrdp
2:26 PM
[ERROR] xrdp_sec_incoming: xrdp_mcs_incoming failedxrdp
2:26 PM
[ERROR] [MCS Connection Sequence] receive connection request failedxrdp
2:26 PM
[ERROR] Processing [ITU-T T.125] Connect-Initial failedxrdp
2:26 PM
[ERROR] libxrdp_force_read: header read errorxrdp
2:26 PM
[ERROR] SSL_read: I/O error

Any help appreciated! Thanks

---

### Post by michael351 on 2023-04-20
I think it's fixed. All I did was startXfce instead of Gnome. I have no idea why that worked, but I can get a remote desktop connection and display now.

---

