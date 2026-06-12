---
title: "Kontact groupware broken in Gutsy?"
date: 2007-10-22
forum: General Help
---

### Post by eurgain on 2007-10-22
Hello, all

I use Kontact's simple groupware system that uses kmail and a disconnected imap account to provide groupware functions.  To be more precise, I *used to* use this, because since I upgraded to Gutsy, it has stopped working!

I have turned on groupare fucntionality in the misc settings, and added the resource of type "Calendar on IMAP server via kmail", but I do not then see any calendar entries.  Strangely, there is nowhere to set the resource in Contacts  (there is normally a setting on the left-hand pane in the default view), although I can set up the resource in the KDE control panel (the full version, not the Kubuntu cut-down one).  Of course, I cannot see my contacts either!

I have set this up a dozen times before without problem, and I do not think I am doing anything different, so maybe it is a bug in Gutsy.

Has anyone got this working?

A

---

### Post by Eckat on 2007-10-22
I've the same problem. I seems to be a bug .. :mad:
Here are more information, but they are not very helpful: 
[https://bugs.launchpad.net/ubuntu/+source/kdepim/+bug/139433](https://bugs.launchpad.net/ubuntu/+source/kdepim/+bug/139433)

---

### Post by Xianath on 2007-10-23
I found the solution in the bug report thread Eckat pointed out. Assuming you already have IMAP groupware enabled in KMail and the "Hide IMAP folders" checkbox ticked, try the following:

1. Quit Kontact as well as the KOrganizer reminder daemon
2. Edin ~/.kde/share/config/kmailrc
3. Find your IMAP account entry ( [Account #] ) and note the ID and Folder entries. They should be some large integer numbers (equal, at least for me)
4. Look for the [IMAP Resource] section. It should contain three lines but in my case it only contained two. Add the missing line manually. If all three lines are there but the Account and FolderParent numbers don't match the ones from step 3., fix that. The section should look like this:

```
[IMAP Resource]
TheIMAPResourceAccount=402492544
TheIMAPResourceEnabled=true
TheIMAPResourceFolderParent=402492544
```

5. Start Kontact, keeping the other hand's fingers crossed :)

Cheers,
Peter

---

### Post by Eckat on 2007-10-23
It doesn't work for me :(. Any other ideas..?

---

### Post by whiskybar on 2007-10-25
Thank you! That fixed it for me.

```
[IMAP Resource]
TheIMAPResourceAccount=2044515029
TheIMAPResourceEnabled=true
TheIMAPResourceFolderParent=.2044515029.directory/INBOX

```

TheIMAPResourceAccount was missing. TheIMAPResourceFolderParent is funny because my IMAP server is Courier (but this line was there already).

---

