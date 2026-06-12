---
title: "sendEmail help"
date: 2014-11-23
forum: General Help
---

### Post by fabian12 on 2014-11-23
I am running Lubuntu 14.10 and trying to learn as much as i can about the command line and decided to learn about sending email from the command line with sendEmail. So i installed sendEmail with ```
sudo apt-get install sendemail
``` the other two libraries: libio-socket-ssl-perl and libnet-ssleay.perl were both pre-installed.
 
I then opened up Nano and created a new script called newEmail and i then typed the following:

#!/bin/bash

sendEmail -f [email]username@gmail.com[/email] -t [email]username@gmail.com[/email] -u "Testing sendEmail" -m "Testing sendEmail 1 2 3 ..." -s smtp.gmail.com:587 -xu myUsername -xp my password for the gmail account

I saved the script and then give it executable permissions chmod +x newEmail

But when i tried to run the script using: ./newEmail i got the following error message:

Nov 23 16:54:57 lubuntu sendEmail[4806]: ERROR => ERROR => SMTP-AUTH: Authentication to smtp.gmail.com:587 failed.

Could someone help please.

---

### Post by nerdtron on 2014-11-23
It's an old tutorial but is worth the try [http://ubuntuforums.org/showthread.php?t=1711217](http://ubuntuforums.org/showthread.php?t=1711217)

---

### Post by fabian12 on 2014-11-23
Hey thanks nerdtron. I'll let you know if i have any success lol

---

