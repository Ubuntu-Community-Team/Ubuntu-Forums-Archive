---
title: "Forgotten Information"
date: 2007-03-10
forum: General Help
---

### Post by Eminem on 2007-03-10
I don't know my login information. I don't remember setting it during the installation at all. Is there any way to retrieve the information?

Help! :confused:

---

### Post by llamakc on 2007-03-10
So you've never logged in? You could boot the LiveCD, mount the root (/) partition and cat /etc/users to look for your username, or look at the directories under /home to see if that jogs your memory.

Or reinstall.

---

### Post by Eminem on 2007-03-10
I used the Alternate Install method.

Is there a sort of default login information that I can use? :confused:

---

### Post by llamakc on 2007-03-10
Yes. You created it and have forgotten it. Either use a LiveCD to mount the root partition and look at what user directory is under /home/, hoping that reminds you what the password was, or reinstall and write the information down.

---

### Post by Eminem on 2007-03-10
I'm looking at my /home/ directory using Windows and it's empty.

---

### Post by llamakc on 2007-03-10
Does the alternate cd create an additional system user? I don't know. If it does not, the login user name would be "root" and would be the password that you created.

---

