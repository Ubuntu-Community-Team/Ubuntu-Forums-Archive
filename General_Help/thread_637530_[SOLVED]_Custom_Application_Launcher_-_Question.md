---
title: "[SOLVED] Custom Application Launcher - Question"
date: 2007-12-11
forum: General Help
---

### Post by sultanoswing on 2007-12-11
When trying to run an application using a custom application launcher on the Gnome panel, the program starts, but is missing its icons.

I remember reading somewhere that this is because the program hasn't been started from its own directory, so doesn't have a relative start path, but I can't remember the fix!

The current working command to launch the app (Mupen64) is: "/home/username/Mupen64amd64/mupen64".

What command do I need to add to make the launch relative? I've tried "./home/username....etc" and "~/home/username...etc", but the error "failed to execute child process..." occurs.

Thanks.

---

### Post by yabbadabbadont on 2007-12-11
```
(cd /home/username/Mupen64amd64 && ./mupen64)
```
Should work.

---

### Post by sultanoswing on 2007-12-11
Thanks for the reply - the above however resulted in:

"Failed to execute child process "cd" (No such file or directory)"

...does this need to be an "Application in terminal"-type launcher?

I suppose the other way to do this will be to add the command 'mupen64" to the PATH or somesuch?

EDIT: and yes, the path is correct :)

---

### Post by yabbadabbadont on 2007-12-11
Let's try a slightly different approach.  Create a simple shell script that changes into the program directory and then runs the program.  Have the launcher start the script.

```
#!/bin/bash
cd /home/username/Mupen64amd64
exec mupen64

```

Save that somewhere like /home/username/bin/mupen64_launcher and then make it executable.
```
chmod 755 /home/username/bin/mupen64_launcher
```

---

### Post by sultanoswing on 2007-12-11
The silly thing! Still won't run, despite the above excellent advice (which should work, AFAIK!).

Grrrrr! The mupen64 file executes perfectly fine with a double-click and also via the direct panel app launcher I created, but the bash script (yes, it's chmoded) doesn't seem run the damn thing (again, I've checked the paths). Hmmmm?!??

---

### Post by yabbadabbadont on 2007-12-11
Run the script from a terminal window to see if any error messages are being spit out.

---

### Post by sultanoswing on 2007-12-12
Weird. When running the script from the terminal:

```
curtis@taniwha:~$ sh mupen64_launcher
exec: 3: mupen64: not found
```

...but upon changing to the directory and executing using "./mupen64" it runs!

EDIT: cancel that - it now works, but the script needed a slight modification:

```
#!/bin/bash
cd /home/user/Mupen64
exec ./mupen64
```

Thanks for your help - I really must remember to use the terminal to check for errors!

---

