---
title: "[SOLVED] I installed Pidgin, but how do you uninstall?"
date: 2007-08-09
forum: General Help
---

### Post by RonB123123 on 2007-08-09
I installed Pidgin, but how do you uninstall?

I searched a few posts and I had to execute this command but I don't have the source code and I can't find any folder that contains it.
```

sudo make uninstall

```

I looked through Synaptic and I looked under local or obsolete, but I could not find Pidgin.

I have Pidgin 2.0.2 and I can't find the source code in order to uninstall it. Could anyone help me?

Edit: I found the source finally on sourceforge.net. Downloaded it and extracted all the files to the desktop. Then opened the terminal and navigated to the new directory and ran "./configure" and then "sudo make uninstall" and it worked! :)

---

### Post by mcduck on 2007-08-09
If you installed Pidgin using .deb packages you can just run 'sudo apt.-get remoe pisgin' or use Synaptic to find & remove it.

---

