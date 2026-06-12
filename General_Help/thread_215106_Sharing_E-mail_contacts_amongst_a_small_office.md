---
title: "Sharing E-mail contacts amongst a small office"
date: 2006-07-13
forum: General Help
---

### Post by jrattner on 2006-07-13
Afternoon,

I work in a small office of about 10 people.  I administer their network.  What I'm trying to do is allow the 10 people in the office to share e-mail contacts from one centralized location.
Meaning, everyone has the same contacts.

I understand that I could use LDAP, but i feel its FAR more then overkill for JUST e-mail contacts + names.

Does anyone have an** easy** solution to this situation?

By the way, all clients are running Mozilla Thunderbird.

Thank you,
         jrattner :-|

---

### Post by Valehru on 2006-07-13
You could use TinyLDAP.  
[http://www.fefe.de/tinyldap/](http://www.fefe.de/tinyldap/)

If your using an email client then LDAP is the way to go and set up a Global Address List (GAL).

---

### Post by jrattner on 2006-07-13
Anything even simplier?

---

### Post by stengah on 2006-08-21
Latest response ever, but stumbled across this thread figurered I might as well pose a suggestion.

Try using Thunderbird as a mail client and, get hold of the Sync Kolab extension. If you have IMAP enabled on your mailserver you should be abl to use Sync Kolab to share e.g. mail adresses via an IMAP folder.

I'm not using this extension myself, but meyby this would be a simpler way as opposed to LDAP.

Hope it works (or has worked) out!

---

