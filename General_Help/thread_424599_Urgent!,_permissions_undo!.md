---
title: "Urgent!, permissions undo!"
date: 2007-04-26
forum: General Help
---

### Post by JMO707 on 2007-04-26
I have just made a terrible mistake.

Changing recursively the permissions of one folder, I forgoth to put the "." in front of "/", and press enter. That made 755 everything for a couple of seconds, but now it seems that something important is broken =(

Anything with sudo give me this:
[I]
sudo: /etc/sudoers is mode 0755, should be 0440[/I]

And the autocompletation feature this:

*./subash: /dev/null: Permesso negato*

Im afraid... dont want to reboot the machine =´(

---

### Post by JMO707 on 2007-04-27
No worries. I have learned a time ago to have the OS installed in a different partition to almost everything else. But in any case, it would be good to know:

Is there anyway to reverse the actions taken with *sudo*?

---

