---
title: "FireStarter Login Startup Error"
date: 2005-04-28
forum: General Help
---

### Post by XDevHald on 2005-04-28
To keep it short, I installed Firestarter, I set the gksudo for the session, so that is all setup, the thing is, when I logout, and log back to see if it starts up, well it does, but it gives me an error box.

[b]You must have root privileges to open Firestarter.

[/b]Not sure if anyone had this same problem and was able to fix it, if so, what do I need to do to fix this error?

Cheers!

---

### Post by bored2k on 2005-04-28
[http://www.fs-security.com/docs/faq.php#trayicon](http://www.fs-security.com/docs/faq.php#trayicon)

[http://ubuntuforums.org/showthread.php?t=7812](http://ubuntuforums.org/showthread.php?t=7812)

---

### Post by XDevHald on 2005-04-28
[QUOTE=bored2k][http://www.fs-security.com/docs/faq.php#trayicon]("http://www.fs-security.com/docs/faq.php#trayicon")

[http://ubuntuforums.org/showthread.php?t=7812]("http://ubuntuforums.org/showthread.php?t=7812")[/QUOTE]


Thanks bored2k :)

I did these steps and also put sudo firestarter, due to the other commands not really helping out much, I still get the same error, not sure why this is happening at all.

I put the command line in the sudoers too to give myself privileges without having to use a password.

Any suggestions?

---

### Post by bored2k on 2005-04-28
[QUOTE=BB]Thanks bored2k :)

I did these steps and also put sudo firestarter, due to the other commands not really helping out much, I still get the same error, not sure why this is happening at all.

I put the command line in the sudoers too to give myself privileges without having to use a password.

Any suggestions?[/QUOTE]
 How are you editing your sudoers? You know who have to do it with visudo command right ? not simply open it it in gedit.

Try editing with
```
export EDITOR=gedit && sudo visudo

```

---

### Post by XDevHald on 2005-04-28
I am opening it as root, and yes I did try that command you gave me as well, and I saved the file, logged out, and tried again, but it's still giving me the root erro :(

Not sure why this is happening to me only :p

---

### Post by Turin Turambar on 2005-04-28
Are you using Firestarter 1.0.3? What happens when you click on the icon in SystemTools/Firestarter?

---

### Post by XDevHald on 2005-04-28
Actually I just got it working lol, I put **sudo firestarter --start-hidden** in the Sessions.

Not sure why I didn't do this before ](*,) 

Thanks for the replies. :)

**Edit$ ~  **Ok, found the deb file at the fs-security.com website and dpkg'd it :) now running 1.0.3.

---

