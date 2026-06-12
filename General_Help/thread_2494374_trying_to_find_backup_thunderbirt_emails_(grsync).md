---
title: "trying to find backup thunderbirt emails (grsync)"
date: 2024-01-14
forum: General Help
---

### Post by StrobeWylan on 2024-01-14
I used Grsync to backup my whole system on Xubuntu on a regular schedule. The computer crashed last year and I now need to find some old emails within the backup on the external hard drive. I was using Thunderbird and still do. 
I don't have a clue where to start. 

Thank you in advance.

sorry for the typo in the title

---

### Post by SeijiSensei on 2024-01-15
Thunderbird stores everything in /home/username/.thunderbird (note the leading period). You'll see one or more directories with random names like "ab71nipn.default-release". Find the most recent directory, then look in the ImapMail folder.

If you use IMAP, some of your mail may still reside on the server.

---

### Post by StrobeWylan on 2024-01-19
I responded with a thank you post but don't see that it became part of this thread. 

Thank You for your help. I did find a file but can't figure out how to read the text. When I use Thunderbird to open it I only get a write box for a new send e-mail. I get that result if I use T-bird to thy to open any file whatever kind it is.

Any suggestions?

Thanx

---

### Post by ajgreeny on 2024-01-19
If this is now solved for you as it appears to be please mark the thread as SOLVED from the Tread Tools menu up-top.

It can be a great help to other users searching the forum.

---

### Post by SeijiSensei on 2024-01-20
You should see a ~/.thunderbird/[random profile name]/your_server_name/ImapMail/ directory in the backup. It contains the state of all your mail at the time. Try creating your account first, then close Thunderbird and replace the newly-created ImapMail directory with the one in the backup. Any better?

Once again, if you are using IMAP, your mail should still be on the server.

---

