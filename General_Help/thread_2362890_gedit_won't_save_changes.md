---
title: "gedit won't save changes"
date: 2017-06-03
forum: General Help
---

### Post by dunique on 2017-06-03
I am trying to install SimpleScalar on my Ubuntu which runs on virtualbox.

While installing my simpleutils

I needed to replace all instances of yy_current_buffer to YY_CURRENT_BUFFER in the simpleutils-990811/ld/ldlex.l file. 

After making these changes, I clicked on save. 

I discovered when I reopen the file, the changes doesn't save. 

What could be the cause and what do I do? 

Thanks

---

### Post by yancek on 2017-06-03
Modifying files outside the user /home directory usually requires root privileges so you could try opening gedit in a terminal prefacing it with sudo.

---

### Post by dunique on 2017-06-03
Thank you. 

Resolved!

---

### Post by ajgreeny on 2017-06-03
However, you should **never use sudo for any GUI applications** as you may find that after doing so you are unable to login as your username.
See [COLOR="#FF0000"]Root-Sudo[/COLOR] in my signature for details.

Use **sudo -H gedit** if you must use a GUI application, or once you get used to it it is very easy to use **sudo nano** to edit files.

---

