---
title: "UEFI Grub boot issues, wrong TFTP Path"
date: 2017-07-05
forum: General Help
---

### Post by vsarin1979 on 2017-07-05
I am trying to PXE boot Dell Alienware PC with following setting RAID-> UEFI-> Non Secure
[FONT=inherit]I downloaded grubnetx64.efi from the site below.[/FONT]
[FONT=inherit][http://archive.ubuntu.com/ubuntu/dists/xenial-updates/main/uefi/grub2-amd64/current/](http://archive.ubuntu.com/ubuntu/dists/xenial-updates/main/uefi/grub2-amd64/current/)[/FONT]
[FONT=inherit]I am able to successfully download this file and after this I am not able to download the next files. It seems the tftp path asked after this boot file is incorrect.[/FONT]
[FONT=inherit]Jul 4 12:52:45 SDIN-SWT-AT-27 tftpd[28654]: tftpd: trying to get file: grubnetx64.efi Jul 4 12:52:45 SDIN-SWT-AT-27 tftpd[28654]: tftpd: serving file from /tftpboot Jul 4 12:53:39 SDIN-SWT-AT-27 tftpd[28658]: tftpd: trying to get file: grubnetx64.efi Jul 4 12:53:39 SDIN-SWT-AT-27 tftpd[28658]: tftpd: serving file from /tftpboot Jul 4 12:53:40 SDIN-SWT-AT-27 tftpd[28660]: tftpd: trying to get file: /grub/x86_64-efi/command.lst Jul 4 12:53:40 SDIN-SWT-AT-27 tftpd[28662]: tftpd: trying to get file: /grub/x86_64-efi/fs.lst Jul 4 12:53:40 SDIN-SWT-AT-27 tftpd[28664]: tftpd: trying to get file: /grub/x86_64-efi/crypto.lst Jul 4 12:53:40 SDIN-SWT-AT-27 tftpd[28666]: tftpd: trying to get file: /grub/x86_64-efi/terminal.lst Jul 4 12:53:40 SDIN-SWT-AT-27 tftpd[28668]: tftpd: trying to get file: /grub/grub.cfg[/FONT]
[FONT=inherit]The path should be grub/grub.cfg. This is not coming.[/FONT]
[FONT=inherit]I have grub directory in /tftpboot[/FONT]
[FONT=inherit]root@SDIN-SWT-AT-27:/var/log# cd /tftpboot/ root@SDIN-SWT-AT-27:/tftpboot# ls -lrt grub total 8 drwxrwxrwx 2 nobody root 4096 Jul 4 13:13 x86_64-efi -rwxrwxrwx 1 nobody root 168 Jul 4 19:11 grub.cfg root@SDIN-SWT-AT-27:/tftpboot#[/FONT]
[FONT=inherit]My tftp file looks like this.[/FONT]
[FONT=inherit]cat /etc/xinetd.d/tftp service tftp { protocol = udp port = 69 socket_type = dgram wait = yes user = nobody server = /usr/sbin/in.tftpd[/FONT]
server_args = /tftpboot

[FONT=inherit]serverargs = /tftpboot disable = no }[/FONT]
[FONT=inherit]Please help if any one solution to this problem.[/FONT]

---

