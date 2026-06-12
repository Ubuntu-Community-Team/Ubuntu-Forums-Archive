---
title: "Help with a script"
date: 2007-03-24
forum: General Help
---

### Post by tbeld on 2007-03-24
I am working on script that will format a .csv file for uploading users to another system. All I have left to do is to copy the email from the email field and paste it at the beginning of the line followed by comma space comma. So the csv file looks like this:

username, password, firstname, lastname, email,
jane, doe, [email]jdoe@someservice.com[/email]

and i need the script to make each record look like this:

username, password, firstname, lastname, email
[email]jdoe@someservice.com[/email], ,jane, doe, [email]jdoe@someservice.com[/email]

The system will autogenerate the password. Thanks for any help.

---

### Post by kidders on 2007-03-24
Hi there,

Taking the example you mentioned, you could convert [COLOR="Blue"]jane, doe, jdoe@someservice.com[/COLOR] to [COLOR="Blue"]jdoe@someservice.com, ,jane, doe, jdoe@someservice.com[/COLOR] this way...

```
echo "jane, doe, jdoe@someservice.com" | sed 's/\([^,]*\),\s*\([^,]*\),\s*\([^,]*\)/\3, , \1, \2, \3/'
```

The short answer is that you could use a **sed** swap, but I thought a quick example might help.

---

### Post by tbeld on 2007-03-24
Perfect. Thanks so much kidders!

---

### Post by kidders on 2007-03-24
:-) No problem.

---

