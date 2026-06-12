---
title: "[SOLVED] /etc/group corruption"
date: 2007-12-22
forum: General Help
---

### Post by clarknova on 2007-12-22
I'm running Ubuntu 7.10 i386.

Any time I add a user via gnome's User & Group control panel, my /etc/group file is effectively voided, leaving just two lines, for "nogroup" and the user I just added.

Fortunately for me, I have a backup of the file in question, which I simply copy back into place, then manually re-add a line for the new user. My /etc/passwd and /etc/shadow files remain intact. sudo fails silently, but fortunately I have a root password and I am able to su root to make the necessary changes.

I no doubt caused this problem as I was hand-editing these aforementioned files by hand in the recent past, but for the life of me, I don't know just what I might have done to cause this phenomenon.

It's a bit of a pain, as this is a public computer and I'm adding users on a regular basis. I'm sure a fresh install would correct the problem, but restoring the whole system would be a significant undertaking at this point. I could add users via CLI, but I'm trying to train others here to admin and CLI is not really an option. Furthermore, I would certainly prefer taking the opportunity to learn something from my mistake, rather than just wiping the slate yet again.

I'm not finding the like in the forums, so any hypotheses appreciated.

db

---

### Post by clarknova on 2008-02-12
Solved. And perhaps I should have given more detail on how the problem was created.

I have 4 systems in a public place, each user with his own login. When I add a user, I add him to the first system then copy from /etc/ passwd, group, shadow and gshadow. Only I had overlooked copying gshadow and this oversight was somehow depopulating my group file.

Copy all four files to the other machines, ensuring proper ownership and permissions in their destinations and the trick works. I'll be replacing this headache with an edubuntu thin-client network in the near future.

db

---

