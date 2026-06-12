---
title: "Can't change password with cron"
date: 2020-01-08
forum: General Help
---

### Post by asaushkin on 2020-01-08
Hi,

I would like to change a user password using cron. So I have added records to /etc/crontab:

```
* 22-23,0-6 * * * root echo -e "*RANDOM*\n*RANDOM*" | passwd user && /sbin/shutdown -h now
* 7-21 * * * root echo -e "my_pass\nmy_pass" | passwd user
```

These commands work as expected when I call them from the command line but with cron they throw a message:

```
passwd: Authentication token manipulation error
passwd: password unchanged
```

As I understand it because of lacking pam records for cron. I've tried to add this line to /etc/pam.d/cron:

```
@include common-password
```

but it has no effect.

What I must to do to allow the password changing with cron?

P.S. It happens on fresh Ubuntu 18.04

---

### Post by TheFu on 2020-01-08
I'm sorta glad this isn't possible.  Always thought that password changes required a tty/pty to work.  After ssh keys are setup, I'll make a crazy long password and forget about it.  It never gets used anyway.  Remote password access is blocked in the sshd_config, if you want to make attempted access with a password useless.

For changing passwords, I'd use either expect or ansible, but there are a number of other, similar, tools.  Haven't used expect since the 1990s. Ansible works over ssh and with a deploy account, you can setup sudo not to require password auth.

Perhaps if we understood the purpose behind this, then a different solution could be suggested?

---

### Post by Impavidus on 2020-01-09
Let's see what you're trying to do. At night, you run a command every minute to change the password of a user and shutdown the computer. With the computer shutting down every minute it's quite impossible to use it already, so I'm not sure of the purpose of the password changes. During the day, you reset the password every minute to a different default. Doing it once at boot would be sufficient, unless it's your intention to make it impossible to change the password to something secret. Further, both passwords are stored in plain text and readable for everybody in /etc/crontab. And everybody who can boot the computer at night probably has physical access and would be able to remove those cron jobs.

---

### Post by asaushkin on 2020-01-09
> **TheFu said:**
> 
Perhaps if we understood the purpose behind this, then a different solution could be suggested?

I want to limit usage of that box for *user* only from 7:00 to 21:59

---

### Post by TheFu on 2020-01-09
Did you try pam_time first?  [http://www.linux-pam.org/Linux-PAM-html/sag-pam_time.html](http://www.linux-pam.org/Linux-PAM-html/sag-pam_time.html)
Did it not work? [https://debian-administration.org/article/227/Restricting_server_access_by_time](https://debian-administration.org/article/227/Restricting_server_access_by_time)

I've not used this.

There's also the **usermod** technique to lock and unlock a user account. No need to screw with the password at all.  From the manpage:
```
       -L, --lock
           Lock a user's password. This puts a '!' in front of the encrypted
           password, effectively disabling the password. You can't use this
           option with -p or -U.

           Note: if you wish to lock the account (not only access with a
           password), you should also set the EXPIRE_DATE to 1.

```

If locking down just the network access is sufficient, many routers have that capability.  I have used it.

---

### Post by asaushkin on 2020-01-09
> **Impavidus said:**
> Let's see what you're trying to do. At night, you run a command every minute to change the password of a user and shutdown the computer. With the computer shutting down every minute it's quite impossible to use it already, so I'm not sure of the purpose of the password changes. During the day, you reset the password every minute to a different default. Doing it once at boot would be sufficient, unless it's your intention to make it impossible to change the password to something secret.

Yes, this is a possible solution. But if you turn on the box in 6:59 it is possible that password won't changed with the @reboot keyword.


> **Impavidus said:**
> Further, both passwords are stored in plain text and readable for everybody in /etc/crontab. And everybody who can boot the computer at night probably has physical access and would be able to remove those cron jobs.

Yes, you are right. This is my child and I hope that he will solve that, then I'll do something new for him :)

---

### Post by asaushkin on 2020-01-09
> **TheFu said:**
> Did you try pam_time first?  [http://www.linux-pam.org/Linux-PAM-html/sag-pam_time.html](http://www.linux-pam.org/Linux-PAM-html/sag-pam_time.html)
Did it not work? [https://debian-administration.org/article/227/Restricting_server_access_by_time](https://debian-administration.org/article/227/Restricting_server_access_by_time)

I've not used this.

There's also the **usermod** technique to lock and unlock a user account. No need to screw with the password at all.  From the manpage:
```
       -L, --lock
           Lock a user's password. This puts a '!' in front of the encrypted
           password, effectively disabling the password. You can't use this
           option with -p or -U.

           Note: if you wish to lock the account (not only access with a
           password), you should also set the EXPIRE_DATE to 1.

```

If locking down just the network access is sufficient, many routers have that capability.  I have used it.


Thanks, **TheFu**!

I think that **usermod **is exactly what I am trying to find. 

**pam_time** also looks really interesting for me.

---

