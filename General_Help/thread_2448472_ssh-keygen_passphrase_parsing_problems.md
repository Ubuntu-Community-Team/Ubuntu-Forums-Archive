---
title: "ssh-keygen passphrase parsing problems"
date: 2020-08-08
forum: General Help
---

### Post by brianbuchanan on 2020-08-08
I ran into trouble with ssh-keygen using a randomly generated passphrase.  It looks like my trouble is the "$V" character combination when entered interactively.  I've been able to reproduce it on two of my systems (and a CentOS8.1 system) and I don't quite understand what I'm doing wrong.

```
$ ssh-keygen -f ./test-key -N "1234$V" -t rsa -C "test-key"
Generating public/private rsa key pair.
Your identification has been saved in ./test-key
Your public key has been saved in ./test-key.pub
{clip}
$ ssh-keygen -p -f test-key
Enter old passphrase:
Failed to load key test-key: incorrect passphrase supplied to decrypt private key
$ ssh-keygen -p -f test-key -P "1234$V"
Key has comment 'test-key'
Enter new passphrase (empty for no passphrase):



```

I'm running Ubuntu 20.04.
```
$ uname -a
Linux veeambrs03 5.4.0-42-generic #46-Ubuntu SMP Fri Jul 10 00:24:02 UTC 2020 x86_64 x86_64 x86_64 GNU/Linux
```

---

### Post by TheFu on 2020-08-08
'$' is being interpreted by the shell as $V which is probably an empty environment variable.  If you want to use any character that gets interpreted by the shell you use there are multiple choices.

Escape the character ..... \$
Use single-quotes to wrap the entry  .....    ''
Learn the differences between using double-quote "" and single-quotes '' in a shell. 
[https://www.gnu.org/software/bash/manual/html_node/Double-Quotes.html](https://www.gnu.org/software/bash/manual/html_node/Double-Quotes.html)
[https://www.gnu.org/software/bash/manual/html_node/Single-Quotes.html](https://www.gnu.org/software/bash/manual/html_node/Single-Quotes.html)

BTW, why use rsa?  That in an old type key.  **ssh-keygen -t ed25519**

I didn't look at the rest of the options. Don't know if those are or are not valid.

And don't forget to use **ssh-copy-id** to push the public key to the other system(s) you want ssh/sftp/scp/rsync/sshfs/rdiff-backup or 50 others to have access.

---

### Post by brianbuchanan on 2020-08-08
Thank-you!  Changing to single quotes solved the problem.

The reason for rsa is just because I'm trying to create a private key that putty can use without conversion through puttygen.  I haven't solved that yet; got stuck on the passphrase.

Edit: Actually it's not Putty, I'm trying to generate a format that Veeam can use, and it only supports passphrases encrypted with formats that putty can read.

> 
Veeam Backup & Replication supports only keys whose passphrase is encrypted with algorithms supported by PuTTY:

[LIST]
[*]AES (Rijndael): 128-bit, 192-bit and 256-bit CBC or CTR (SSH-2 only)
[*]Blowfish: 128-bit CBC
[*]Triple-DES: 168-bit CBC
[/LIST]



[https://helpcenter.veeam.com/docs/backup/hyperv/credentials_manager_linux_pubkey.html?ver=100](https://helpcenter.veeam.com/docs/backup/hyperv/credentials_manager_linux_pubkey.html?ver=100)

---

