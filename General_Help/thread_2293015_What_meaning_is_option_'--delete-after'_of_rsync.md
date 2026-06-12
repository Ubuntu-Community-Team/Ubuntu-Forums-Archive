---
title: "What meaning is option '--delete-after' of rsync?"
date: 2015-09-01
forum: General Help
---

### Post by ruwan2 on 2015-09-01
Hi,

I see the following command on-line:
rsync -rl --delete-after --safe-links [email]pi@192.168.1.PI[/email]:/{lib,usr} $HOME/raspberrypi/rootfs

Although I have check the option '--delete-after' of terminal help:

[COLOR=#0000cd]--delete-after          receiver deletes after transfer, not during[/COLOR]

It is still unclear to me.
Could you explain it to me?

Thanks,

---

### Post by btindie on 2015-09-02
Files that exist at DEST and not at SRC will be deleted once all other files have been transferred to DEST, as opposed to before or during the transfer.

---

