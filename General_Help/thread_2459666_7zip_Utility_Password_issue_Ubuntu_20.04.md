---
title: "7zip Utility Password issue Ubuntu 20.04"
date: 2021-03-23
forum: General Help
---

### Post by lordgallen on 2021-03-23
Downloaded 7zip from Ubuntu repositories. Files add to archive, however password won't set with -p switch even after entering and verifying password at prompts. Able to extract files without password. 

Example:

```
marbu@anastacia:~/Documents$ 7z a -p test.7z 2fa


7-Zip [64] 16.02 : Copyright (c) 1999-2016 Igor Pavlov : 2016-05-21
p7zip Version 16.02 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,64 bits,8 CPUs Intel(R) Core(TM) i7-10510U CPU @ 1.80GHz (806EC),ASM,AES-NI)


Scanning the drive:
1 file, 0 bytes


Creating archive: test.7z


Items to compress: 1




Enter password (will not be echoed):
Verify password (will not be echoed) :
    
Files read from disk: 0
Archive size: 82 bytes (1 KiB)
Everything is Ok
marbu@anastacia:~/Documents$
```

---

### Post by spjackson on 2021-03-24
> **lordgallen said:**
> 
```
marbu@anastacia:~/Documents$ 7z a -p test.7z 2fa


7-Zip [64] 16.02 : Copyright (c) 1999-2016 Igor Pavlov : 2016-05-21
p7zip Version 16.02 (locale=en_US.UTF-8,Utf16=on,HugeFiles=on,64 bits,8 CPUs Intel(R) Core(TM) i7-10510U CPU @ 1.80GHz (806EC),ASM,AES-NI)


Scanning the drive:
1 file, 0 bytes



```
Encryption of a 0 byte file is er... special. Nothing encrypts to nothing. If you repeat the test with a file whose size is greater than 0 you will need to enter the password to extract it.

Note that by default, the table of contents for the archive is not encrypted so you can list the contents without the password. If you encrypt the table of contents too using the -mhe flag, then you will need the password to list the contents and would also need the password to extract your 0 byte file.

---

### Post by lordgallen on 2021-03-24
> **spjackson said:**
> Encryption of a 0 byte file is er... special. Nothing encrypts to nothing. If you repeat the test with a file whose size is greater than 0 you will need to enter the password to extract it.

Note that by default, the table of contents for the archive is not encrypted so you can list the contents without the password. If you encrypt the table of contents too using the -mhe flag, then you will need the password to list the contents and would also need the password to extract your 0 byte file.


Thank-You! very much for replying, I will take a close look and report back.

UPDATE: O.K. that worked! thanks again for being astute!

---

