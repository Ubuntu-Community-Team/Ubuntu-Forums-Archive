---
title: "Synchronize Normal Settings With Root User Settings?"
date: 2012-10-26
forum: General Help
---

### Post by JBA2337 on 2012-10-26
I use Ubuntu 11.04.

I noticed that if I run the Configuration Editor as a normal user, any settings changes that I make are not used when I am in in root user mode. 

And if I run the Configuration Editor as root, any settings changes that I make are not used when I am in normal mode.

How can I synchronize the configuration settings so that they are the same whether I am in normal mode or root user mode?

JBA2337

---

### Post by JBA2337 on 2012-10-28
In another forum I found the answer to my question.

You don't synchronize normal settings with root user settings.

Configuration editor (Gconf-editor) settings are individual to the user account being used. Root has its own settings, and the computer user has his own settings. The two are not the same. This is by design. When you are operating as root, you are using the root user's profile, and when you're operating as yourself, you're using your personal profile. Each has its own permissions and ownership, tied to that particular account. They're not intended to be the same.

JBA2337

---

