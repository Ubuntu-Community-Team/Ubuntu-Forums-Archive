---
title: "Apend date to an executing script ?"
date: 2018-08-16
forum: General Help
---

### Post by raleigh3 on 2018-08-16
This works except the date being sent to this script.

Is it because I am trying to write to an executing script?

Is there a better way?

```
date '+%m-%d-%Y_%I:%M-%p'>> Send_Email.sh CONTENT="Backup to Maxtor Drive has occured."
echo "Sending email."
/usr/sbin/ssmtp -t << EOF
To: a7@yahoo.com
From: a7@yahoo.com
Subject: Backups to Maxtor Drive
$CONTENT
EOF
```

---

### Post by Holger_Gehrke on 2018-08-16
> **raleigh3 said:**
> 
Is it because I am trying to write to an executing script?

Is there a better way?


The output redirection appends the date at the end of the script **after** the end of the HERE-document. Just use a command substitution to put the date into a variable and put that variable in the body of the mail before or after $CONTENT.

Holger

---

