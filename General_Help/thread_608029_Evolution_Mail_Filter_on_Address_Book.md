---
title: "Evolution Mail Filter on Address Book"
date: 2007-11-09
forum: General Help
---

### Post by Eddy5 on 2007-11-09
As a way of filtering Junk e-mails in Thunderbird I had a filter that would check if the sender was in my address book. And this worked pretty well for me.
Is there a way to do this in Evolution as I can't seem to find it?

---

### Post by dawansv on 2008-02-28
I know you asked that question a while ago but I figured this might help somebody else if not you.

I too was looking for a way to filter on the address book. I found that I could do it by using the "pipe to program" filter option pointing to the following script (just create a text file with extension .sh and put it somewhere in your home directory; make sure to make it executable).

#!/bin/sh
EMAIL=`grep -m 1 'From:' | perl -ne 'print /[\w\.\-]+@[\w\.\-]+\w+/g'`
grep $EMAIL ~/.evolution/addressbook/local/system/addressbook.db


Essentially the script extracts the From line from incoming emails, then extracts the email address from that line; finally it looks whether the email address exists in the address book. It returns 0 if there is a match, 1 otherwise, so I have my rule set to "if return value greater that 0 then move email to folder XYZ"

Hope this helps...

Vincent

---

