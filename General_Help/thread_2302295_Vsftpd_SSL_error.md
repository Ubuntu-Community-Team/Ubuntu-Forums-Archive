---
title: "Vsftpd SSL error"
date: 2015-11-09
forum: General Help
---

### Post by gordon16 on 2015-11-09
Hello,

I have installed Vsftpd and forward port 21 and passive ports in the firewall (pfsense). Everything works great, but now I have enabled SSL encryption,
and I`m abel to connect to thes server (most of the time, some unstable for some reason?), but when I try to transfer it will not start and after a while I
got error "Data Socket Error: Connection timed out" "Transfer Failed".

Must I portward some port for SSL also? 

Copy / Past conf file:
ssl_enable=YES
allow_anon_ssl=NO
force_local_data_ssl=NO
force_local_logins_ssl=NO
ssl_tlsv1=YES
ssl_sslv2=NO
ssl_sslv3=NO

pasv_enable=YES
pasv_max_port=5980
pasv_min_port=5950

---

