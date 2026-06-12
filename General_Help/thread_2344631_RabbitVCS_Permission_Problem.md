---
title: "RabbitVCS Permission Problem"
date: 2016-11-27
forum: General Help
---

### Post by jo-jo-too on 2016-11-27
I'm new to Linux, so I don't understand what the permission problem I'm having is. I set up an SVN repository on a network drive, and mounted it. I can checkout with RabbitVCS, but I can't commit. When I try to do so, Rabbit creates a new file in the db folder in the repo, but then gives me an error saying that is can't set permissions on the file it just created because the operation is not permitted. I can commit from the terminal using "svn commit ...". I have tried assigning ownership of the folder to myself, and making sure that everyone has read and write access to it, but it still gives me the permission error.

Can anyone tell me why RabbitVCS can't commit to the repository?

---

### Post by jo-jo-too on 2016-11-27
Since I'm so new to Linux, I assumed I was just doing something wrong. I guess I should have checked RabbitVCS known issues, because not supporting mounted locations is one of them.

---

