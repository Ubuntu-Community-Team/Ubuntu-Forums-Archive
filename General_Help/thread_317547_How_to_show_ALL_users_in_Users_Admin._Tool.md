---
title: "How to show ALL users in Users Admin. Tool"
date: 2006-12-12
forum: General Help
---

### Post by peterx14 on 2006-12-12
Hi all,

I'm working through installing apache2 + subversion using the notes here:
[https://help.ubuntu.com/community/Subversion](https://help.ubuntu.com/community/Subversion)

and I need to create the "subversion" group (done that) and add myself and the www-data user to this group. The problem is that "www-data" doesn't show as a user which (correct me if I'm wrong) is because this user has an ID < 100 or 1000 and is considered a system user?

Anyway, I clicked Help in the user admin tool and it says:

> The Users Administration Tool main window contains the following elements:

Users list

    Shows the available users. depending on the gconf key "/apps/gnome-system-tools/users/show_all" it will show the system users too.


which is helpful; so I fired up gconf-editor, navigated my way to the specified key and checked the box beside "showall". And it makes absolutely no difference!

I logged out (in case that makes a difference) but no joy. I rebooted (those Windows habits die hard!), but again, it made no difference.

Any ideas on how to make it work?

TIA!

Peter.

---

### Post by peterx14 on 2006-12-12
In reply to my own post.... whilst I was writing, I noticed that the help file mentions the gconf entry:

/apps/gnome-system-tools/users/show_all

whereas when I go into gconf-editor itself, it shows the key

/apps/gnome-system-tools/users/showall

(missing an underscore between "show" and "all"). So I added another key "show_all" as a boolean set as true. This works.... although it didn't seem to work when I first tried it. Anyways, should I file a bug? And if so, could anyone tell me where?!

Cheers!

Peter. :-D

---

### Post by peterx14 on 2006-12-15
FWIW there is a bug filed here:
[https://bugs.launchpad.net/distros/ubuntu/+bug/74984](https://bugs.launchpad.net/distros/ubuntu/+bug/74984)

---

### Post by doddi on 2007-04-10
I have just had this same problem using the latest feisty release. So thought I would bump this useful thread.

I also noticed that the bug status is still classed as unconfirmed..can this perhaps be changed to confirmed?

I am new to linux so not sure how that side of stuff works

Cheers,

Doddi

---

### Post by bear_out_there on 2007-06-18
Got the same problem and changing the gconf settings as described above did not work.  Using Ubuntu 6.10 on an AMD box.

---

### Post by SneakyWho_am_i on 2008-05-12
> **bear_out_there said:**
> Got the same problem and changing the gconf settings as described above did not work.  Using Ubuntu 6.10 on an AMD box.

Wow. I was reading the subversion installation instructions and it said I might have to use the gconf thing if www-data wasn't in the list.
It wasn't in the list, so  followed the link. The link there wasn't particularly helpful; it only showed how to start the gconf thing. Of course I had forgotten that on the very last page it had said what to edit. I'm only a stupid user ;)

So I searched... Came here... Original poster's fix didn't work for me at all (I'm under Hardy by the way)... I wonder if it was a mistake for me to type it all in as lowercase letters??

Anyway I'm not going to play these stupid games if I can help it. Instead of wasting half an hour trying to make the two GUI programs play nice together, jump in and get your hands dirty??

"gksu" below might be "kdesu", "gksudo" or "kdesudo" or even just yucky "sudo"...:
```
gksu gedit /etc/group
```
And note that gedit might be kwrite or kedit or something....

Anyway once you've opened that, scroll all the way down to "subversion" at the bottom and change (your numbers and usernames will be different to mine) it from this:
```
subversion:x:1002:root,sneaky
```
to this:
```
subversion:x:1002:root,sneaky,www-data
```

That's all we were supposed to be doing in the first place.. Doesn't really seem worth all that fuss, does it? :D
Well I dunno, it's not a fix at all but I hope it at least helps someone to get the job done.

---

