---
title: "how to make myself &quot;root&quot;"
date: 2014-08-25
forum: General Help
---

### Post by nitewalker41 on 2014-08-25
I am trying to shutdown from the terminal and it says I need to be "root" to do it, when I put my password in it says it is wrong....how to I make myself root please:confused:

---

### Post by overdrank on 2014-08-25
Hi and what is the command you are using?
This may help _[RootSudo]("https://help.ubuntu.com/community/RootSudo")_

---

### Post by raptir on 2014-08-25
Ubuntu's default escalation method is [sudo]("http://linux.die.net/man/8/sudo"). sudo allows you to run commands as root while authenticating with your own password. So to shutdown your system, you would run:

```
sudo shutdown now
```

You will then be prompted for your password.

Some more information on sudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

**Be careful** when using sudo. You are completely free to break your system when using sudo, and any command that you run with sudo can do whatever it wants maliciously. Never run an application with sudo unless you know why you need to and why you want to.

---

### Post by nitewalker41 on 2014-08-25
Thanks for the help, all works find now.......thanks again to all

---

