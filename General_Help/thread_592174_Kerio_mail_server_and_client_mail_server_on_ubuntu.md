---
title: "Kerio mail server and client mail server on ubuntu"
date: 2007-10-26
forum: General Help
---

### Post by cmbxl on 2007-10-26
Hello, 

We use Kerio mail server and i want to use a compatible mail client on ubuntu or a method to get mail   and calendar with evolution or thunderbird.

Any idea ? 

Thx a lot

---

### Post by Poleh on 2007-11-26
Can you not simply use Evolution and IMAP to connect to the server?

---

### Post by murasame on 2007-12-04
That's a really good question.

I've been trying hard to connect to the kerio mail server at my office using evolution and the exchange protocol without much success. (I'm on ubuntu 7.10)

I've got a win2000 (thanks to our admin) / ubuntu 7.10 (thanks to me) dual boot there.
I've checked the configuration in outlook and the client is setup to use the exchange protocol and connect to kerio mail server.

I'm still wondering wether it is possible on ubuntu. Mind you, I could just use the kerio webmail server (typing [http://webmail.ourdomain.com/](http://webmail.ourdomain.com/)) but our proxy doesn't allow any web address that has the word 'mail' in it...

I do have an issue here as I really want to be able to check my professional mailbox on ou local server without rebooting on win2000.

A clue would be appreciated.

Of course, my admin just tells me to f... off and stop using linux as he's "implemented a windows network, not a linux one", which -although not making much sense today- can't be discussed in anyway. All is up to me.

> **Poleh said:**
> Can you not simply use Evolution and IMAP to connect to the server?

Well, I'm not sure imap could technically act as a micros*** exchange protocol to do the job. Do you mean using imap in evolution to connect to the kerio mail server ? How would you do that ?

---

### Post by Poleh on 2008-02-26
odd that you have Exchange pointing to Kerio mail server using exchange protocol ... as I know Kerio has its own Exchange connector, or you could use IMAP to connect to it (either from Exchange/Evolution).

To clarify-
 - you can use Evolution to connect to Kerio using IMAP (not exchange) protocol
 - you can use Evolution to connect to Exchange using IMAP (if it's enabled by your admin) or Exchange protocols

Hope this helps

---

