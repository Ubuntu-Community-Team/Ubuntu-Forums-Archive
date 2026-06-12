---
title: "evolution no more shared folder ?"
date: 2005-03-22
forum: General Help
---

### Post by garyng on 2005-03-22
Does anyone know if the developer has withdrawn this feature in IMAP ? I googled around and it seems that it was there in the 1.4 version but I cannot find it anyone in 2.2.1.

This is a setback as shared folder(in IMAP) can be  very handy for a small business setup(sales support etc.) I am wondering if it has anything to do with Novell because they sell groupwise which evolution supports(with shared folder).

---

### Post by mjk on 2005-05-08
For me it worked this way:

- Open the account editor, tab "Receiving Email"
- Set "Server Type" to "IMAP4rev1"
- Choose tab "Receiving Options"
- Enable "Overwrite server-supplied folder namespace" 
- Leave "Namespace" empty
- Some of the shared folders appear (strange thing!)
- Restart evolution, then all readable shared folders will appear  :) 


Client: Ubuntu hoary, evolution 2.2.1.1
Server: Cyrus-imapd from Debian sarge

---

### Post by df-sean on 2005-06-01
I wasn't able to get this to work at all.  No matter what I do, all 8 of my accounts display separately -- which means I have to scroll to see if I have any new messages in any of my 8 inboxes -- arrrgh!

---

