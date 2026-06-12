---
title: "Copy On Write Filesystem available?"
date: 2007-12-19
forum: General Help
---

### Post by jimcooncat on 2007-12-19
I'd like to set up a copy-on-write (cow) filesystem for use in web development. I'm sure such a system has other good uses as well. For example, this is what I'd like my users to be able to do:

[LIST]
[*]In place is an original /var/www directory.
[*]Enter a copy-on-write command, and it creates a /var/draft directory.
[*]Web author makes changes to the draft.
[*]Manager reviews the draft, likes the changes, and enters a "publish" command.
[*]Changes get merged back into /var/www. A new, fresh /var/draft directory gets created for the next round.
[/LIST]

I'd like to save on disk space. Currently I'm copying the whole website to a draft directory, and it's very slow, wasteful, and not-so-nice to use.

I first thought about using LVM snapshots and rsync to make this functionality, but the problems with these snapshots is (apparently) they don't survive a reboot. There is probably some way to write a script using hard links, and some fuse filesystem, but there must be an easier way.

Update: I've found Unionfs and Aufs, they look as if they'll meet my needs. I've googled over thirty pages each on them, and while I've printed the best docs I can find, they're not very understandable. I'll work through them over the holiday, but if you can give me some pointers, please post 'em!

---

