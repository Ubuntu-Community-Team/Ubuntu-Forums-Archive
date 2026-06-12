---
title: "Segfaults"
date: 2013-05-13
forum: General Help
---

### Post by pittdaydreamer on 2013-05-13
For reasons that are unknown to me (newb), my server will randomly generate segfaults when trying to execute the awk command.  For example, here is where I typed vi followed by a tab from the command line:

 vi awk: fatal error: internal error: segfault

Also, as I said, the behavior appears to be random.  It will segfault sometimes and sometimes it will execute the command without error.  I think this issue only occurs when running awk, but I will update the post if I notice this behavior with other commands.

Here is the output from uname -a

 Linux box01 3.5.0-28-generic #48~precise1-Ubuntu SMP Wed Apr 24 21:42:24 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

I would really love to get this sorted out as it's quite annoying.

Thanks!

---

### Post by sandyd on 2013-05-13
Have you tried running memtest on the machine?
It may be that the RAM has issues.

---

### Post by pittdaydreamer on 2013-05-22
I replaced the memory in this computer to no avail.  I am still receiving random segmentation faults for various commands -- host, awk, gawk, etc.  Sometimes the commands will run properly and sometimes they will generate a segmentation fault.

Is this most likely some other type of hardware fault -- CPU, motherboard, etc.?

Any ideas are greatly appreciated.

---

### Post by pittdaydreamer on 2013-05-22
Here are some errors being reported by the kernel:

[FONT=courier new]May 22 11:58:32 forensics01 kernel: [    8.930706] sshd[547] general protection ip:7ff48a2a5745 sp:7fffc0b5f2f0 error:0 in libcrypto.so.1.0.0[7ff48a1bc000+1b1000]
May 22 11:59:11 forensics01 kernel: [   47.465741] host[1682] general protection ip:7f54c0eaa745 sp:7fffc597df20 error:0 in libcrypto.so.1.0.0[7f54c0dc1000+1b1000]
May 22 11:59:16 forensics01 kernel: [   52.410640] host[1702] general protection ip:7f2b7d593745 sp:7fff1c662dd0 error:0 in libcrypto.so.1.0.0[7f2b7d4aa000+1b1000]
May 22 11:59:20 forensics01 kernel: [   56.058707] host[1725] general protection ip:7f02d43f8745 sp:7fffa9631a00 error:0 in libcrypto.so.1.0.0[7f02d430f000+1b1000]
May 22 11:59:23 forensics01 kernel: [   59.162711] host[1746] general protection ip:7f0e4cac4745 sp:7fff88d03fb0 error:0 in libcrypto.so.1.0.0[7f0e4c9db000+1b1000]
May 22 11:59:58 forensics01 kernel: [   94.697210] host[1858] general protection ip:7f36399ca745 sp:7fff702cdfa0 error:0 in libcrypto.so.1.0.0[7f36398e1000+1b1000]
May 22 12:00:01 forensics01 kernel: [   97.289134] host[1872] general protection ip:7febea7ac745 sp:7fffd202e510 error:0 in libcrypto.so.1.0.0[7febea6c3000+1b1000]
May 22 12:00:03 forensics01 kernel: [   98.849144] host[1881] general protection ip:7f074014a745 sp:7fff265c5e50 error:0 in libcrypto.so.1.0.0[7f0740061000+1b1000]


May 22 09:02:39 forensics01 kernel: [ 2621.637350] host[2222]: segfault at 80000045 ip 00007fd479de6745 sp 00007fff455ab6c0 error 4 in libcrypto.so.1.0.0[7fd479cfd000+1b1000]
May 22 11:29:23 forensics01 kernel: [  792.288845] update-mime-dat[4131]: segfault at 18a40618 ip 00007f1b6c4877b4 sp 00007fff019d5ed0 error 4 in libxml2.so.2.7.8[7f1b6c42b000+151000]
May 22 11:31:56 forensics01 kernel: [   55.763246] host[1778]: segfault at 80000045 ip 00007fe7c3e39745 sp 00007fff3caf6270 error 4 in libcrypto.so.1.0.0[7fe7c3d50000+1b1000]
May 22 11:59:10 forensics01 kernel: [   45.935952] host[1677]: segfault at 80000045 ip 00007fdfc5e4c745 sp 00007fff87dd7230 error 4 in libcrypto.so.1.0.0[7fdfc5d63000+1b1000]
May 22 12:00:00 forensics01 kernel: [   95.826278] host[1863]: segfault at 80000045 ip 00007f6007b71745 sp 00007fff90b46740 error 4 in libcrypto.so.1.0.0[7f6007a88000+1b1000][/FONT]

---

