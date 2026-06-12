---
title: "What is the password for the sshd user?"
date: 2014-05-25
forum: General Help
---

### Post by vRanger on 2014-05-25
So, after installing OpenSSH, I find a user called "sshd", and am informed in other thread that this is a necessary account for file access by OpenSSH.  However, I see with this
> :~$ sudo grep "sshd" /etc/shadow
sshd:*:16198:0:99999:7:::

that there is the possibility to login with the 'sshd' user (because there is no "!" in the return string "sshd:*:16198:0:99999:7:::" like there is for root for example
> :~$ sudo grep "root" /etc/shadow
root:!:16197:0:99999:7:::

indicating that login for root is disabled.)  Can anyone tell me what or how the password is generated, and if one should disable the ability to log in with 'sshd' user with this command
> [COLOR=#333333][FONT=UbuntuMono]sudo passwd -dl sshd[/FONT][/COLOR]
I'm trying to shore up any vulnerabilities in my server, and notice that there are many attempts as shown in my auth.log, to try and gain access with the 'sshd' user.

---

### Post by steeldriver on 2014-05-25
I think you have misunderstood. Form the man page for shadow (man shadow)

```

       encrypted password
           Refer to crypt(3) for details on how this string is interpreted.

           [B]If the password field contains some string that is not a valid
           result of crypt(3), for instance [COLOR=#0000ff]! or *[/COLOR][/B], the user will not be able
           to use a unix password to log in (but the user may log in the
           system by other means).

```

---

### Post by vRanger on 2014-05-25
Ok!  First then, what is the difference between '!' and '*'.  Secondly, what is shadow?  Thanks for your support!

---

### Post by brian_woods on 2014-05-26
I think the reason could be that your authorized keys files are not accessible on the server  for OpenSSH Or your public key has not been found in the authorized keys file.

---

### Post by Lars Noodén on 2014-05-26
> **vRanger said:**
> Ok!  First then, what is the difference between '!' and '*'.  Secondly, what is shadow?  Thanks for your support!

The files /etc/passwd and /etc/shadow hold system user information. The file /etc/passwd holds what can reasonably safely be read by any user.  The file /etc/shadow contyains the encrypted password, it is there to hide the password itself.  The ! and * by themselves prevent login.  However, the ! can be prepended to an existing enrypted password to lock the account.  The account can be unlocked by removing the ! before the encryped password.  Try looking in *man shadow* or *man 5 passwd* for the official explanations.  Generally /etc/passwd no longer contains any passwd information.  

Also, the **sshd** user is there to provide unprivileged child processes so that the SSH server does not need root for everything.  That helps contain the damage should something go wrong.  

There is more detail about it here:
 [http://www.citi.umich.edu/u/provos/ssh/privsep.html](http://www.citi.umich.edu/u/provos/ssh/privsep.html)
 [http://www.citi.umich.edu/u/provos/papers/privsep.pdf](http://www.citi.umich.edu/u/provos/papers/privsep.pdf)

A lot of daemons now use the concept.

---

### Post by matt_symes on 2014-05-26
Hi

You should not be able to login as the sshd user as its shell should be

/ usr/sbin/nologin

 under ubuntu.

To check type this at the terminal

  grep sshd /etc/passwd

To see what a user who could log in as sshd, type this at the terminal

 /usr/sbin/nologin

Another layer of defence along with tje acount disabled and no password.

Kind regards

---

