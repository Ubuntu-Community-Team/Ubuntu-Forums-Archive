---
title: "Thunderbird won't send messages through gmail"
date: 2018-04-25
forum: General Help
---

### Post by Coriander Redgoat on 2018-04-25
Thunderbird won't send messages using gmail, it was previously fine. It just says "connected to smtp.googlemail.com and stays there. I tried changing the port but no improvement.

---

### Post by cressrt2 on 2018-04-25
My gmail connects to smtp.gmail.com, not sure if this will make any difference.

---

### Post by SeijiSensei on 2018-04-25
I just configured Thunderbird for GMail the other day; it's using smtp.gmail.com on port 465.

smtp.googlemail.com and smtp.gmail.com are not the same machine:

```
$ host smtp.googlemail.com
smtp.googlemail.com is an alias for googlemail-smtp.l.google.com.
googlemail-smtp.l.google.com has address 173.194.203.16
googlemail-smtp.l.google.com has IPv6 address 2607:f8b0:400e:c00::10

$ host smtp.gmail.com
smtp.gmail.com is an alias for gmail-smtp-msa.l.google.com.
gmail-smtp-msa.l.google.com has address 173.194.203.109
gmail-smtp-msa.l.google.com has address 173.194.203.108
gmail-smtp-msa.l.google.com has IPv6 address 2607:f8b0:400e:c05::6d

```

---

### Post by Coriander Redgoat on 2018-04-25
I just tried with [COLOR=#000000]smtp.gmail.com [/COLOR][COLOR=#000000]on port 465[/COLOR][COLOR=#000000], but I have the same problem[/COLOR]

---

### Post by SeijiSensei on 2018-04-26
Call your ISP and make sure they are not blocking outbound mail.  Maybe they changed their policies recently.

Install the telnet package, then try 

```
telnet smtp.gmail.com 465
```

Do you get the server's banner?

```

$ telnet smtp.gmail.com 465
Trying 173.194.208.108...
Connected to gmail-smtp-msa.l.google.com.
Escape character is '^]'.
^]
telnet> quit

```

---

### Post by Coriander Redgoat on 2018-04-26
The command took a few minutes to complete, and then it immediately closed:

```
telnet smtp.gmail.com 465Trying 2607:f8b0:400d:c0d::6c...
Trying 173.194.207.109...
Connected to smtp.gmail.com.
Escape character is '^]'.
Connection closed by foreign host.



```

My other email account sends mail no problem

Thanks!

---

### Post by Coriander Redgoat on 2018-04-26
Hmmm... with further testing it appears emails are going through, but it's just really slow

---

### Post by Coriander Redgoat on 2018-05-05
nvm seems to be solved. Thanks

---

