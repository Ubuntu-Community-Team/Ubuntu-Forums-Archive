---
title: "Wine TFTP server issues"
date: 2007-05-25
forum: General Help
---

### Post by dpsguard on 2007-05-25
I have installed Wine and then installed SolarWinds tftp server. I have made sure that there is no other tftp server package on the machine. But when I try to launch Solarwinds, I ger error that another tftp server is already running on port 69. Here is some info:

dpsguard@dpsguard-laptop:~$ dpkg -l | grep tftp
ii  tftp                                       0.17-15ubuntu1                     
Trivial file transfer protocol client
dpsguard@dpsguard-laptop:~$ 
dpsguard@dpsguard-laptop:~$ netstat -a | grep tftp
dpsguard@dpsguard-laptop:~$ 

dpsguard@dpsguard-laptop:~$ wine ~/.wine/drive_c/Program\ Files/SolarWinds/Free\ Tools/TFTP-Server.exe
Can not start tftp server. A tftp server is already running on port 69.

Clearly netstat shows there is no tftp running and there is no tftpd server package listed by dpkg -l. What else should I try to locate and stop this unwanted tftpd, so that I can use Solarwinds thru wine.

Thanks

---

### Post by dpsguard on 2007-05-27
Hi All,

Any tftp server which will not require a file to be present in tftpboot directory in order to let a tftp client to write to it? 

The only reason, I need to use Solarwinds is this as I have to download large number of files from network devices to tftp server and I do not want to always create a file of the same name and then set permissions on it before a network device will be allowed to upload its configuration file.

I can not figure out that if there is nothing running on UDP port 69, why will Solarwinds installed thru Wine will complain and stop. I have made sure by uninstalling tftpd-hpa, but I am not sure what else could be signaling Solarwinds that the port it is trying to use is already in use by another  process.

Looking forward to some assistance.

Thanks

---

