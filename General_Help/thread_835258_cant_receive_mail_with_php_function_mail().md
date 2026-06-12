---
title: "cant receive mail with php function mail()"
date: 2008-06-20
forum: General Help
---

### Post by eerojms5 on 2008-06-20
i installed sendmail
then i configured it by answering Y to all the questions

When i fill my form then everything is ok but i dont receive any mail
can anyone help??

---

### Post by fragos on 2008-06-20
Your browser will use you system default mail package to send mail. Evolution is the default unless you change that in "Preferred Applications" Preferences.

---

### Post by lightstream on 2008-06-20
Do you mean you are sending a test message using mail() on localhost, but not receiving the email?

Try looking in the sendmail log for clues as to what is happening - I think it's located in /var/log/sendmail

---

