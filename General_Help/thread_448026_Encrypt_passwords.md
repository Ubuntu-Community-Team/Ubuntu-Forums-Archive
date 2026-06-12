---
title: "Encrypt passwords"
date: 2007-05-18
forum: General Help
---

### Post by Derezo on 2007-05-18
I'm trying to write a script to create new users. Seemed like a simple task, but when I try 'useradd -p password -m username' the password is stored unencrypted in /etc/shadow
How can I easily encrypt the password? I'm not familiar with the type of encryption it's using. I'm running a fresh install of ubuntu server 7.04.

Google revealed some solutions involving the --stdin parameter to the passwd command, but this doesn't seem to be an option with the packaged version of passwd. There were a couple other solutions but they seemed needlessly complicated.

Any help is appreciated.

---

### Post by mbradlcu on 2007-05-19
I'm not sure but you may find this valuable:
from the man:
The password field must be filled. The encrypted password consists of
       13 to 24 characters from the 64 character alphabet a thru z, A thru Z,
       0 thru 9, \. and /. Optionally it can start with a "$" character. This
       means the encrypted password was generated using another (not DES)
       algorithm. For example if it starts with "$1$" it means the MD5-based
       algorithm was used.

seems generating a md5 hash can be done like:
daturan@cpr3:~$ echo hi | md5sum
764efa883dda1e11db47671c4a3bbd9e

I'm guessing you could add the $1$ easily enoungh

---

