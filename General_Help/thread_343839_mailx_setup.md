---
title: "mailx setup"
date: 2007-01-22
forum: General Help
---

### Post by mvaniersel on 2007-01-22
How do I set up the mailx package, so I can send email from scripts using the mail command? 

I've searched the internet and I find a lot of guides (like [https://help.ubuntu.com/community/PostfixBasicSetupHowto](https://help.ubuntu.com/community/PostfixBasicSetupHowto)) on how to get your computer to receive email, but none on how to send email.

I think it must be a simple matter of adding an smtp address to a config file, but I have no idea how or where.

---

### Post by mvaniersel on 2007-01-23
No replies? I didn't think this was so hard... Am I missing something?

---

### Post by mvaniersel on 2007-01-23
Ok, I managed to solve it. The solution was to install the package ssmtp, and then point it to my smtp server in /etc/ssmtp/ssmtp.conf. No need to set up postfix.

---

### Post by marshcast on 2007-03-15
thank you - thats saved me a lot of mucking about! 

i'll give it a go ;)

---

