---
title: "Changing Grub Boot Parameter Causes Major Slow Down"
date: 2018-01-24
forum: General Help
---

### Post by rwonder on 2018-01-24
So I ran into the problem where I cannot enter my password to decrypt my disk. So I used the solutions found here: [Cannot enter password to start Ubuntu 16.04]("https://askubuntu.com/questions/574296/cannot-enter-password-to-start-ubuntu")

Which in summary is...

Update boot parameters in /etc/default/grub and change splash to nosplash. After that you can run update-grub.

It solved the problem, yay! But then, once I log in Ubuntu is super laggy. If I type a letter, it takes 10 seconds for the letter to appear.

1) Why? Would love to understand.

2) What can I do to get around this?

3) Before I knew this was the cause, I tried solving this by installing a fresh copy of Ubuntu. Interestingly, unless I selected the following install options I would run into the same problem: 
[IMG]https://i.stack.imgur.com/cOBaA.png[/IMG]
Why in the world would leaving "Encrypt..." and/or "Use LVM..." unchecked cause major lag?

---

