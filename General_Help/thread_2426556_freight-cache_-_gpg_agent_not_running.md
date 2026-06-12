---
title: "freight-cache - gpg agent not running"
date: 2019-09-10
forum: General Help
---

### Post by mikeaw2010 on 2019-09-10
Hello.

For starters I need to state my experience with Freight and gpg is very limited. I was asked for assistance with this matter. Basically whenever we attempt to serve our apt's via freight-cache, we are receiving an error stating that gpg-agent is not available and asks us to manually input the passphrase when it is supposed to be obtaining it from a file. The reason this is an issue is we are running freight from a script and the script does not prompt the user to enter a password causing the script to fail due to a timeout. After debugging it and running it from the host machine, we came up with this:

```

host:~$ freight-cache -p /home/host/gpg-passphrase


You need a passphrase to unlock the secret key for
user:*************
4096-bit RSA key, ID XXXXXXXX, created XXXX-XX-XX


**gpg: gpg-agent is not available in this session**
Enter passphrase: 



```

```

host:~$ gpg-agent
**gpg-agent[27264]: gpg-agent running and available**

```

```

host:~$ gpg --version
**gpg (GnuPG) 1.4.20**
Copyright (C) 2015 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.


Home: ~/.gnupg
Supported algorithms:
Pubkey: RSA, RSA-E, RSA-S, ELG-E, DSA
Cipher: IDEA, 3DES, CAST5, BLOWFISH, AES, AES192, AES256, TWOFISH,
        CAMELLIA128, CAMELLIA192, CAMELLIA256
Hash: MD5, SHA1, RIPEMD160, SHA256, SHA384, SHA512, SHA224
Compression: Uncompressed, ZIP, ZLIB, BZIP2


host:~$ gpg-agent --version
**gpg-agent (GnuPG) 2.1.11**
libgcrypt 1.6.5
Copyright (C) 2016 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.


host:~$ gpg2 --version
**gpg (GnuPG) 2.1.11**
libgcrypt 1.6.5
Copyright (C) 2016 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.


Home: ~/.gnupg
Supported algorithms:
Pubkey: RSA, ELG, DSA, ECDH, ECDSA, EDDSA
Cipher: IDEA, 3DES, CAST5, BLOWFISH, AES, AES192, AES256, TWOFISH,
        CAMELLIA128, CAMELLIA192, CAMELLIA256
Hash: SHA1, RIPEMD160, SHA256, SHA384, SHA512, SHA224
Compression: Uncompressed, ZIP, ZLIB, BZIP2

```

After some research I came to find that gpg and gpg-agent are now incompatible and you must use gpg2. The problem is, freight-cache does not seem to use gpg2.

Can I get some recommendations on how to solve this issue?

---

### Post by mikeaw2010 on 2019-09-13
Any ideas?

Also, can anyone tell me what exactly freight-cache is supposed to do?

---

