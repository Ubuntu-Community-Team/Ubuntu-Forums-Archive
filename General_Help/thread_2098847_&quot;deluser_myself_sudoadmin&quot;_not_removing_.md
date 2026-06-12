---
title: "&quot;deluser myself sudo/admin&quot; not removing sudo privelage"
date: 2012-12-27
forum: General Help
---

### Post by haplorrhine on 2012-12-27
In the terminal, I entered
sudo deluser myself sudo
and
sudo deluser myself admin

Why do I still have root privileges under this user?

[COLOR=DimGray]I made a new user and added it to "sudo" and "admin."  I want to have someone else set the password for it, so I can lock myself out of the hosts file when URLs are blocked.[/COLOR]

---

### Post by steeldriver on 2012-12-27
Have you logged out / back in? a user's group memberships are only read on login afaik

> **haplorrhine said:**
> [COLOR=DimGray]I made a new user and added it to "sudo" and "admin."  I want to have someone else set the password for it, so I can lock myself out of the hosts file when URLs are blocked.[/COLOR]

No idea what that means :confused:

---

### Post by haplorrhine on 2012-12-27
I tried logging out and logging in, and I still had root privileges.  When I read your post, I did a restart.  It worked.  Problem solved. Thanks.

I had the bottom text in grey because it wasn't important.

---

