---
title: "FTP Server Recommendations?"
date: 2017-02-26
forum: General Help
---

### Post by Zafaron on 2017-02-26
Hi, I'm sortof a linux newbie so bear with me please.  I am wondering if there are any ftp servers which allow read only or read/write directory access?  I need to allow a small number of users to read files from multiple directories that they might not have permission to write to.  Ideally it would be ftp only access and not linux shell access.  Running Ubuntu 16.04.something

The read only directory access is the main feature needed.


Thanks for any input.

---

### Post by TheFu on 2017-02-26
Welcome to the forums.

a) Don't use plain FTP. Use sftp instead.
b) Setup sftp with a chroot. openssh-server is the package.  
c) There are chroot how-tos for sftp.

If you can, have the users generate ssh-keys and make their access key-based, not passwords.  In the security game, passwords are the weakest part, by far.

And if you care about security, don't let brute force attacks happen. Block them after a few attempts for a day or a month or a year. denyhosts or fail2ban can do that.

---

### Post by HermanAB on 2017-02-26
I recommend vsftpd.  I happen to be busy writing a little guide on it.  See my blog web site, it will be at the top in a few hours.

Everyone and his dog will tell you not to use FTP, since it is not secure.  That is not a problem if your data is on a LAN and your users are using Windows, since then everything is insecure anyway.  If the reason for using FTP is simplicity and that it works transparently with Windows, then go ahead.

---

### Post by cariboo on 2017-02-26
Moved double post.

---

