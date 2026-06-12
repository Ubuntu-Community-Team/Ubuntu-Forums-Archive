---
title: "chmod 777?"
date: 2007-05-04
forum: General Help
---

### Post by Linkerator on 2007-05-04
I'm still a bit new to Linux. Thanks to you guys for helping out.

I'm playing Starcraft on WINE. It works well (spare a bit of lag, but no matter). Now, I'm trying to play on Battle.net and it crashes immediately after. I've heard I must chmod 777 the Starcraft directory. I know where it is (~/.wine/drive_c/Program Files/Starcraft/), but I don't know much about this chmod stuff, other than it gives permissions to edit files.

Could somebody please help me with how I'm supposed to chmod this?

Thanks in advance (I don't like thanking afterwards, bumps the post, blocking out others that need help).

---

### Post by dead_end on 2007-05-05
try this....

```
chmod 777 ~/.wine/drive_c/Program Files/Starcraft
```

if it complains then try it using sudo

---

### Post by Linkerator on 2007-05-05
```
sudo chmod 777 ~/.wine/drive_c/Program Files/Starcraft
chmod: cannot access `/home/<NAME>/.wine/drive_c/Program': No such file or directory
```

I get that. My wine folder is hidden. Maybe somehow un-hiding it will make it work?

---

### Post by CocoAUS on 2007-05-05
You can't have spaces in the command line.  To include a space in a file name, either put the entire location in quotes, or put a backslash before the space.  So, Program Files would be Program\ Files.

---

