---
title: "recover administrator password"
date: 2007-05-23
forum: General Help
---

### Post by jbrown96 on 2007-05-23
I have been using a single administrator account for all purposes. Today, I created separate administrator account. However, the new password does not work, and I can't access the user menu because I don't have administrator privileges anymore.

How can I get the password back?

---

### Post by codesplice on 2007-05-23
So the account that you can still login on does not have administrator access right?

---

### Post by wuhaa on 2007-05-23
I don't think you can get it back, but you can reset it by rebooting the system in single user mode!!!


Hit [COLOR="Red"]e[/COLOR] on the grub screen.

Choose the like that says something like

[COLOR="Red"]/boot/vmlinuz-2.6.20-15-generic root=UUID=d63fb4e2-0eb8-47f8-9b7c-734b78cf18b8 ro quiet splash[/COLOR]

and hit the e key to edit

at the end of everything put -s so it looks like

[COLOR="Red"]/boot/vmlinuz-2.6.20-15-generic root=UUID=d63fb4e2-0eb8-47f8-9b7c-734b78cf18b8 ro quiet splash -s[/COLOR]

and hit [COLOR="Red"]b[/COLOR] to boot

The system should boot in single user mode. Then type in passwd  and set a new password!!!

Excuse my english

---

### Post by codesplice on 2007-05-23
Hey, that's pretty slick.

Hope that helps you out **jbrown**.

---

### Post by jbrown96 on 2007-05-23
Thanks Wuhaa for the help. I'll try it when I get home. 
I can still log into my old account, but have no administrator privileges (i.e. no updates, installs, etc.). I've read about the single-user mode, but it doesn't sound like it will work. 
I have an external HD, so I'll back everything up and reinstall it looks like.

---

