---
title: "Root?"
date: 2008-05-22
forum: General Help
---

### Post by Yappy on 2008-05-22
I boot up and key in my ID and password.

Does it meant that I am in root directory as there is no other user using my computer?

How do I know that I am in root directory and with the right that come along?

Thank you.

---

### Post by cdtech on 2008-05-22
When you log in, you are just a user.

You can't log in as root (well you could), but you can become root once your logged in:
sudo -s

You should see a prompt:
root@yourcomputer:

---

### Post by prshah on 2008-05-22
> **Yappy said:**
> 
Does it meant that I am in root directory as there is no other user using my computer?

Open a terminal (Applications-Accessories-Terminal) and give the command ```
whoami
``` That will show your userid. You are a normal user with administrative rights but _not_ root's rights.

To get the rights of root, prefix any command with "sudo". Eg,```
sudo whoami
``` will return "root" showing that if you use sudo, for the duration of the command, you are root.

---

