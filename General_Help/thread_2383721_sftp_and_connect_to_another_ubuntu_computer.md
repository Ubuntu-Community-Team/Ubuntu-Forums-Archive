---
title: "sftp and connect to another ubuntu computer"
date: 2018-01-29
forum: General Help
---

### Post by norcal on 2018-01-29
I was using sftp to access my files on ubuntu 16.04 box. then I reinstalled to 17.10  and gave it a different name. 
Now when I try and access it through other locations , connect to server in files it remembers the old name . even though the address is right it won't let me in. 

My question is how do I delete this information.  I already cleared the ssh conf file. didn't work.

---

### Post by TheFu on 2018-01-29
mv ~/.ssh/ ~/.ssh-really-old

Then generate new ssh-keys (ssh-keygen), use ssh-copy-id to push them to the other systems.  When you connect from the shell, if there are issues in the known-hosts or authorized hosts files, a warning will be displayed.  If the connection isn't allowed and the messages aren't sufficient, you can increase the "verbosity" by adding -vvv to the options.

---

### Post by norcal on 2018-01-31
found answer
go to passwords and keys and delete entry.

---

