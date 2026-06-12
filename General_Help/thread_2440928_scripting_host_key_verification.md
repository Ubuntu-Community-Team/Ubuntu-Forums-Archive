---
title: "scripting host key verification"
date: 2020-04-16
forum: General Help
---

### Post by jyanga on 2020-04-16
Hi!

I am trying to create a script where host key verification is automated.  Here is part of my script.

```
ssh-keyscan host1.example.com >> ~/.ssh/known_hosts
sshpass -f file.txt ssh-copy-id -i ~/.ssh/id_rsa.pub user1@host1.example.com[COLOR=#000000][FONT=Menlo]
[/FONT][/COLOR]
```
[COLOR=#000000][FONT=Menlo]
After running the first line, I found out that though the keys are in the known_hosts file I am still being prompted for verification.

This works on Ubuntu 16.04 but not on 18.04.  Any suggestions on how to get it working on 18.04?

Thank you in advance.  :)

Regards,
J[/FONT][/COLOR]

---

### Post by jyanga on 2020-04-16
Updating [FONT=Menlo][COLOR=#000000]and rebooting seems to have resolved the issue.  I apologize for the inconvenience.[/COLOR][/FONT]

---

