---
title: "User has full access with FTP, limited access with SFTP"
date: 2014-10-24
forum: General Help
---

### Post by Vaindil on 2014-10-24
*Original post here, feel to reply at either/both locations: [http://askubuntu.com/questions/539497/user-has-full-access-with-ftp-limited-access-with-sftp](http://askubuntu.com/questions/539497/user-has-full-access-with-ftp-limited-access-with-sftp)*

I'm running Ubuntu Server 14.04, and I followed [these instructions]("https://www.linode.com/docs/tools-reference/tools/limiting-access-with-sftp-jails-on-debian-and-ubuntu") to set up a user account that should be limited to its own home directory. The problem, however, is that FTP access is still allowed for the user account and when the account connects via FTP it has full view access to the entire filesystem. When the user uses SFTP, access is properly limited to the user's home directory. How do I correct this to block FTP access entirely? (Note: SSH access is blocked as it should be. The PuTTY window simply closes when the user tries to log in, no message is displayed or anything.)

Also, I want this user to be able to edit a subdomain on my server (apache2). I have a symlink set up pointing from /home/user/index to /var/www/subdomain, the symlink is owned by the www-data group (of which the user is a member), and the subdomain directory and all files are also owned by www-data, but the user cannot access the symlinked directory via SFTP. How do I make this all work together properly?

---

### Post by pqwoerituytrueiwoq on 2014-10-24
a quick fix would be to use a firewall to block port #22 (ftp) while SFTP uses port #23
edit: opps got my port numbers mixed up sorry

---

### Post by Lars Noodén on 2014-10-24
> **Vaindil said:**
> I'm running Ubuntu Server 14.04, and I followed [these instructions]("https://www.linode.com/docs/tools-reference/tools/limiting-access-with-sftp-jails-on-debian-and-ubuntu") to set up a user account that should be limited to its own home directory. The problem, however, is that FTP access is still allowed for the user account and when the account connects via FTP it has full view access to the entire filesystem. When the user uses SFTP, access is properly limited to the user's home directory. How do I correct this to block FTP access entirely? (Note: SSH access is blocked as it should be. The PuTTY window simply closes when the user tries to log in, no message is displayed or anything.)

If you have SSH and SFTP behaving the way you like, then you probably ought to [uninstall FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp).  It is not needed and is unsafe and the correct way is to remove it.  

About the firewall, [port 22](https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.txt) is for SSH and SFTP, as SFTP works over SSH.  But since you've configured your SSH server (openssh-server) to not allow shell access, then that is set.  So for SFTP access, port 22 incoming should be allowed.

---

### Post by Vaindil on 2014-10-24
> **Lars Noodén said:**
> If you have SSH and SFTP behaving the way you like, then you probably ought to [uninstall FTP]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp").  It is not needed and is unsafe and the correct way is to remove it.  

About the firewall, [port 22]("https://www.iana.org/assignments/service-names-port-numbers/service-names-port-numbers.txt") is for SSH and SFTP, as SFTP works over SSH.  But since you've configured your SSH server (openssh-server) to not allow shell access, then that is set.  So for SFTP access, port 22 incoming should be allowed.
Ah, okay, that makes sense. So SFTP is actually handled by OpenSSH, not vsftpd? I would uninstall vsftpd entirely to uninstall FTP? That sounds perfect.

(Not necessarily directed to you now, just a general statement:) My other question is still unanswered though (which is fine, I only posted 45 minutes ago). How would I go about fixing the problem with the SFTP user not being able to access the symlinked directory?

---

### Post by Lars Noodén on 2014-10-24
> **Vaindil said:**
> Also, I want this user to be able to edit a subdomain on my server (apache2). I have a symlink set up pointing from /home/user/index to /var/www/subdomain, the symlink is owned by the www-data group (of which the user is a member), and the subdomain directory and all files are also owned by www-data, but the user cannot access the symlinked directory via SFTP. How do I make this all work together properly?

Ok.  First, usually nothing in the /var/www hierarchy should be owned by www-data, except in a few unusual circumstances.  The purpose of www-data is to provide a user for Apache2 to run under that *can't* write to anything.  That's to contain damage in case something should go wrong with access otherwise, especially with PHP or other scripts.  About the symlink, the target of the symlink is outside the chroot, so it cannot be read.  You could do what you are aiming for with [mount](http://manpages.ubuntu.com/manpages/utopic/en/man8/mount.8.html)

```

sudo mkdir /home/user/subdomain/
sudo mount --bind /var/www/subdomain/ /home/user/subdomain/

```

That will put a folder "subdomain" in the one user's home directory and in reality it is /var/www/subdomain

That mount won't survive a reboot.  I'm not sure what to put in fstab to ensure that it survives a reboot, but the above gives you an idea.

---

### Post by Vaindil on 2014-10-30
Ah, perfect. I implemented this when you posted, just completely forgot to come back and thank you!

I used fstab, the line to be added is ```
/var/www/subdomain    /home/user/index    none  0 0
```

Thank you again for your help, I greatly appreciate it!

---

