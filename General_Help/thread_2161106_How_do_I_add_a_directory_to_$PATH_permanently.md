---
title: "How do I add a directory to $PATH permanently?"
date: 2013-07-09
forum: General Help
---

### Post by JRV on 2013-07-09
I am using:```
export PATH=$PATH:$HOME/arm-2008q3/bin
```

I need to run the command every time I start the terminal.

Is there a way to add the directory to the $PATH permanently?

---

### Post by JRV on 2013-07-09
I am using:```
export PATH=$PATH:$HOME/arm-2008q3/bin
```

I need to run the command every time I start the terminal.

Is there a way to add the directory to the $PATH permanently?

---

### Post by papibe on 2013-07-09
Hi JRV.

You can add that line to your **~/.bashrc** for personal use, or add the path to the list in **/etc/environment** to set it system wide.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by Lars Noodén on 2013-07-09
You could append it to ~/.bashrc or ~/.profile but perhaps that method is deprecated :

[https://help.ubuntu.com/community/EnvironmentVariables#Session-wide_environment_variables](https://help.ubuntu.com/community/EnvironmentVariables#Session-wide_environment_variables)

---

### Post by cariboo on 2013-07-09
Merged duplicate threads.

---

### Post by JRV on 2013-07-09
Thank You Lars Noodén, I added it to .profile.

cariboo907 - Sorry about the double post, there was a long delay and I didn't think it went through.

Thread marked solved.

---

