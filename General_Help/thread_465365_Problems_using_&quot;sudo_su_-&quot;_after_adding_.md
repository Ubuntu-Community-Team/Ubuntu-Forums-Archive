---
title: "Problems using &quot;sudo su -&quot; after adding &quot;mail_always&quot; to sudoers defaults"
date: 2007-06-05
forum: General Help
---

### Post by ideastar on 2007-06-05
I am using Ubuntu 6.06.1 LTS.  After running visudo and adding "mail_always" to the defaults, when I next execute "sudo su -" the prompt then alternates on each keystroke between a root prompt and the user prompt.

user@andram:~$ sudo su -
user@andram:~$ root@andram:~# l
-bash: l: command not found
user@andram:~$ -su: s: command not found
root@andram:~#
user@andram:~$ -su: -: command not found
root@andram:~# l
-bash: l: command not found
user@andram:~$ -su: a: command not found
root@andram:~#

I have been able to duplicate this behavior on two machines so far.

I know I can use "sudo -s" or something similar, but I'd like to know what's going on.

---

### Post by stchman on 2007-06-05
> **ideastar said:**
> I am using Ubuntu 6.06.1 LTS.  After running visudo and adding "mail_always" to the defaults, when I next execute "sudo su -" the prompt then alternates on each keystroke between a root prompt and the user prompt.

user@andram:~$ sudo su -
user@andram:~$ root@andram:~# l
-bash: l: command not found
user@andram:~$ -su: s: command not found
root@andram:~#
user@andram:~$ -su: -: command not found
root@andram:~# l
-bash: l: command not found
user@andram:~$ -su: a: command not found
root@andram:~#

I have been able to duplicate this behavior on two machines so far.

I know I can use "sudo -s" or something similar, but I'd like to know what's going on.

Are you trying to get a root terminal?  If so then sudo -s is the way to go.

---

### Post by ideastar on 2007-06-06
Thanks.

As I mentioned in the original post, I know that "sudo -s" can be used.

The point of adding "mail_always," in my case is to find out which user is abusing their privileges.  If I have to tell people to change the way they are doing things, it's going to warn them that something is up.

It also doesn't look very good to say "I don't know why it doesn't work. Just do it this way."

---

