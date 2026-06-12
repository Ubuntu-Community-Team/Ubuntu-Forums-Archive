---
title: "User Configuration question"
date: 2007-05-06
forum: General Help
---

### Post by hyde200j on 2007-05-06
Hello everyone,
So interesting story...I have two partitions for / and /home respectively, but for the longest time after installing feisty, I was not mounting my /home partition (so /home/user is on the same partition as everything else).  Well I finally got around to formatting the other partition and attempted to make the switch.

Simply put, I copied the /home/user directory over to the now blank partition.  Then I changed fstab accordingly and restarted.  It mounts and the files are all accounted for (I think), but everything is back to default.  Keyboard shortcuts, desktop, keyring all back to original.  It's the same user name and nothing should have changed, but it did.

Quite likely there is some hidden file that defines this that was not copied, but what is it and why would it not have been copied with everything else?  It's not a tremendous challenge to change this all manually again, but I am curious.

Any help would be appreciated...at least the location of the above-mentioned configuration.

Thanks.

And since I don't get to say this often, Feisty is truly amazing!  Never have I been so impressed by a release, nor have I done so little hacking with a fresh install.

---

### Post by Soarer on 2007-05-06
It sounds like you haven't copied the hidden files, which contain your settings.

Control-H should show them, if they are there.

---

### Post by hyde200j on 2007-05-06
Nope, they should all be accounted for.
Thanks for the suggestion though.

This is very strange indeed.  Perhaps some permissions are out of order.

---

### Post by hyde200j on 2007-05-06
Fixed.
Somewhere along the way, many of the hidden files got changed to root owner and group.  I tried changing these settings, but obviously something still wasn't changing.
I recopied, this time everything owned by <user> and it worked.

I can't imagine too many others benefiting from this, but the lesson (as obvious as it is) is to make sure everything in /home/user should be owned by user.

Thanks.

---

### Post by Soarer on 2007-05-06
Glad you got it sorted, and thanks for letting us know.

Should be plain sailing from now on :)

---

