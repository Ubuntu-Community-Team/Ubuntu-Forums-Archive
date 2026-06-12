---
title: "Return full path"
date: 2007-11-14
forum: General Help
---

### Post by pylon42 on 2007-11-14
Is there some basic command that returns the full path of a file? For example.

cd /home/me/blah/file
*someCommand* file
output: /home/me/blah/file

Or anything remotely close to that?

---

### Post by vambo on 2007-11-14
What about 
```
locate <file>
```

---

### Post by kebes on 2007-11-14
The command "pwd" returns the current working directory, so you can probably use that, and concatenate it with the filename:
```
echo `pwd`/`find filename`
```

---

### Post by pylon42 on 2007-11-14
GAH!

Thank you both... I'm all set.

---

