---
title: "HOWTO: Use a password shorter than 6 characters for any user account"
date: 2008-04-09
forum: General Help
---

### Post by hashi856 on 2008-04-09
You've created an account, and now you've decided that "algorithm" is too long a password, and you don't feel like typing it in every  time Linux decides it needs permission for something. But you're not allowed to have a password of less than 6 characters. Well here's what you do.

1. Open a terminal

2. type "sudo -i"
type in password if prompted

3. enter "passwd username". replace "username" with the user name of the account whose password you are trying to change

4. it will ask you for a new unix password. 

5. Type what ever you want.

Bam, you got a new password of what ever length you want.

---

### Post by jespdj on 2008-04-09
Beware that doing this will make your system less secure - it will make it easier for people who would like to break in into your computer to discover your password.

Note that there are lots of hackers all around the world who try to break in into computers via the Internet all the time. If you have a short password, they have a much bigger chance of finding it out.

There's a security reason why passwords have to be at least 6 characters - that rule isn't just there to annoy you.

---

