---
title: "phpBB2 and Exim4"
date: 2006-12-11
forum: General Help
---

### Post by DarthSwampy on 2006-12-11
I just got my Ubuntu 6.06 server up and running with LAMP, and I want to host a phpBB-forum. Everything works fine, except the mail-function. I configured it so that a email is being sent to the administrator so that he can activate new users. First I had no mail-server and it gave a error when you tried to register. Then I tried Sendmail, wich just made the web-browser load forever and the shell that runs sendmail prints the message: "Recipient names must be specified". Finally I tried Exim4 and everything seems to work, you get the message:

"Your account has been created. However, this forum requires account activation by the administrator. An e-mail has been sent to them and you will be informed when your account has been activated".

But I don't get any mail to the configured admin-address.

---

