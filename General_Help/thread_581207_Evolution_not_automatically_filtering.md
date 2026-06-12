---
title: "Evolution not automatically filtering?"
date: 2007-10-19
forum: General Help
---

### Post by mbeierl on 2007-10-19
Filters are not automatically applied on new incoming mail when Exchange plug in is used.

The post for this in Gutsy development has been closed, but I just wanted to know if I was the only one still experiencing this?

---

### Post by tychocity on 2007-10-21
i have this problem too.

---

### Post by lfjewett on 2007-10-22
I am also having this problem with a fresh install of Gutsy.  I noted that someone else on here with evolution & exchange that said it was working fine for them said the filters were applied to their windows outlook as well.  I know my exchange servers won't accept filters from any client except outlook, 

Could the problem be that evolution is trying to do server side filtering instead of client side filtering?

---

### Post by mbeierl on 2007-10-22
Doh!  I don't know what I did, but it's working for me now.  Odd - I haven't seen any updates since Gutsy was released...

---

### Post by MikeMLP on 2007-10-22
I am having trouble with filters as well.
I've been getting a lot of spam lately on my school account, and it is tagged properly by their system.

I'm sure I have the right settings set to put all of the tagged spam into a spam folder, but Evolution does not comply.  Any tips would be appreciated.

Edit:I've noticed that if I have a message selected in my inbox that should have been sent to the spam folder, and I click message>apply filters <Ctrl+Y>, the message in question gets moved properly.  Is there a proper way to set it up so that the mail never appears in my inbox?

---

### Post by mbeierl on 2007-10-22
Dang!  Posted too soon.  Filters stopped working again!  This is quite confusing...

---

### Post by firsttry on 2007-10-24
Got the same problem - filters worked in feisty, then I performed an unsuccessful upgrade from feisty to gutsy (loads of problems), followed by a clean install of gutsy (keeping my home partition), In both cases of Gutsy the filters didn't work - the only workaround was to select the newly arrived messages and Ctrl-Y. It'd be nice to sort this out, especially seen as I've seen threads about this issue from a few years ago...!

I too am using the Microsoft Exchange server... Is this Ubuntu-specific or a cross-platform Evolution bug?

---

### Post by stevoooo on 2007-10-24
FWIW I'm having the same problem and I'm also using an Exchange server.  Worked just fine in feisty and stopped working after the upgrade.  I tried removing and re-adding the message filters and that seemed to work at least partly, but now I'm back to having to do it manually.  I've tried disabling the Exchange plugin as suggested but that didn't help either (also, is it just me or does the "configure" button not work for every plugin?).

I'm afraid that I don't have an answer, but this **is** driving me absolutely nuts and so will have to get it fixed soon :mad:

---

### Post by stevoooo on 2007-10-24
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/10669/](https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/10669/) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				At least this issue appears to be recognised, so hopefully there's a good chance of it getting fixed soon...

---

### Post by firsttry on 2007-10-25
> **stevoooo said:**
> **This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/10669/](https://bugs.launchpad.net/ubuntu/+source/evolution-exchange/+bug/10669/) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				At least this issue appears to be recognised, so hopefully there's a good chance of it getting fixed soon...

That's the bug I was talking about: 2004!!!

---

### Post by mbeierl on 2007-10-25
It appears if I start Evolution with my Exchange Server mailbox completely empty, then filtering automatically works.

If there are any emails in my inbox on the server, automatic filtering does not work. :confused:

---

### Post by bullsbarry on 2007-10-31
I was successfuly using this feature on fedora 7 without problem.  I wonder if it works on fedora 8, which should be the same version of evolution as gutsy (7 should've been the same version as feisty)

Edit: Should've mentioned...no success for me.

---

