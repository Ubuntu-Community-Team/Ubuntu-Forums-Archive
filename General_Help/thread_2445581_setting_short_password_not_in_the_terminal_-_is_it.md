---
title: "setting short password not in the terminal - is it possible?"
date: 2020-06-16
forum: General Help
---

### Post by ronjjjg8885 on 2020-06-16
hi
i want to change my system password.
i want to set a short password but not allowed to.
is there a way to bypass that that doesn't involved with using the terminal?

thanks

---

### Post by TheFu on 2020-06-16
Not that i know.   Open a terminal, type "**passwd**"
Enter the same password 3 times.
Done.

That only changes the current userid password.  i don't know what a "system password" is. Never heard of that.

---

### Post by QIII on 2020-06-16
Careful:  If you have an encrypted /home or full disk encryption, changing your password will likely result a disastrous emotional event.

Also, short passwords are inherently dangerous.  "I'll be careful."; "I live alone."; "Nobody has access to my machine.";  "I won't go on the web."  So many reasons people arrive here asking about how to fix compromised machines.

My recommendation:  Don't do short passwords.

---

### Post by TheFu on 2020-06-16
Full disk encryption isn't tied to any single userid password.  LUKS has 8 slots for different decryption methods. These are completely, 100% separate from login passwords or ldap passwords.

i have no idea how home directory encryption ties into the userid's password.

My login password is over 25 characters.

My LUKS passphrase uses a yubikey for challenge-response and the backup LUKS passphrase is over 65 random characters that I&#8217;m not sure i could actually type and there is a 2-part static LUKS paraphrase that used a long password on the beginning and a static replay from a different yubikey for the 2nd half. it must be 80 characters total, at least.

i have excellent backups on all my systems, but especially on encrypted systems. if anything bad happens to encrypted storage, a backup that can be restored is the only answer.

---

### Post by kneutron on 2020-06-16
> [COLOR=#000000]i want to set a short password but not allowed to.[/COLOR]
[COLOR=#000000]is there a way to bypass that that doesn't involved with using the terminal?

--There's no reason to NOT use the terminal, and learning how to leverage its power will get you farther than almost any GUI.  Root is allowed to do almost anything; if you want to set a short password - and you know what you're doing and accept the risks - issue ' sudo passwd useridhere ' and it might warn you, but it won't stop you.

--That said, if it's a long password for root, you might read up on how to issue certain sudo commands without a password. If you're in a home environment it doesn't matter much, but setting a short password is a huge security risk if it's business-related. If it involves ssh, there are ways to use private-key authentication instead of having to type a password.  Knowing more about WHY you want to set a short password, and what you want to accomplish, would be useful.

REFs:
[/COLOR][https://www.cyberciti.biz/faq/linux-unix-running-sudo-command-without-a-password/](https://www.cyberciti.biz/faq/linux-unix-running-sudo-command-without-a-password/)

[https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2](https://www.digitalocean.com/community/tutorials/how-to-set-up-ssh-keys--2)[COLOR=#000000]
[/COLOR]

---

### Post by grahammechanical on 2020-06-16
We can change a user password in System Settings>Users. Whether it will allow a password less than 6 characters is another matter.

Regards

---

### Post by HermanAB on 2020-06-16
It is controlled by PAM and she is a very sensitive girl and not to be messed with, since if PAM has a bad hair day, then you can be locked out of your machine.

Anyhoo, many moons ago, a younger me have made lots of money repairing Linux machines after someone decided that a four character password is kewl...

---

### Post by ronjjjg8885 on 2020-06-17
interesting ideas
thanks!

---

