---
title: "file ownership"
date: 2005-06-28
forum: General Help
---

### Post by chasesjr on 2005-06-28
How do I establish file ownership so that I may make changes to that file?


      Thanx


       Chas

---

### Post by Xian on 2005-06-28
Assuming the following:

1. Your user and group name is chasesjr:chasesjr.
2. The file you are wanting to gain ownership of is called file_name.
3. It is located at /home/chasesjr

Then this is the command you would issue:
```
 $ sudo chown chasesjr:chasesjr /home/chasesjr/file_name
```

---

### Post by dfghost on 2005-06-28
in terminal sudo chown [username] [filename]
or for groups sudo chgrp [groupname] [filename]
or for permissions sudo chmod xxx [filename]

for chmod, the first x is owner, second x group, and third x others

the codes are 1-execute, 2-write, 4-read or any addition off them to get what you want

---

