---
title: "root password doesn't change, supports 2 passwords"
date: 2019-11-13
forum: General Help
---

### Post by loub19 on 2019-11-13
Hello, we found that when we change the root password "passwd root" that that password is changed but we can now log into root with both old and new password. I also tried disabling root, "passwd -ld root", what I've found is that the new passwd causes a "Permission denied",  but I'm still able to log in with the old passwd. 
Any ideas???
Ubuntu 18.04.

---

### Post by TheFu on 2019-11-13
We use sudo techniques instead in Ubuntu.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by loub19 on 2019-11-13
Yes I understand the reason behind sudo but Ubuntu, CentOS, Fedora have always been open and allowing the user to manage there environment as they please.
I've tested my CentOS V7 systems and they do not support 2 passwords for the root account.
If anyone else has any suggestions I would greatly appreciated it.
Thanks,

---

### Post by TheFu on 2019-11-13
Ubuntu is different from CentOS, Debian, Fedora or Slackware which all set the root account at install time.

Thinking a little more, perhaps systemd broke something?  [https://linux.slashdot.org/story/15/08/29/1526217/systemd-absorbs-su-command-functionality](https://linux.slashdot.org/story/15/08/29/1526217/systemd-absorbs-su-command-functionality)  

I tried to reproduce the issue and couldn't on Ubuntu 16.04.  Set a passwd. Changed the passwd. Tried to use both to **su -**; only the correct password was allowed.  Then I removed the root passwd by editing the shadow file. No **su - **was allowed.  **sudo -i** still worked fine.

Are you certain there is only 1 root account?  Use  **getent passwd**  to check.
In the /etc/shadow file, it should look like this:
```
root:!:17995:0:99999:7:::
```

Some programs in Ubuntu have been patched according to that link already provided. Might that be part of the issue?

As for having multiple passwords, multiple root-equiv accounts can be used.

---

### Post by TheFu on 2019-11-13
Tested on an 18.04 server and couldn't reproduce the issue there either.

Can you please show the steps involved?

---

### Post by loub19 on 2019-11-13
I have a number of Ubuntu (16.04, 18.04) installation both vm's and physical servers.  I have found this issue on all our servers.  Our installation process is as followings.

   
  
[LIST=1]
[*][FONT=&amp]Install Ubuntu from iso[/FONT] 
[*][FONT=&amp]During installation create a default account &      password[/FONT] 
[*][FONT=&amp]Continue installation,  once installed enable root      account with default password.[/FONT] 
[*][FONT=&amp]Test server, install additional software needed for      productions with root[/FONT] 
[*][FONT=&amp]Once the server is ready for production we change root password.[/FONT] 
[/LIST]
   

   

  ```
root@test2:/etc/pam.d# getent passwd| grep -i root
"root:X:0:0:root:/root:/bin/bash"
root@test2:/etc/pam.d# getent shadow| grep -i root
"root:!18213:0:99999:7:::"
```

---

### Post by TheFu on 2019-11-13
```
root:X:0:0:root:/root:/bin/bash
```
should be
```
root:x:0:0:root:/root:/bin/bash
```

Yes?

From the manpage, section 5 ....
```
       The encrypted password field may be blank, in which case no password is
       required to authenticate as the specified login name. However, some
       applications which read the /etc/passwd file may decide not to permit
       any access at all if the password field is blank. If the password field
       is a **lower-case** &#8220;x&#8221;, then the encrypted password is actually stored in
       the shadow(5) file instead; there must be a corresponding line in the
       /etc/shadow file, or else the user account is invalid. If the password
       field is any other string, then it will be treated as an encrypted
       password, as specified by crypt(3).

```

---

### Post by loub19 on 2019-11-13
Yes that is correct I was trying to clean up the emoji that the editor kept inserting the first 3 times for both passwd and shadow.

---

### Post by TheFu on 2019-11-13
Looks like my update was missed.

check out section 5 manpage for passwd.  LOWER CASE is required.

---

### Post by CatKiller on 2019-11-13
> **loub19 said:**
> I was trying to clean up the emoji that the editor kept inserting

If you put things between [code] tags the forum won't change the formatting.

---

### Post by loub19 on 2019-11-14
I would like to also point out that we have a hpc cluster built by an outside vendor, Ubuntu 16.04, shipped to us with a non root account. Once on site we enabled root and we have changed the password a few times and we the same issue, the root account support 2 passwords.

---

