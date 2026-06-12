---
title: "Active Directory and Password Update"
date: 2019-12-19
forum: General Help
---

### Post by bpearson on 2019-12-19
Hey folks!

I've skimmed though the forum but didn't see anything exactly like what i'm looking for, and not sure if this is in the correct section.

Windows domain with Active Directory, I can join the domain perfectly fine using PBIS and all is good there, but what do I do when the user's domain password needs changed (as in user must change password on next login).
When I try to sign in via the GUI it recognizes the password that I created, prompts the user to change password (old then new twice), but fails to register the new password and fails.
I've double checked the password complexity requirements and have checked the GPO for password age - its minimum is set to 1 day (of which I've been trying this over a few days).

Some of the solutions that were provided with odd user logins suggested using the terminal to log in with, but I get the same results - old is acknowledged, prompt for new, but then nothing.

Not a Linux guru by any means, but can figure most things out with a little guidance.

We're running this on a clean install of Ubuntu 18.04.3 (with the PBIS and its requirements).

Any direction would be greatly appreciated.

Thanks!

---

