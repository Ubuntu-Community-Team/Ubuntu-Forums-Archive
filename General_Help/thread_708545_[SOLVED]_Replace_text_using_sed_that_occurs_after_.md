---
title: "[SOLVED] Replace text using sed that occurs after a given character (last part of a l"
date: 2008-02-26
forum: General Help
---

### Post by Eliseo on 2008-02-26
I have a file like this:

```
server.ip=localhost
server.name=myserver
server.port=7001
```

I need to be able to change the part that comes after the '='.

This needs to be done inside a bash script using sed or any other command.

Any clues? Thanks! :)

---

### Post by pointone on 2008-02-26
```
sed -i -e 's/=.*/=new_value/' /path/to/file
```

---

### Post by Eliseo on 2008-02-26
That worked, thanks!

---

