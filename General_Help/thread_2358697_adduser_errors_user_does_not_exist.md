---
title: "adduser errors user does not exist"
date: 2017-04-16
forum: General Help
---

### Post by miked6127 on 2017-04-16
I am trying to create a new user using several options but I am getting an error when executing the following command:

adduser --shell /bin/bash --gecos 'Steve Smith' --ingroup math --add_extra_groups science steve

The error says: adduser: The user 'science' does not exist

it is picking up the additional group of science as the user and not steve. From looking at the man page for adduser, I do not see where I went wrong.

---

### Post by steeldriver on 2017-04-16
AFAIK --add_extra_groups doen't take an argument - it is just a boolean flag (equivalent to setting ADD_EXTRA_GROUPS to 1 in adduser.conf) that causes the user to be added to the **pre-defined** list of EXTRA_GROUPS given in your adduser.conf file (which by default are "dialout cdrom floppy audio video plugdev users")

---

