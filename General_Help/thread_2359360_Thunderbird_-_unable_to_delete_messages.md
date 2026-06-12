---
title: "Thunderbird - unable to delete messages"
date: 2017-04-23
forum: General Help
---

### Post by satimis on 2017-04-23
Hi all,

Thunderbird 45.8.0
Ubuntu 16.04 desktop

I'm not allowed to delete messages.  I must do;
right click -> move to Trash
to delete it.

Neither I can create a new Trash under the User because there is already a Trash exiting.

Any advice?  Thanks

Regards
satimi

---

### Post by TheFu on 2017-04-23
I use thunderbird.

Once a week or so, I'm unable to delete messages.  It is usually due to another client having locked the message (somehow). My email server uses IMAP, so I don't know if this would be an issue with POP3S accounts.

The fix is to shutdown thunderbird and restart it. That has always fixed it for me.

If that didn't work, I'd look at the thunderbird and system log files to see what they show.  Might also run thunderbird with debug enabled until the next time the same problem happened.  Without logs, we don't really know what is happening.

---

### Post by satimis on 2017-04-23
> **TheFu said:**
> I use thunderbird.

Once a week or so, I'm unable to delete messages.  It is usually due to another client having locked the message (somehow). My email server uses IMAP, so I don't know if this would be an issue with POP3S accounts.

The fix is to shutdown thunderbird and restart it. That has always fixed it for me.

If that didn't work, I'd look at the thunderbird and system log files to see what they show.  Might also run thunderbird with debug enabled until the next time the same problem happened.  Without logs, we don't really know what is happening.

Hi,

Thunderbird is running on a VM.  I have tried re-boot VM to retart Thunderbird and it didn't help.

I have looked at /var/log and couldn't find Thunderbird log file there?

Regards
satimis

---

### Post by SeijiSensei on 2017-04-23
Thunderbird "deletes" messages by moving them to Trash.  You can delete them entirely by right-clicking on Trash in the folder tree and choosing "Empty Trash."

---

### Post by satimis on 2017-04-23
> **SeijiSensei said:**
> Thunderbird "deletes" messages by moving them to Trash.  You can delete them entirely by right-clicking on Trash in the folder tree and choosing "Empty Trash."
Hi,

Thanks for your advice.

That is what I'm now doing to delete the messages, moving them to Trash first and then "Empty Trash".

Regards
satimis

---

### Post by walts48 on 2017-04-24
Use Shift and Delete to bypass the Trash folder, but make sure you really want to delete those messages.

---

### Post by TheFu on 2017-04-24
Ok - in my case, when I delete the message, it comes back at the next msg list refresh and does NOT get moved or copied to the trash.  However, if I restart thunderbird, then I can delete message.  I think it happens because there are multiple clients connected via IMAPS to the IMAPS server sitting on/viewing the same message.  Somehow it locks the message so it cannot be removed.  I have 4 possible clients - a desktop, laptop, Phone and/or tablet, each with the same access to the same messages.

I hope the OPs issue isn't as easy as "delete" doesn't work. It has to be more complex than that folks.

---

### Post by dragonfly41 on 2017-04-24
I sometimes see "deleted" messages reappearing in Thunderbird.
I am purging lots of old messages and I now go to the IMAP server for such purging.

---

### Post by SeijiSensei on 2017-04-24
> **TheFu said:**
> I think it happens because there are multiple clients connected via IMAPS to the IMAPS server sitting on/viewing the same message.
IMAP does lock messages so I can see this happening when you have multiple clients all open at the same time and viewing the identical message.

---

