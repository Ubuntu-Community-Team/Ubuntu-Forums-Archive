---
title: "Launcher to shutdown the computer."
date: 2007-03-23
forum: General Help
---

### Post by glore2002 on 2007-03-23
Hello!

I am trying to create a launcher to shutdown the computer (for instance, at 9pm everyday).
What should I do (detailed explanation, Please!!! :-) to create that launcher?

Thanks in advance for your help.

G.Lorenzo.-

---

### Post by alamba on 2007-03-23
One option is setting up a daily cron job with a script containing init 0.

A

---

### Post by glore2002 on 2007-03-23
So, can I do that as a user or just as root?

If possible, please, let me know how the script should be.

Thanks for your valuable help.

---

### Post by ardchoille42 on 2007-03-23
You might set a cronjob with the following command
```

/usr/bin/gnome-session-save --kill

```

---

