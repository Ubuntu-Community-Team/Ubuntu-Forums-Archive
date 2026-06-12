---
title: "vsftpd: pam_smbpass.so is missing"
date: 2013-05-07
forum: General Help
---

### Post by GrayBear on 2013-05-07
Hello all,
I updated the system to 13.04 64 bit (from 12.10).
Now I can't log in with FTP. I checked /var/log/auth.log and it says:
May  7 22:50:20 ubuntu vsftpd: PAM unable to dlopen(pam_smbpass.so): /lib/security/pam_smbpass.so: cannot open shared object file: No such file or directory
May  7 22:50:20 ubuntu vsftpd: PAM adding faulty module: pam_smbpass.so
May  7 22:50:20 ubuntu vsftpd: PAM audit_log_acct_message() failed: Operation not permitted

I did:
```
apt-file search pam_smbpass.so
```
and i get:
```
libpam-smbpass: /lib/x86_64-linux-gnu/security/pam_smbpass.so
```

then i did:
```
apt-get remove libpam-smbpass
apt-get install libpam-smbpass
```

but FTP still doesn't work

There is an old bug about the same (or similar) issue back in 2008 : [https://bugs.launchpad.net/ubuntu/+source/pam/+bug/216990](https://bugs.launchpad.net/ubuntu/+source/pam/+bug/216990)
[http://ubuntuforums.org/showthread.php?t=770724](http://ubuntuforums.org/showthread.php?t=770724)

But still I could not figure how to solve it.
Any idea what can I do?

thanks

---

### Post by GrayBear on 2013-05-10
I found the solution (3 steps)!

I applied [the advice given here]("http://www.howtoforge.com/forums/showthread.php?t=22742"):
```
In /etc/pam.d/common-auth and /etc/pam.d/common-password comment out the lines that have pam_smbpass.so in them. 
```

then I got another error (auth.log):
```
May 10 10:22:16 ubuntu vsftpd: PAM audit_log_acct_message() failed: Operation not permitted
```

then I applied [the solution posted on launchpad]("https://bugs.launchpad.net/ubuntu/+source/vsftpd/+bug/1160372"): (see messages #25, #26 and #27 - Vincent DAVY (vincentdavy) wrote on 2013-05-01)

```
Download the patched version of vsftpd:
https://bugs.launchpad.net/ubuntu/+source/vsftpd/+bug/1160372/+attachment/3661388/+files/vsftpd_3.0.2-1ubuntu1_amd64_patched.deb
sudo apt-get remove vsftpd
sudo dpkg -i vsftpd_3.0.2-1ubuntu1_amd64_patched.deb
```

and then I got another error when connecting to FTP:
```
vsftpd: refusing to run with writable root inside chroot()
```

so I had to apply [the solution posted here]("http://askubuntu.com/questions/239239/ubuntu-12-04-500-oops-vsftpd-refusing-to-run-with-writable-root-inside-chroot"):
```
add thee following line to /etc/vsftpd.conf:
allow_writeable_chroot=YES
```

---

