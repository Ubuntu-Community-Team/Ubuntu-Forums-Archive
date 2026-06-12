---
title: "need help with boot"
date: 2015-05-13
forum: General Help
---

### Post by charles55 on 2015-05-13
when i boot up it goes strait to terminal and its response to any sudo command is: sudo: unable to mkdir /var/lib/sudo/sharkboy5: no such file or directory


what do i do to get out of the terminal and to the desktop( i downloaded ubuntu and this is the first linux ive ever had)

---

### Post by Bashing-om on 2015-05-13
charles55; Hi ! Welcome to the forum.

This is a first for me, and got me scratching my head.
But I will start the ball rolling.

As you cannot 'sudo' in your normal terminal we access the system from the recovery console and gain "root" access in this recovery mode.

Boot to the grub boot menu:
As soon as the bios screen clears depress and hold the right-shift- key -> boot menu
Here select the 'advanced' option -> in the next menu choose a recovery console.
in the recovery console menu choose " root".
This gives you a terminal with "root" access.
What returns from terminal commands:
```

ls -al /var/lib/sudo/
ls -al /var/lib/sudo/sharkboy5
cat /etc/sudoers
cat /etc/group

```

To exit the root terminal type exit - returns you to the console menu.

[INDENT]when you do not know
[INDENT][INDENT][INDENT]start look'n in the 'source'
[/INDENT][/INDENT][/INDENT][/INDENT]

---

