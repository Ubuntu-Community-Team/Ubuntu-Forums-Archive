---
title: "Decryption using openssl - If not decrypted, I will lose this pics forever"
date: 2013-04-02
forum: General Help
---

### Post by iErika on 2013-04-02
So I'm using a Mac, unix based machine. I know this OS works the same way as Ubuntu, so I asked here anyways.

So I tried password protecting this tar.gz file. However, I can't decrypt it when I tried to. The file inside it that I compressed and archived was a .zip file.

This is the command that I typed...
```
$ openssl enc -in file.tar.gz -aes-256-cbc -e > file.tar.gz // I tried to encrypt the file this way... and I was asked to set a password of course
```

then I tried decrypting it using this command...
```
$ openssl enc -in file.tar.gz -aes-256-cbc -d > file.tar.gz
error reading input file // error had appeared.
```

any idea???
worst case scenario: I'd ask someone to decrypt this confidential pics...which I wish I don't have to...

---

### Post by Cheesemill on 2013-04-02
I think you're out of luck.

By piping the output of the encode command into the same input file that it's processing you've most likely corrupted the original file beyond any hope of recovery.
You should ***always*** redirect the output of such commands to a ***different*** file than the file being processed, for example...
```
 openssl enc -in file.tar.gz -aes-256-cbc > file.tar.gz.encrypted
```
or
```
 openssl enc -in file.tar.gz -aes-256-cbc -out file.tar.gz.encrypted
```

I think your only hope now is to restore the files from your most recent backup before you messed up.

---

### Post by iErika on 2013-04-07
omg!!! I can't believe this. Those were my only copies! Unfortunately. I have no backups.

anyways, I understand it now, thank you.

---

### Post by iErika on 2013-04-07
how can I mark this post as solved?

---

