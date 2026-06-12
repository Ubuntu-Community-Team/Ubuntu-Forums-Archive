---
title: "Start up scripts"
date: 2006-10-15
forum: General Help
---

### Post by dmsn on 2006-10-15
Hey im old slackware user and there i use /etc/rc.d/rc.local
to make programs to start up with boot.
How do i start exempel sshd with boot in ubuntu, sudo needed too? :P


Thanks

---

### Post by dagnabit dang doohickey on 2006-10-15
Put your script in the /etc/init.d directory.

After you make the script executable, use the following command to add the symbolic links:
```
update-rc.d your_script_name defaults
```

If you ever want to remove the script from the startup sequence, use this:
```
update-rc.d -f  your_script_name remove
```

You might want to give a look at the update-rc.d man page for further options you can use with the command.

BTW: I ran across this [startup script generator]("http://rob.pectol.com/content/view/17/33/") a couple of days ago that might come in handy.

---

