---
title: "GPG questions V2"
date: 2007-12-17
forum: General Help
---

### Post by oneadvent on 2007-12-17
Ok, so thanks to help from this forum we have 
```
find . -maxdepth 1 -type f -exec bash -c 'gpg -r jwelch -e {} && rm {}' \; 
```
to encrypt all the files in a directory, but how can I get it to decrypt all the files in the directory with a single line?

(Think shell script.)

I am going to read the man pages now, but I went through it once and didn't see it. 

Can anyone else lend some light?

---

### Post by oneadvent on 2007-12-17
Ok, I got this far, but it is still not right:
```
find *.gpg -maxdepth 1 -type f -exec bash -c 'gpg -r jwelch --decrypt-files --passphrase-file /home/jwelch/Desktop/tester/gpgfile.txt {} && rm {}' \; 
```

where I put the passkey in gpgfile.txt in the correct directory.

---

### Post by oneadvent on 2007-12-17
Actually I get this
```

jwelch@jwelch-laptop:~/Desktop/tester$ gpg -r jwelch --decrypt-files --passphrase-file /home/jwelch/Desktop/tester/gpgfile.txt gpg.txt.gpg

You need a passphrase to unlock the secret key for
user: "jwelch <oneadvent@gmail.com>"
2048-bit ELG-E key, ID 8EA75DC3, created 2007-12-17 (main key ID C593DB90)

gpg: gpg-agent is not available in this session
Enter passphrase:  
```

Which wont work in a shell script

---

