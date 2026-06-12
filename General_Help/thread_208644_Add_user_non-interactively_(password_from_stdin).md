---
title: "Add user non-interactively (password from stdin)"
date: 2006-07-03
forum: General Help
---

### Post by dyssident on 2006-07-03
this seems like it should be a nobrainer, but ive been beating my head against the wall for an hour now.

im trying to add a user non-interactively, ie. setting the password from the command line, not when prompted. the catch is, i want to do this from a clean ubuntu install without adding anyting like Expect.

with smbpasswd you can do `(echo passw0rd; echo passw0rd; ) | smbpasswd -s -a us3rname`, which would be ideal.

i cant find anything similar with any of the normal user management utilities:

adduser will accept a password with --password, but it must be ecrypted with crypt, and ubuntu apparently doesnt include crypt by default.

useradd asks for input from stdin, but doing `(echo "passw0rd"; echo "passw0rd"; echo "Full Name"; echo "rn"; echo "workphone"; echo "homephone"; echo "oth"; echo "y"; ) | sudo adduser us3rname` returns "Enter new UNIX password: Retype new UNIX password: Sorry, passwords do not match
passwd: Authentication information cannot be recovered"

passwd has a --stdin option on some versions of RedHat, but apparently not on Ubuntu.

any suggestions? my next and last idea is to use perl to mymic crypt and supply the password to adduser.

---

### Post by az on 2006-07-03
[QUOTE=dyssident]
passwd has a --stdin option on some versions of RedHat, but apparently not on Ubuntu.
[/QUOTE]
Huh?

Mine does.

---

### Post by dyssident on 2006-07-03
[QUOTE=azz]Mine does.[/QUOTE]

im as surprised as you are. `passwd --stdin` returns "passwd: unrecognized option `--stdin'"

maybe this is a version thing; this box is running Breezy, not Dapper. perhaps ill upgrade and see what i get.

Edit: could you run `dpkg -l | grep passwd` and tell me what version you have? thanks in advance.

---

### Post by dyssident on 2006-07-05
ive tried passwd on my Breezy and Dapper boxes, and neither recognize --stdin. does it work for anyone out there?

---

### Post by cpbl on 2006-09-27
On Dapper, the solution is:

useradd prometeo  -p `mkpasswd someword`

to set the password to "someword".

However, what if the user is not new? I want to reset the password.

c

---

