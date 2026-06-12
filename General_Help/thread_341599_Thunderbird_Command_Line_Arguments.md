---
title: "Thunderbird Command Line Arguments?"
date: 2007-01-18
forum: General Help
---

### Post by carney1979 on 2007-01-18
Does anyone know the command line arguments for Thunderbird to compose to a specific email address and add an attachment to the email?

David

---

### Post by Johan! on 2007-01-18
You can find all command line options here:
[http://www.mozilla.org/docs/command-line-args.html](http://www.mozilla.org/docs/command-line-args.html)
[http://kb.mozillazine.org/Thunderbird_Command_Line_Arguments](http://kb.mozillazine.org/Thunderbird_Command_Line_Arguments)

To send an email:
```
mozilla-thunderbird -compose to="test@foo.com",subject="testsubject",body="testbody",attachment="file:///home/username/testattachment.foo"
```

Type this all in one line, and modify it to fit your needs:)

---

### Post by penno on 2007-10-07
hi all

This command brings up the compose window with all the parameters nicely filled in. Which is fine. (c: Is there a way to automatically send the email? ie if I wanted to cron an automatic email, can I use thunderbird?

Thanks

penno

---

### Post by wacked215 on 2008-04-12
I was running into the same problem. I ended up using [JavaMail]("http://java.sun.com/products/javamail/") and its samples to create my own program that can send from the terminal. It works like a charm, although I wasn't able to get a working version without using an IDE to compile and add the proper mail.jar and activation.jar libraries to the project.

---

### Post by penno on 2008-04-13
fwiw I ended up using sendEmail. Example:

[FONT="Courier New"]cat file |sendEmail -f [email]from@email.addr[/email]ess -t [email]to@email.addr[/email]ess -u "subject" -s mail.server.com[/FONT]

---

