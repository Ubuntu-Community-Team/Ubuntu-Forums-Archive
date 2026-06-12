---
title: "Writing executables to launch programs"
date: 2008-04-28
forum: General Help
---

### Post by cometa2k7 on 2008-04-28
Ok, basically I would like to launch about 3 programs on start up, but in a specific order.

I don't mind having to launch an executable, and I could force it to run on start up.

I know how to autostart programs, but when I have them set to run on boot, they start in an annoying order, and I have to close them and open them again to get it right.

I have written a small script which I can run, but it only launches one, and onlt hen I close that program, does the next run.

```

guake && emesene && checkgmail

```

Any way to either delay start up of programs, or to write a script that will start them all?

---

### Post by amingv on 2008-04-28
That won't do; it will only run the next program when the one before exits successfully.
You could use sleep and try something like this:

```
#!/bin/bash

guake &
sleep 5
emesene &
sleep 5
checkgmail
```

You can change 5 for any value that matches your needs.

---

### Post by cometa2k7 on 2008-04-28
Thanks, that's perfect.

I knew that there would be something that you could do, I just didn't know what.

---

