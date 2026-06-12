---
title: "Getting problem when sending mail using yahoo through msmtp"
date: 2013-03-06
forum: General Help
---

### Post by imarunsinghal on 2013-03-06
I am configuring ~/.msmtprc as below :-- 

[I]account yahoo
host smtp.mail.yahoo.com
port 465
tls on
tls_certcheck off
tls_starttls off
auth on
from [EMAIL="imarunsinghal@yahoo.in"]imarunsinghal@yahoo.in[/EMAIL]
user [EMAIL="imarunsinghal@yahoo.in"]imarunsinghal@yahoo.in[/EMAIL]
password passwd[/I]

And using following command as below :--
cat << EOF | msmtp -a yahoo [EMAIL="imarunsinghal@gmail.com"]imarunsinghal@gmail.com[/EMAIL] -C ~/.msmtprc 
Subject:test 
good
EOF



I am able to send mail using yahoo account. In subject it's showing "No subject" 
And in main body of mail it showing as below :--
Subject:test 
good

Please help in this that how to send mail using msmtp with Subject.
Please see attached screenshot in this mail for more clarification. 

Thanks,
Arun Singhal.

---

