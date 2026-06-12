---
title: "PAM authentication failure with nis"
date: 2007-04-21
forum: General Help
---

### Post by Arne_M on 2007-04-21
Hi

Last Thursday I've installed Feisty on my desktop.
I've got a Server, which runs Suse 9.2 and manages user accounts via nis and nfs.

nfs works.

nis works, as far as I can see.
ypcat passwd returns me the passwd of the server and getent passwd shows me the local users followed by the server-users. So all fine. 

But unfortunately I can't login. 

So where have I gone wrong - How do I have to configure PAM (or do I have to? - I don't remember doing something like that on my Suse Box) ?

thanks in advance
Arne

PS: The server provides the passwords in the passwd, while my local passwords are located in shadow.

Oh yes - but first suing to root and then suing to a server-user works. So those users are there.

---

### Post by Arne_M on 2007-04-21
could the cause be different password encoding algorithms in Suse and ubuntu?
What algorithm does ubuntu use?

---

### Post by Arne_M on 2007-04-21
mmh that shouldn't be the problem - the encryption algorithm seems to be encrypted in the password

my passwords in the shadow seem to be md5 encoded - they start with $1$
the passwords in passwd, that I get from the server start with $2a$05$

so anybody got an idea what the problem might be?

greez
Arne

---

### Post by Arne_M on 2007-04-21
Ha found the problem - and fixed it! :guitar: 

my suse server uses blowfish encryption, but feisty doesn't support blowfish by default. So I had to install [FONT="System"]libpam_unix2[/FONT] and then modify my pam scripts to use [FONT="System"]pam_unix2.so[/FONT] instead of [FONT="System"]pam_unix.so[/FONT].

I've read, that blowfish is more secure than md5, why does ubuntu use md5 by default?

greetz

Arne

---

### Post by Arne_M on 2007-04-21
darn! - now I'm not able to unlock my screensaver without changing back to [FONT="System"]pam_unix.so[/FONT]

I only have to change [FONT="System"]/etc/pam.d/common-auth[/FONT] though...

---

### Post by fakie_flip on 2007-04-22
I have a similar problem. Can you help?

[http://ubuntuforums.org/showthread.php?t=412320](http://ubuntuforums.org/showthread.php?t=412320)

---

### Post by Arne_M on 2007-04-22
Sorry  - I'll probably won't be able to help you. (unless you use [FONT="System"]pam_unix2.so[/FONT], too)

My problem was located in the [FONT="System"]common-auth[/FONT] file in [FONT="System"]/etc/pam.d[/FONT], where I've simply switched the line
```
auth required pam_unix.so nullok_secure
```
into
```
auth required pam_unix2.so nullok_secure
```
but nullok_secure wasn't a valid parameter for pam_unix2.so, so I had to change it into
```
auth required pam_unix2.so nullok
```
to get it working.

---

