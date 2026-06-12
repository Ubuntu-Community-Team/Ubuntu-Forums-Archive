---
title: "Editing /etc/sudoers made mistake"
date: 2007-04-16
forum: General Help
---

### Post by steve52 on 2007-04-16
I was editing /etc/sudoers file and made a mistake. Now I am not allowed root access. How can I fix this problem. I accidently put a # in front of the last line in the file. Now I do not have root to reedit the file to correct the issue.

>>> Here is my /etc/sudoers file:
>>> # /etc/sudoers
>>> #
>>> # This file MUST be edited with the 'visudo' command as root.
>>> #
>>> # See the man page for details on how to write a sudoers file.
>>> # Host alias specification
>>>
>>> # User alias specification
>>>
>>> # Cmnd alias specification
>>>
>>> # Defaults
>>>
>>> Defaults    !lecture,tty_tickets,!fqdn
>>>
>>> # User privilege specification
>>> root    ALL=(ALL) ALL
>>>
>>> # Members of the admin group may gain root privileges
>>> # %admin ALL=(ALL) ALL                    (Not sure where the # came from but think this is my problem)
>>> 
>>> %steve ALL=NOPASSWD:/usr/sbin/firestarter               (I added this line)
>>>

---

### Post by NeoLithium on 2007-04-16
I believe that recovery mode with the live CD will allow you to use sudo to make the correction :)

---

### Post by steve52 on 2007-04-16
I tried that but could not mount my drive to edit the file. I have 2 weeks under my belt so know just about nothing

---

### Post by NeoLithium on 2007-04-16
Well, there is a nice walkthrough here, which should lend you a hand to get back in:
[http://www.psychocats.net/ubuntu/sudo](http://www.psychocats.net/ubuntu/sudo)

---

