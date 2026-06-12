---
title: "Not able to set systemwide path"
date: 2014-07-01
forum: General Help
---

### Post by Stijn_T on 2014-07-01
Hi,

I have been trying for days to add some directories to the path in ubuntu 14.04 in a way that is set for all users instantly.
I tried creating a file in profile.d, adding the path in /etc/profile, in /etc/environment. Everytime the same: I open the terminal and the path is back to its original state.
I found something related to it being a case of interactive login and interactive not-login shells. If I open a terminal in a graphical ubuntu, it is an interactive not-login shell and ignores those files previously mentioned. If I login with an interactive login shell, the path is adjusted.
I need a way to add for instance /usr/local/bedtools/ to the path in such a way that it is available to all users, in interactive login and not-login shells.
Does anyone know how to accomplish this?

---

### Post by ajgreeny on 2014-07-01
I found this on askubuntu [http://askubuntu.com/questions/60218/how-to-add-a-directory-to-my-path](http://askubuntu.com/questions/60218/how-to-add-a-directory-to-my-path) with a quick search, but have no experience of using it so be prepared to find that either it does not work, or for others to tell you another way to add the new $PATH variable.
> To set it system wide, append the line ```
export PATH=/path/you/are/adding:$PATH
``` to the end of /etc/profile.

  To add the directory for only the logged-in user, append the same line to ~/.bash_profile.


---

### Post by Stijn_T on 2014-07-02
Thanks for the reply. Unfortunatley, that only works for a login shell.
When you log into a graphical ubuntu, it uses that path. But when you open a terminal inside that graphical ubuntu, it is no login shell and thus it doesn't read that file.
I am looking for a way so that bash also reads /etc/profile.

---

### Post by Bucky Ball on 2014-07-02
Welcome. Are you starting your commands with 'sudo'?

---

