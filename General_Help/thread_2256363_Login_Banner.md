---
title: "Login Banner"
date: 2014-12-11
forum: General Help
---

### Post by Nxion on 2014-12-11
So I am having a real hard time finding the correct way to add a warning banner to Ubuntu 14.10. Im using Unity and just want a banner to display warning users  and having them have to accept it.

This is what I want the warning banner to look like:

> WARNING NOTICE TO USERS: Systems Are Monitored

 This information system is monitored and is for authorized uses only.

 --------------- Be aware you have no privacy on these systems. --------------

    All users of this system and all information on this system are
    subject to interception, monitoring, recording, copying, auditing,
    and inspection at the discretion of COMPANY. By using or accessing
    this system, you consent to and permit all of the above without
    limit as to when such action may be undertaken.

    Unauthorized or improper use of this system may result in
    disciplinary, administrative, civil, and/or criminal penalties.

    LOGIN to acknowledge and agree with these terms and conditions or
   DISCONTINUE all efforts to access or use this information system

 I know there is a lack of info so if anyone needs more info to help me out plese let me know!

---

### Post by lah7 on 2014-12-11
Lightdm is the login manager, take a look here on running a start-up script before a user logs in:
[http://askubuntu.com/questions/74189/run-a-startup-script-with-lightdm](http://askubuntu.com/questions/74189/run-a-startup-script-with-lightdm)

In summary, write a simple shell script and add the line **"display-setup-script=[COLOR=#b22222]/path/to/some/script[/COLOR]"** to [B]/etc/lightdm/lightdm.conf
[/B]
You could use **zenity** in the script, which will produce a graphical dialog. It's installed by default on Ubuntu.
For example: 
```
zenity --info --title="Warning Notice to Users" --text="Your Message Here" --ok-label="I accept"
```

Type this into a terminal for more possible uses with Zenity:
```
zenity --help-all
or
man zenity
```

---

