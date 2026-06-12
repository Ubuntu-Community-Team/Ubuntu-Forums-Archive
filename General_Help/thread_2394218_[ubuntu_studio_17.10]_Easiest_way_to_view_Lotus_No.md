---
title: "[ubuntu studio 17.10] Easiest way to view Lotus Notes databases in Ubuntu Studio 17"
date: 2018-06-14
forum: General Help
---

### Post by Linux_newbie_no1 on 2018-06-14
What is the easiest way to view my Lotus Notes databases in Ubuntu - is  it to install Lotus Notes (and if so how would I do that - I'm running  32 bit Ubuntu Studio 17.10), or is there any tool that can 'extract' my  Notes emails into an Ubuntu email client ?

---

### Post by Linux_newbie_no1 on 2018-06-16
I guess not then ?

---

### Post by PaulW2U on 2018-06-16
Linux_newbie_no1, I saw your first post but as I had nothing constructive to post I decided not to.

[Lotus Notes 8.5 Installation]("https://help.ubuntu.com/community/LotusNotes") on the official Ubuntu Community Help Wiki is very much out of date. Some times we just can't help with support requests that we have no experience of.

Did you find anything useful searching the web? I found a number of results that referred to Ubuntu 16.04 or earlier but I don't know how useful they may be to you knowing that you are running 17.10 which of course must soon be upgraded to 18.04.

---

### Post by Linux_newbie_no1 on 2018-06-19
Thanks man, and I've trawled the web with no success, and spent a long while doing the same on IBM sites, and there were a couple of articles on there e.g.:

[https://www.ibm.com/support/knowledgecenter/mk/SSKTMJ_9.0.1/admin/inst_installingandupgradingnotesonlinux_t.html](https://www.ibm.com/support/knowledgecenter/mk/SSKTMJ_9.0.1/admin/inst_installingandupgradingnotesonlinux_t.html)

And this is going to show my real linux ineptitude, I'm assuming for Ubuntu I'd want to follow the instructions for the Deb install, assuming I could find the actual Notes install package ?

---

### Post by PaulW2U on 2018-06-19
> **Linux_newbie_no1 said:**
> And this is going to show my real linux ineptitude, I'm assuming for Ubuntu I'd want to follow the instructions for the Deb install, assuming I could find the actual Notes install package ?
Yes, you need be looking for the .deb package that that web pages refers to and hopefully it isn't specifically for Debian or an older Ubuntu release than the 17.10 you are using. You might find that the package depends on other packages which are no longer available in Ubuntu or have been subsequently updated with newer versions. The dependencies set in the package that you download might then prohibit installation.

---

