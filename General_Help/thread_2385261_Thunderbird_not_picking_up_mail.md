---
title: "Thunderbird not picking up mail"
date: 2018-02-18
forum: General Help
---

### Post by Panawe on 2018-02-18
I have started to have problems picking up my email via Thunderbird. here is the error message I get:

The RETR command did not succeed. Error retrieving a message. Mail server mail.talktalk.net responded: cannot open file '/nfs2/mailnec/mail_08/11/3b/phil47walk%talktalk.net/0A7000AA5BC5239D.msg' errno 2, file does not exist

I can pick up email via other devices but prefer to use Thunderbird if I can.

TIA

---

### Post by TheFu on 2018-02-18
I would contact the admin of mail.talktalk.net and ask them to fix the issue.

---

### Post by Panawe on 2018-02-18
What is xman? When I google it I get a lot of stuff about X-men and it doesn't seem to be in my Ubuntu repository.

Thanks.

---

### Post by SeijiSensei on 2018-02-18
If the failing command is [RETR]("http://www.freesoft.org/CIE/RFC/1725/8.htm"), then you must have your clients configured for POP3 rather than IMAP4.   Often POP3 servers are configured to delete the mail from the server after it has been retrieved.  If all your clients use POP3, then your mail can be scattered across devices.  Given that the error indicates T-Bird is asking for a file that does not exist, this could be the reason.

You have a couple of options.  See if enabling the Leave Mail on Server option works.  (Some providers ignore this command to save disk space.)  The other option, if your provider supports it, is changing to IMAP on all your devices.  In Thunderbird that appears in the Account Settings.

---

### Post by oldos2er on 2018-02-18
> **Panawe said:**
> What is xman? When I google it I get a lot of stuff about X-men and it doesn't seem to be in my Ubuntu repository.

It's included in the package x11-apps, which is installed by default.

---

### Post by Panawe on 2018-02-18
Converted to IMAP and things much improved.

As always, thanks to all.

---

