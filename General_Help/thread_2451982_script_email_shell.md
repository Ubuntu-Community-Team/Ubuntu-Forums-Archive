---
title: "script email shell"
date: 2020-10-14
forum: General Help
---

### Post by emanuelemx on 2020-10-14
Hi,
i must to send a file log to email.
i have configure msmtp like this:
/home/linux/.msmtprc

```
#example
account gmail
tls on
tls_certcheck off
auth on
host smtp.gmail.com
port 587
user [EMAIL="pippo@gmail.com"]pippo@gmail.com[/EMAIL]
from [EMAIL="pippo@gmail.com"]pippo@gmail.com[/EMAIL]
password pippo
```


I do the sending test:

cat /var/log/esito | msmtp -a gmail [EMAIL="miaemail@dominio.it"]my_email@dominio.it[/EMAIL]

but nothing happens
the cursor doesn't even go to #
as if waiting for an answer
Can you help me? or find another solution?
Thanks

Ubuntu 20.04 LTS

---

### Post by ActionParsnip on 2020-10-14
What version of msmtp are you using. This link seems to show that 1.4.26 is broken.
[https://askubuntu.com/questions/233576/msmtp-hangs-instead-of-delivering-the-message](https://askubuntu.com/questions/233576/msmtp-hangs-instead-of-delivering-the-message)

---

### Post by emanuelemx on 2020-10-14
my version is msmtp 1.8.6-1

---

