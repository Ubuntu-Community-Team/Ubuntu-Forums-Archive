---
title: "Problem changing passwords for users in different groups"
date: 2024-02-02
forum: General Help
---

### Post by billyjimmyx on 2024-02-02
I'm attempting to use recovery mode to change my (forgotten) main user password, but when I do the system says that the account doesn't exist. I have two other accounts also on this machine, and I am able to change those passwords and log into them successfully, but not this one. The passwd file shows that the two extra accounts are in their own groups, while the one I need reads 

"groupname:x:1000:1000:accountname,,,:/home/groupname:/bin/bash". I believe that this is the problem, but I don't know how to fix it and I have files in that account that I'd like to access. 

How can I reset this password?

---

### Post by Holger_Gehrke on 2024-02-03
The problem is very simple. Just read 'man 5 passwd'. The first field is not the name of the group, it's the login name. The following fields are the password (and since Ubuntu uses the shadow-password system that field normally contains just an 'x'), the numeric user id, the numeric id of of the main group of the user, a comma separated list of 'real' information about the user (full name and address could be stored in here, but there are no rules for this field; it's often used as a comment field), home directory, and finally the shell assigned to that user. There are no group names in this file, they are all in /etc/group.

Holger

---

### Post by billyjimmyx on 2024-02-03
Thanks Holger that makes sense, I was able to change the password but now I'm stuck in a login loop, the password seems to have successfully changed but it just takes me back to log in again, I'm running version 22.04.

---

### Post by TheFu on 2024-02-03
> **billyjimmyx said:**
> Thanks Holger that makes sense, I was able to change the password but now I'm stuck in a login loop, the password seems to have successfully changed but it just takes me back to log in again, I'm running version 22.04.

Sometimes this happens when root is the owner of files in the HOME for the user. Fix that.  File ownership matters.

---

