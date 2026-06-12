---
title: "Compiling VSTFPD 3.0.02 on 12.04LTS"
date: 2014-08-17
forum: General Help
---

### Post by coetzeec2380 on 2014-08-17
Hi,

I am running 12.04 server edition, i have one problem with vsftpd. i used to have ver 2.3.5 , but getting users to be locked to their home directories keep giving me two types of errors . one being 500 OOPS: vsftpd: refusing to run with writable root inside chroot() issue and the other Connection attempt failed with "ECONNREFUSED - Connection refused by server".  I read through a good quantity and the guide on ubuntu regarding the setup , but to no luck will the server work correctly. If i leave the server in default states for user to log on the user is able to browse the whole system which is a bad idea for me. Reading through some more posts it seems their is a solution in the the VSFTPD 3.0.2  by adding "allow_writeable_chroot=YES" in the conf file. this does not seem to work in version 2.3.5. 

So i decided to update vsftpd to 3.0.2 on ubuntu 12.04LTS server, but when i make the application for installation i am getting the below error, i don't think it has to do with permissions as i purposely made chmod 0777.

standalone.o hash.o tcpwrap.o ipaddrparse.o access.o features.o readwrite.o opts.o ssl.o sslslave.o ptracesandbox.o ftppolicy.o sysutil.o sysdeputil.o seccompsandbox.o -Wl,-s -fPIE -pie -Wl,-z,relro -Wl,-z,now `./vsf_findlibs.sh`
sysdeputil.o: In function `vsf_sysdep_check_auth':
sysdeputil.c:(.text+0x109): undefined reference to `crypt'
sysdeputil.c:(.text+0x13a): undefined reference to `crypt'
collect2: ld returned 1 exit status
make: *** [vsftpd] Error 1
root@c2dserver:/home/vsftpd302_ub/vsftpd-3.0.2#


does anyone have a idea to solve this

Regards 
CC

---

