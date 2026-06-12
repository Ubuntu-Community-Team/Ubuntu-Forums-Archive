---
title: "[SOLVED] Lastlog command"
date: 2008-07-01
forum: General Help
---

### Post by troythetechguy on 2008-07-01
When I run the command "lastlog" under Ubuntu 7.10, it shows user2 **never logged in**.  However, I know user2 has logged in as recently as yesterday.  I tried running the command as sudo, but this did not make a difference.

I'm running Fedora in VM, and the lastlog command works fine in Fedora, so I assume I do not have something set correctly in Ubuntu.  Any ideas or suggestions?

Thanks,

Troy

---

### Post by VMC on 2008-07-01
I have never run that command. After running it, it shows that my login was several days ago. I'm setup with auto login, so I think that lastlog info is when I used the Ctrl+Alt+F1 and logged in a virtual terminal.

---

### Post by troythetechguy on 2008-07-01
Thanks VMC for your response.  I tried what you suggested, logging in via virtual terminal rather than X, and you're correct.  When I log in through the virtual terminal, the login name is logged and can be read from with the lastlog command.

---

