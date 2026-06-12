---
title: "Make sylpheed delete trashed e-mail from POP3 server account"
date: 2013-05-28
forum: General Help
---

### Post by Charlotte18 on 2013-05-28
Is there a way to make Sylpheed delete messages from the POP3 server INBOX when the messages are deleted from the INBOX in Sylpheed?

---

### Post by Cheesemill on 2013-05-29
Can you use IMAP instead of POP3?

POP3 was never designed to do what you are asking.

---

### Post by Irihapeti on 2013-05-29
Thunderbird does have a setting that allows you to delete messages on the server if they're deleted locally. I don't see any setting in Sylpheed that would let you do that. But it could be done manually with the use of message filters. You could mark messages to be deleted by setting a flag and then run a filter that deletes all flagged messages from the POP3 server.

---

### Post by Charlotte18 on 2013-05-29
> **Cheesemill said:**
> Can you use IMAP instead of POP3?No. The e-mail service doesn't have IMAP on.
> POP3 was never designed to do what you are asking.Who cares? I do a lot of things contrary to the original design.
[QUOTE=Irihapeti]You could mark messages to be deleted by setting a flag and then run a filter that deletes all flagged messages from the POP3 server.[/QUOTE]Thanks, that will work.

---

### Post by Zill on 2013-05-29
> **Cheesemill said:**
> Can you use IMAP instead of POP3?

POP3 was never designed to do what you are asking.
Err... I disagree.  To quote [Wikipedia]("http://en.wikipedia.org/wiki/Post_Office_Protocol"):
> POP supports simple download-and-delete requirements for access to remote mailboxes (termed maildrop in the POP RFC's). Although most POP clients have an option to leave mail on server after download, e-mail clients using POP generally connect, retrieve all messages, store them on the user's PC as new messages, delete them from the server, and then disconnect.
In Claws Mail, simply go to the Account preferences and check the option to "Remove messages on server when received".

---

### Post by Cheesemill on 2013-05-29
> **Zill said:**
> Err... I disagree.  To quote [Wikipedia]("http://en.wikipedia.org/wiki/Post_Office_Protocol"):

In Claws Mail, simply go to the Account preferences and check the option to "Remove messages on server when received".

I know how POP3 works, but this isn't what the OP was asking to do.

Instead of deleting the messages from the server when they are downloaded, the OP wants to download all of the messages ***and*** keep them on the server, but have any messages that are deleted from the local inbox automatically deleted from the server as well.

---

### Post by Charlotte18 on 2013-05-29
> You could mark messages to be deleted by setting a flag and then run a filter that deletes all flagged messages from the POP3 server.For some reason, this method gives every appearance of working (i.e., the filter rule runs and is set to delete from server, the messages move to Sylpheed's trash), but the messages remain on the server.

---

### Post by Irihapeti on 2013-05-29
The messages actually get deleted when you next check for new mail. At least, that's my experience with using Thunderbird.

---

### Post by Charlotte18 on 2013-05-29
Unfortunately, in Sylpheed, the messages remain on the server when "delete from server" is checked in the filter even after a check for new mail.

---

### Post by Irihapeti on 2013-05-29
That sounds like a bug, either in Sylpheed or the way the server has been set up. The only thing I can suggest is trying a different email client (Thunderbird, perhaps) to narrow it down, and then either report a bug or inform the ISP/email provider.

---

### Post by Zill on 2013-05-29
> **Charlotte18 said:**
> Unfortunately, in Sylpheed, the messages remain on the server when "delete from server" is checked in the filter even after a check for new mail.
IMHO this problem does not need a filter.

Have you actually set the Account preferences option to "Remove messages on server when received" as I recommended in post [#5]("http://ubuntuforums.org/showthread.php?t=2149454&p=12668506#post12668506") above?

---

### Post by Charlotte18 on 2013-05-29
I don't want to remove the messages from the server *when received*.  I want to remove the messages from the server when they are deleted in Sylpheed.

---

### Post by Zill on 2013-05-30
My apologies to Cheesemill and Irihapeti. ;-)

Their advice is quite correct in that POP3/Sylpheed will not do what you wish IMO.

---

### Post by Charlotte18 on 2013-05-30
That is why I have entitled the thread, "*Make* (as in 'force') Slypheed" to do what I want. I don't understand why the filter set to "delete from server" does not in fact delete the filtered messages from the server.

---

### Post by Zill on 2013-05-30
> **Charlotte18 said:**
> ...I don't understand why the filter set to "delete from server" does not in fact delete the filtered messages from the server.
Probably because this is an IMAP function, not a POP3 function.  POP3 normally deletes mail from the server after downloading it to the PC whereas IMAP keeps mail on the server.

---

### Post by Charlotte18 on 2013-05-30
I understand, but obviously it's possible to have the e-mail client do what I want Slypheed to do since Thunderbird and Evolution are able to delete messages from the POP3 server when they are deleted from the client software. So the mere fact that I'm on a POP3 server doesn't render impossible what I want to do. More likely, the Slypheed developers have a conservative outlook on the "proper" purpose of POP3.

---

### Post by Irihapeti on 2013-05-30
POP3 will either leave the mail on the server or delete it, depending on your email client setup. Probably most often, people choose to delete the mail as soon as they've downloaded it, but there is the choice. I have several email clients set up, including one on my phone, and I only want one of them to actually delete the mail off the server. The others are set to leave it there.

Thunderbird can be set up to do what the OP wants, and I've been using it that way for some time. The Sylpheed filters look as though they're not doing what they're supposed to. That is the problem, not the nature of POP3 mail.

---

