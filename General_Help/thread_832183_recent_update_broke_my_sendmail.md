---
title: "recent update broke my sendmail"
date: 2008-06-17
forum: General Help
---

### Post by dr.krap on 2008-06-17
I host my website with apache and I use php sendmail with it. After the update this morning, I rebooted and when it got to console, it was stuck on something about (mta)sendmail. I jumped over to tty2 and reinstalled the nvidia driver, and started x. The first thing I did was check my site and test to see if the sendmail php form was still working. Sure enough, it wasn't. I then rebooted to see if it would show the message again, but it didn't.

Does anyone know what the problem could be, or have any idea what I should check to get it working again?

:confused:

---

### Post by HalPomeranz on 2008-06-18
If you rebooted and didn't see the message, perhaps the problem was transitory.  Have you tried sending email through your PHP form since the reboot?

Sendmail error messages end up in /var/log/mail.log.  That's the first place I'd look to find your error message.  Hopefully the error will give you a clue about what you need to do to fix the system.  Or post the error message here and I'll try to help.

---

