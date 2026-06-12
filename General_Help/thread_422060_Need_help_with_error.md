---
title: "Need help with error"
date: 2007-04-24
forum: General Help
---

### Post by nealmohanp on 2007-04-24
When i log into my account it says the language and date you save cannot be saved cause there is something wrong with the file HOME/.dmrc and i need to set it to 644 permission. Anyone know what it's talking about?

---

### Post by strabes on 2007-04-24
Run this command in a terminal (Applications, Accessories, Terminal):

```
sudo chmod 644 ~/.dmrc
```

---

### Post by nealmohanp on 2007-04-25
It didn't work but thanks any way.
this is what the erroe exactly says:

"User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by others"

Some one please help me if you know how to fix it.

---

### Post by Darko-TheRaven on 2007-04-25
try running this command in the console:
```
sudo chown *yourusername*:*yourusername* /home/*yourusername*/.dmrc

```
this will ensure you own the file then type:
```
sudo chmod 664 /home/*yourusername*/.dmrc

```

I wouldn't use the ~ shortcut because sudo might be interpreting ~ as '/root/'

---

### Post by nealmohanp on 2007-04-25
Thanks but it didn't work iam gonna reinstall ubuntu. I think the problem occured because i was messeing around with the files
](*,)

---

