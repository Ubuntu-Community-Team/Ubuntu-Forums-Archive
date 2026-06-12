---
title: "item in home directory denies me permission"
date: 2022-01-29
forum: General Help
---

### Post by Richard-S on 2022-01-29
I run Ubuntu 20.04. I have a folder in my home directory for Virtual Box. I recently copied it from another hard drive into my home directory. Then I ran chown -R and chgrp -R making me the owner. When I try to gain access to that directory I am told i don't have permission.

How do I get permission?

Richard

---

### Post by HermanAB on 2022-01-30
See what are the permissions exactly:
$ cd
$ ls -al

Now you should be able to tell what is the matter.

---

### Post by Richard-S on 2022-01-30
Thank you sir.

We never seem to learn not to assume things. I assumed that chown -R would change ownership of all of the files and directories inside.

Richard

---

### Post by Impavidus on 2022-01-30
> **Richard-S said:**
> I assumed that chown -R would change ownership of all of the files and directories inside.
According to the manual, it does.

---

