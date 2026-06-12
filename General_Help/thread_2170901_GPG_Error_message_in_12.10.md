---
title: "GPG Error message in 12.10"
date: 2013-08-28
forum: General Help
---

### Post by cluelesswonder on 2013-08-28
Hello there!
An error message spontaneously showed up. When I ran apt-get update I got this (I'm just including the error part)
```
Get:10 http://ca.archive.ubuntu.com quantal-updates/multiverse i386 Packages [11.2 kB]
Hit http://ca.archive.ubuntu.com quantal-updates/main Translation-en           
Hit http://ca.archive.ubuntu.com quantal-updates/multiverse Translation-en     
Hit http://ca.archive.ubuntu.com quantal-updates/restricted Translation-en     
Hit http://ca.archive.ubuntu.com quantal-updates/universe Translation-en       
Hit http://ca.archive.ubuntu.com quantal-backports/main Sources
Hit http://ca.archive.ubuntu.com quantal-backports/restricted Sources
Hit http://ca.archive.ubuntu.com quantal-backports/universe Sources
Hit http://ca.archive.ubuntu.com quantal-backports/multiverse Sources
Hit http://ca.archive.ubuntu.com quantal-backports/main i386 Packages
Hit http://ca.archive.ubuntu.com quantal-backports/restricted i386 Packages
Hit http://ca.archive.ubuntu.com quantal-backports/universe i386 Packages
Hit http://ca.archive.ubuntu.com quantal-backports/multiverse i386 Packages
Hit http://ca.archive.ubuntu.com quantal-backports/main Translation-en
Hit http://ca.archive.ubuntu.com quantal-backports/multiverse Translation-en
Hit http://ca.archive.ubuntu.com quantal-backports/restricted Translation-en
Hit http://ca.archive.ubuntu.com quantal-backports/universe Translation-en
Ign http://ca.archive.ubuntu.com quantal/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com quantal/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com quantal-updates/main Translation-en_CA
Ign http://ca.archive.ubuntu.com quantal-updates/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com quantal-updates/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com quantal-updates/universe Translation-en_CA
Ign http://ca.archive.ubuntu.com quantal-backports/main Translation-en_CA
Ign http://ca.archive.ubuntu.com quantal-backports/multiverse Translation-en_CA
Ign http://ca.archive.ubuntu.com quantal-backports/restricted Translation-en_CA
Ign http://ca.archive.ubuntu.com quantal-backports/universe Translation-en_CA
Fetched 754 kB in 5min 4s (2,472 B/s)
Reading package lists... Error!
W: GPG error: http://dl.google.com stable Release: The following signatures were invalid: BADSIG A040830F7FAC5991 Google, Inc. Linux Package Signing Key <linux-packages-keymaster@google.com>
E: Malformed Description-md5 line; includes invalid character 'q0e5d14b133619f80a041f09d50d2ddd'
E: Malformed Description-md5 line; includes invalid character 'q0e5d14b133619f80a041f09d50d2ddd'
E: Malformed Description-md5 line; doesn't have the required length (32 != 33) '04e9d867e446a8c22145964210021b9d1'
E: Malformed Description-md5 line; doesn't have the required length (32 != 33) '04e9d867e446a8c22145964210021b9d1'
E: Malformed Description-md5 line; doesn't have the required length (32 != 33) '09ae7e6ad74f71e9dccd8d5281b51d2c2'
E: Malformed Description-md5 line; doesn't have the required length (32 != 33) '09ae7e6ad74f71e9dccd8d5281b51d2c2'
E: The package lists or status file could not be parsed or opened. 
```

When I ran apt-get install I got this:
```
enigma@Peanut:~$ sudo apt-get install
Reading package lists... Error!
E: Malformed Description-md5 line; includes invalid character 'q0e5d14b133619f80a041f09d50d2ddd'
E: Malformed Description-md5 line; includes invalid character 'q0e5d14b133619f80a041f09d50d2ddd'
E: Malformed Description-md5 line; doesn't have the required length (32 != 33) '04e9d867e446a8c22145964210021b9d1'
E: Malformed Description-md5 line; doesn't have the required length (32 != 33) '04e9d867e446a8c22145964210021b9d1'
E: Malformed Description-md5 line; doesn't have the required length (32 != 33) '09ae7e6ad74f71e9dccd8d5281b51d2c2'
E: Malformed Description-md5 line; doesn't have the required length (32 != 33) '09ae7e6ad74f71e9dccd8d5281b51d2c2'
E: The package lists or status file could not be parsed or opened.
enigma@Peanut:~$ 
'
```

I'm not sure what this means or what I should do to fix it. Can anyone help?

Thanks very much!

---

### Post by sudodus on 2013-08-28
I think it could be a temporary error at the website providing the updates. Please try again after some time.

***gpg*** is the ***GNU Pretty Good Privacy*** software, that is used to verify that the downloads are not damaged or changed during the transfer via the internet.

---

### Post by ibjsb4 on 2013-08-28
Or just try another download source.

---

### Post by cluelesswonder on 2013-08-30
OK, thanks. It seems to have sorted itself out now. . .!

---

