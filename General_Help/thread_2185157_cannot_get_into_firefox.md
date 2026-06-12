---
title: "cannot get into firefox"
date: 2013-11-01
forum: General Help
---

### Post by user987 on 2013-11-01
i am running a live cd on a usb drive in mint 13 lts.
firefox was running fine, i then updated every thing and the next day when i boot up and use FF, it say profile missing or inasseible.

I tried some of the solutions in the forum and nothing.

i then went to terminal and put  gksudo firefox and i was in.

prior to update FF was at version 12 now it is latest version 25

how can i fix the problem so i can use FF from the task bar and not use terminal.

from my research it seems to be a permission problem in FF.

Also when i was in FF via terminal it was slow so i got out and went back to XP to type this.

---

### Post by Kirboosy on 2013-11-01
I would recommend trying the following guide from Mozilla!

[Managing Profiles Firefox]("https://support.mozilla.org/en-US/kb/profile-manager-create-and-remove-firefox-profiles#w_starting-the-profile-manager")


Hope that helps!
~Caboose

---

### Post by Impavidus on 2013-11-01
Your profile must be owned by root. Try to repair it with```
sudo chown -R yourusername:yourusername ~/.mozilla
```
Firefox 12 was released in April 2012. Good you upgraded. Although Firefox is reasonably secure (but version 12 isn't), it remains a web browser and therefore a program with an outside connection to many malicious sites. For security I never run Firefox with root privileges, which may have caused your profile to be root-owned in the first place.

---

### Post by protoss96 on 2013-11-01
Can you just post here the output from terminal? It helps a lot.

---

### Post by user987 on 2013-11-02
thanks for input will try some of the solutions and let you guys know.
also how do i post terminal results?
not fimilar with linux commands.

---

### Post by user987 on 2013-11-02
impavdis,
              i never setup user name or password since i am running from a live cd on a usb drive.
how do i use your command sudo chown without user name?

---

### Post by Impavidus on 2013-11-02
Oh, sorry. I was under the impression that you used a live disk because you had a problem with Firefox.

You have persistency, else you wouldn't be able to save anything. The live disk automatically has one user, named ubuntu, who can use sudo and who has an empty password. Still, I don't think live disks are really fit for daily usage. They're mostly for testing hardware compatibility, installing and fixing problems. When you're confident your system works, try a full install.

---

