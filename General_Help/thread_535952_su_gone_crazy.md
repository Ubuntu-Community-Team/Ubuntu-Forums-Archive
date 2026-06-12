---
title: "su gone crazy"
date: 2007-08-27
forum: General Help
---

### Post by dijxtra on 2007-08-27
Is it possible that su is not recognising a valid root password? I'm 100% sure that I'm typing in correct password. Interesting thing is that adept_installer recognises my root password. This is what I do:
nick@rilmir:/var/log$ su
Password: 
su: Authentication failure
Sorry.

When I run adept_installer, it accepts the same password.

/var/log/auth.log says this:
Aug 27 11:33:28 rilmir su[6239]: (pam_unix) authentication failure; logname= uid=1000 euid=0 tty=pts/1 ruser=nick rhost=  user=root
Aug 27 11:33:30 rilmir su[6239]: pam_authenticate: Authentication failure
Aug 27 11:33:30 rilmir su[6239]: FAILED su for root by nick
Aug 27 11:33:30 rilmir su[6239]: - pts/1 nick:root

Where does su look for root password (or it's hash or whatever)? Is it possible that there is some kind of disk error or something that corrupted stored hash or whatever of my password?

---

### Post by kellemes on 2007-08-27
> **dijxtra said:**
> Is it possible that su is not recognising a valid root password? I'm 100% sure that I'm typing in correct password. Interesting thing is that adept_installer recognises my root password. This is what I do:
nick@rilmir:/var/log$ su
Password: 
su: Authentication failure
Sorry.

When I run adept_installer, it accepts the same password.

/var/log/auth.log says this:
Aug 27 11:33:28 rilmir su[6239]: (pam_unix) authentication failure; logname= uid=1000 euid=0 tty=pts/1 ruser=nick rhost=  user=root
Aug 27 11:33:30 rilmir su[6239]: pam_authenticate: Authentication failure
Aug 27 11:33:30 rilmir su[6239]: FAILED su for root by nick
Aug 27 11:33:30 rilmir su[6239]: - pts/1 nick:root

Where does su look for root password (or it's hash or whatever)? Is it possible that there is some kind of disk error or something that corrupted stored hash or whatever of my password?

But adept_installer you'll probably startup using sudo or gksu right?
That's asking for userpassword..

Edit: Are you sure there is a rootpassword set?

---

### Post by kerry_s on 2007-08-27
> **dijxtra said:**
> Is it possible that su is not recognising a valid root password? I'm 100% sure that I'm typing in correct password. Interesting thing is that adept_installer recognises my root password. This is what I do:
nick@rilmir:/var/log$ su
Password: 
su: Authentication failure
Sorry.

When I run adept_installer, it accepts the same password.

/var/log/auth.log says this:
Aug 27 11:33:28 rilmir su[6239]: (pam_unix) authentication failure; logname= uid=1000 euid=0 tty=pts/1 ruser=nick rhost=  user=root
Aug 27 11:33:30 rilmir su[6239]: pam_authenticate: Authentication failure
Aug 27 11:33:30 rilmir su[6239]: FAILED su for root by nick
Aug 27 11:33:30 rilmir su[6239]: - pts/1 nick:root

Where does su look for root password (or it's hash or whatever)? Is it possible that there is some kind of disk error or something that corrupted stored hash or whatever of my password?

there is no "su" in ubuntu, root is disabled for security, use> sudo su

---

### Post by dijxtra on 2007-08-27
> **kellemes said:**
> But adept_installer you'll probably startup using sudo or gksu right?
That's asking for userpassword..
Hm, don't know really, I'm not that proficient in Linux and my user password and root password are the same (yeah, I know, a security risk, but it's just my home computer). But wait, isn't sudo asking for root password?
> **kellemes said:**
> Edit: Are you sure there is a rootpassword set?
Yes, I'm quite sure.

But, just for the heck of it, I tried with empty password, and su failed again...

---

### Post by dijxtra on 2007-08-27
> **kerry_s said:**
> there is no "su" in ubuntu, root is disabled for security, use> sudo su
Wohow, I love you :-D I thought I was in really deep sh... trouble, but not it works :-)

Is there a way to enable su?

---

### Post by kerry_s on 2007-08-27
> **dijxtra said:**
> Wohow, I love you :-D I thought I was in really deep sh... trouble, but not it works :-)

Is there a way to enable su?

yes, you can set a root password which will enable su, but your security will drop to half, since attackers now will only have to guess your root password, instead of your user name and password.

enable root:
sudo passwd root

disable root, should you want to go back:
sudo passwd -l root


you've been warned, in the end it's your choice.

---

### Post by maybeway36 on 2007-08-27
You could type ```
sudo su
``` and use your user password.

---

