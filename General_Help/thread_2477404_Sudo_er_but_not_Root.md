---
title: "Sudo: er but not Root"
date: 2022-07-24
forum: General Help
---

### Post by jacksonguitars on 2022-07-24
Hello! Is there a way of making a non-admin user a sudo: er but not a root-user (that is prevent sudo -i)?
Thank you!

---

### Post by Impavidus on 2022-07-24
You can configure sudo so that it allows specific users to run specific commands: [https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

Don't allow these users to run any command that allows them to drop to a shell (like a shell, or some program that allows the user to open a shell (like vim), or any executable writable or replaceable by this user, or any tool that can be used to replace executables, like mv or cp or any text editor), or you could just as well allow them to open a shell directly with sudo -i.

---

### Post by jacksonguitars on 2022-07-24
Thank you sir. My regular user is now running ufw and iftop as a sudoer.

---

### Post by TheFu on 2022-07-24
Please be kind to the community here and use the "Thread Tools" button to mark your thread as SOLVED, when it is.  Help others from wasting their time, please.

---

### Post by jacksonguitars on 2022-07-26
Sorry, sir

---

