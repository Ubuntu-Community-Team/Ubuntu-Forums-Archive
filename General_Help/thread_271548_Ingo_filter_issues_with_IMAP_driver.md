---
title: "Ingo filter issues with IMAP driver"
date: 2006-10-04
forum: General Help
---

### Post by axial_net on 2006-10-04
Hi,

I'm having a little difficulty with the Ingo mail filter as part of Horde.  At present, whenever I attempt to use it to run a filter rule to move an email from one folder to another a copy of the email is placed in the new mail folder, but the original copy remains.  Additionally, if a rule is created to simply delete an email, the email is not deleted.  However, when a filter rule is run Horde reports that the rule completed successfully.  The success notification occurrs regardless as to whether the rule was a move or delete rule.

(e.g. Filter activity: The message "Network usage report from "user <user@server>" has been deleted.

or

'Filter activity: The message "[ *SPAM?* ] Anatrim will change your life" from "Mallory Betts <CfdCgsdbue@mail.ru>" has been moved to the folder "INBOX.SPAM-Detected".')

I am using:

Courier imap - 3.0.8-13ubuntu5.1
Horde3 - 3.1.1-1
IMP - 4.0.4-1
Ingo - 1.0.2-2
Postfix - 2.2.10-1ubuntu0.1

The contents of backend.php are as follows:

> $backends['imap'] = array(
    'driver' => 'null',
    'preferred' => 'my.mail.server.com',
    'hordeauth' => true,
    'params' => array(),
    'script' => 'imap',
    'scriptparams' => array()
);

Unfortunately the PHP error logs do not provide any useful information, nor do the mail logs.  Also, the use of the procmail or sieve Ingo drivers would not be of use for this mail server as mail users do not have unix accounts or home directories.

Any suggestions as to steps I could take to attempt to address this issue would be very welcome.

---

