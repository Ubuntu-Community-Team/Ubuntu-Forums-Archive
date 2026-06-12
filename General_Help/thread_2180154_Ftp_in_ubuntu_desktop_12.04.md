---
title: "Ftp in ubuntu desktop 12.04"
date: 2013-10-11
forum: General Help
---

### Post by Chrismallia on 2013-10-11
Hi friends forgive me for a silly question but I am new to linux and I am trying to convert some file/media servers from windows to Ubuntu,  I am still testing on a test machine if I manage to get it as I wish I will be installing ubuntu in my server and installing it for people I know, I already got serviio media server working and smb share working, now I kneed ftp server to transfer files over the internet but here is the problem I am having I would like to have a ftp server that I can jail the user to his directory and also give him a directory from a second internal disc I have plugged in, not from the c drive, I tried proftpd but the users I create in it  do not show up in the I manage to connect fine but in proftd it does not list what users I have for some reason, so I am stuck, Thank you in advance.

---

### Post by TheFu on 2013-10-11
Sorry, no answer to your issue, but [this might help]("http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp") with other important considerations.

---

### Post by Chrismallia on 2013-10-12
so your saying in Ubuntu you can't create a simple ftp server that jails the user to his folder  and give him a folder from a second drive instead of c:?

---

### Post by Lars Noodén on 2013-10-12
FTP would be the wrong way to go about it becaue even in a jail, the username, password and data would all be transfered unencrypted in addition to being non-simple to implement.  If you are doing uploads, you almost certainly want SFTP instead.  Also, SFTP is far, far easier to chroot.  SFTP is built into the package openssh-server.

---

### Post by Chrismallia on 2013-10-12
Thanks you right about that. is there maybe  a tutorial on this I am still new so thanks for all help ant tips. and btw in sftp will I be able to give a folder in my second drive?

---

### Post by TheFu on 2013-10-12
> **Chrismallia said:**
> so your saying in Ubuntu you can't create a simple ftp server that jails the user to his folder  and give him a folder from a second drive instead of c:?

Not at all.  i'm saying that most people shouldn't use FTP at all AND that I don't use plain FTP, so do not know how to do what you seek. I have setup a jailed sftp server in the past, but not for regular FTP.

The location of the jail doesn't matter - any disk can be used if file and user permissions support it.  This link [http://askubuntu.com/questions/93411/simplest-easy-way-to-jail-users](http://askubuntu.com/questions/93411/simplest-easy-way-to-jail-users) seems to have good information for jailing both plain and sftp.

There might be a good ftp howto on the ubuntu.com site too.  Just be certain to know which of the FTP servers you are using and follow steps for that specific tool - I think there are 3+ popular ones. Also, 3 of these have had back doors added to the source code previously, which were later discovered and corrected. Be as careful as you can.

Again, sorry that I don't know the answer to your specific question.

---

### Post by Lars Noodén on 2013-10-12
Plain SFTP (highly secure) is easy to set up.  All you have to do is install the package openssh-server.  SFTP comes along for the ride.

If you want to restrict SFTP access for a group of users to a specific directory, such as the one drive you mention, then look at the second example here:
[http://www.howtoforge.com/setting-up-sftp-in-a-hurry-for-file-uploads](http://www.howtoforge.com/setting-up-sftp-in-a-hurry-for-file-uploads)

It's all about setting the [ChrootDirectory](http://manpages.ubuntu.com/manpages/raring/en/man5/sshd_config.5.html) to where you want them to go.  One special thing is that the directory that is the target of the chroot must be owned by root and not writable by anyone else.

---

