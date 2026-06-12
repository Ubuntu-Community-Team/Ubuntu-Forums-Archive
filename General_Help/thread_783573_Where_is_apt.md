---
title: "Where is apt?"
date: 2008-05-05
forum: General Help
---

### Post by JohnJSal on 2008-05-05
Hi everyone. I just tried using apt to search for programs to install, but I get the message

```
bash: apt: command not found
```

What do I do now? Shouldn't this be an integrated part of the Linux install?

---

### Post by Monicker on 2008-05-05
"Apt" by itself is not a command.  You probably want to use apt-cache and apt-get.


```
apt-cache search searchterm
sudo apt-get install programname
sudo apt-get remove programname
```

---

### Post by retrow on 2008-05-05
Use Add Remove, or Synaptic.

---

### Post by FakeOutdoorsman on 2008-05-05
You can also:
```
aptitude search foo
```

---

### Post by JohnJSal on 2008-05-05
> **Monicker said:**
> "Apt" by itself is not a command.  You probably want to use apt-cache and apt-get.


```
apt-cache search searchterm
sudo apt-get install programname
sudo apt-get remove programname
```

Ah, thanks! I didn't realize there was no space between apt and -cache, for example. I thought it was an argument.

---

