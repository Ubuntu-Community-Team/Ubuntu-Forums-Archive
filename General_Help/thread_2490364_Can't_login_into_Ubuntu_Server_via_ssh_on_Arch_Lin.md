---
title: "Can't login into Ubuntu Server via ssh on Arch Linux"
date: 2023-08-31
forum: General Help
---

### Post by drhawes on 2023-08-31
Hello. I am trying to set up Ubuntu server on a Raspberry Pi 4, I got everything thing working. In am able to connect to the device remotely via the ssh command however it ask for the password. The default password is "ubuntu" how ever after entering it it say's "[FONT=monospace][COLOR=#000000]Permission denied, please try again" then after 3 tries it say's [/COLOR][/FONT][FONT=monospace][COLOR=#000000]"Permission denied (password)" then kicks me out. I have a Raspberry Pi 4 Model B 4GB with [/COLOR]Ubuntu Server 22.04.03 LTS (64-bit).
[/FONT]

---

### Post by Holger_Gehrke on 2023-09-01
Are your usernames identical between client and server ? If you just run 'ssh "Server Name or IP"' ssh assumes that you want to use the name you're logged in under locally on the remote end too. If that's not the case, you need to either add the name to the destination ('username@servername_or_server_ip') or use the option '-l "username"'.

Holger

---

### Post by drhawes on 2023-09-01
I was using the wrong IP address. I am able to connect to it now. How do I mark the post as solved?

---

