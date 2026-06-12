---
title: "redirect wall output to a script"
date: 2013-07-06
forum: General Help
---

### Post by szafran on 2013-07-06
Hi,

I'd like to know if there is a way to redirect messages from wall to a script ? (in addition to them being shown on the wall)

---

### Post by gordintoronto on 2013-07-06
What do you mean by "wall"?

---

### Post by tgalati4 on 2013-07-06
*Wall* takes interactive input from the command line, using Control-D to quit the input and send the message to all logged in users.  *Wall* also takes a text file as the message.  So presumably your script can both create the message file, use *wall* to broadcast it, and then have another script read the message file to operate on it.

This is what you are trying to do, but it doesn't work:

tgalati4@Mint14-Extensa ~ $ wall > /tmp/wall_test.txt
wall: cannot get tty name: Inappropriate ioctl for device

You might be able to use *tee* and *wall* together, but that is left for you to play with.

---

### Post by szafran on 2013-07-07
I'm not using wall to show any messages.
I wan't to get system messages shown just like wall does and direct them to a script.
Eg. when the OS is shutting down it sends a message - that message is what I want redirected to a script.

---

