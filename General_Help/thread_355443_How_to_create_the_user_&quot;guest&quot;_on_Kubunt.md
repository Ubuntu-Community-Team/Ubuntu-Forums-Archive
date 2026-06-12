---
title: "How to create the user &quot;guest&quot; on Kubuntu?"
date: 2007-02-07
forum: General Help
---

### Post by Davigetto on 2007-02-07
Hello, I want to create a user, called "guest", for ssh purposes. I want that this account can use all programs like GIMP, amarok, etc..., and it could be able to make changes on the user folder /home/guest.

But I want these special features for this account:

- It cannot run sudo and kdesu.
- It cannot see other folders except /home/guest, and it doesn't have read and write rights. Example: He cannot see the folder /etc, or /.

What must I do to perform that?

Greetings

---

### Post by bapoumba on 2007-02-07
Hello,

if "guest" is not in the admin group, it will not be able to use sudo on a basic ubuntu install.
As you can see, in my /etc/sudoers, without any changes made after install (I skipped comments) :
```
Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

```

Any user in admin group can gain root priviledge (such as first user created on install). I think you can set up other needs for "guest" account in sudoers using aliases (check examples, second half of the page) :
[http://www.die.net/doc/linux/man/man5/sudoers.5.html]("http://www.die.net/doc/linux/man/man5/sudoers.5.html")

edit : and of course see **man adduser** to create a new user ;)

---

