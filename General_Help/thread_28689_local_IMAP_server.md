---
title: "local IMAP server"
date: 2005-04-21
forum: General Help
---

### Post by trash-can on 2005-04-21
I am thinking about making a local IMAP server on my Ubuntu box. Only to be independent from different mail clients. The basic scheme is taht I have a a couple pop3 accounts from which mail has to be fetched locally(fetchmail?) and then accesed with any IMAP capable mail client(or webmail) through local IMAP server.

At the moment everything is no so clear to me. Googling around I came to some conclusions, although I am not sure. That is why I post here. So, possible scheme would be:

Fetching:
fetchmail -> (not sure what here, e.g. how to deliver mail to local imap folders) -> imap-server -> webmail(squirrelmail) OR MUA

Sending:
I guess simply postfix.

I would appreaciate any coments, suggestions or pointing me to some howtos or guides.

As I said in beginning, this will be only for local usage on local box.

Thanks!

---

### Post by ifrflyer on 2005-04-24
I run (on a gentoo server but should be certainly possible on Ubuntu) a seriously great configuration:

fetchmail -> SMTP -> Postrfix -> LMTP -> Amavisd (ApamAssassin/Razor/VClamAV) -> LMTP - Postfix -> maildirs

Then get everything with courier imap. Fantastic.

---

