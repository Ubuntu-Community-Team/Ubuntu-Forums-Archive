---
title: "'freetype-config' is not in your PATH"
date: 2007-01-07
forum: General Help
---

### Post by beamo on 2007-01-07
I get an error telling me I have freetype 2 installed but I need to put "freetype-config" in my path. How do I do that? Thanks for the help.

---

### Post by bodhi.zazen on 2007-01-07
Depends on where is is now ...

Assuming it is somewhere in /home/your_user_name ....

You can :```
sudo ln -s /home/use_name/path/to/freetype-config /usr/bin/freetype-config
```

---

