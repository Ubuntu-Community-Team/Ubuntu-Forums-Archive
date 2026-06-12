---
title: "how do you lift permissions?"
date: 2007-09-21
forum: General Help
---

### Post by nerojrnde on 2007-09-21
im trying to install updates for Savage (a game)

when i attempt to extract to the folder it wont let me. even when i manually went in the folder to delete files, i was denied

basically..i think it would help if i knew the terminal command for deleting a folder. that way i can log in as root (if i knew how :P)

---

### Post by Maestro23 on 2007-09-21
If you are dealing with folders/file owned by root "/", then you need **sudo** in front of your commands.

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Delete something: use the rm (remove) command.  

> man rm

* Manual page for rm (remove).  Gives complete syntax of the command.

---

### Post by nerojrnde on 2007-09-21
ok..and how what would the command be to delete the folder?

sudo in front logs me in..but i dont know the command

---

### Post by nerojrnde on 2007-09-21
ok i managed to delete all the necessary folders..but how do i move a folder into the directory?

i tried dragging the new ones in but it denies me permission

---

