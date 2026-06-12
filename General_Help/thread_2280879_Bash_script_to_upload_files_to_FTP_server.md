---
title: "Bash script to upload files to FTP server"
date: 2015-06-03
forum: General Help
---

### Post by jose79 on 2015-06-03
Hi everyone,

I'm trying to automatize a process to upload files to FTP server, so, I'm doing a bash script.
I've been trying with scp, but doesn't work with the password. I just have FTP acces, no SSH.

Any help will be helpful

Thank you

---

### Post by Lars Noodén on 2015-06-03
Just to be sure, do you have [SFTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) access or just [FTP](https://luxsci.com/blog/if-you-are-using-ftp-you-should-really-stop.html)?  Because if you do have SFTP, it is easily scriptable with keys and batch mode.

---

### Post by jose79 on 2015-06-03
Sftp

---

### Post by Lars Noodén on 2015-06-03
Excellent.  

First to prepare things, you can make a key pair on your client machine to use with that particular server.

```

cd ~/.ssh/
ssh-keygen -t rsa -b 2048 -f some_name_rsa -C "some notes"

```

Since you don't have SSH access, the *public* key will have to be transfered SFTP.  Connect with SFTP using your password and see if the server has the file ~/.ssh/authorized_keys in your account.  

```

ls -l
```

If it is there and non-zero size, then we have to do some other preparations, stop if that is the case.  But if the file is not there, then upload the *public* key to ~/.ssh/ using 'pu' and rename it to 'authorized_keys' using 'rename'  

Then in another terminal try connecting using the key.

```

sftp -i ~/.ssh/some_name_rsa  jose79@someserver.example.org

```

If that works, the next step will be to set up a batch file to use with the [-b option](http://manpages.ubuntu.com/manpages/trusty/en/man1/sftp.1.html).  If the 'authorized_keys' file already exists on the remote sever, then we have to first do a little juggling.

---

### Post by jose79 on 2015-06-03
Don't worry finally I've solved using public-private ssh key. Anyway, thank you for your time

---

