---
title: "[SOLVED] How to delete a non empty folder?"
date: 2008-06-14
forum: General Help
---

### Post by agentsmith23 on 2008-06-14
I am trying to delete a few folders that need sudo access and these folders have files and folders in them. Is there a command that will allow me to delete the folders rather than doing it file by file.

Thanks!

---

### Post by powerpleb on 2008-06-14
> **agentsmith23 said:**
> I am trying to delete a few folders that need sudo access and these folders have files and folders in them. Is there a command that will allow me to delete the folders rather than doing it file by file.

Thanks!

Yes.```
sudo rm -r /folder
```
Be very careful with this command for obvious reasons

---

### Post by Rocket2DMn on 2008-06-14
Let me elaborate on thos *obvious reasons* because they aren't obvious to many.  The rm command CANNOT be undone, there is no trash bin for deleting fromt he terminal.  Once you delete with rm, it's gone.  Be VERY careful with that command, and avoid using sudo with it if possible.

---

### Post by powerpleb on 2008-06-14
Perhaps a safer. more visual way to do it would be to hit ALT + F2,
type ```
gksudo nautilus
```
This gives you the graphical file manager with sudo privileges.

---

### Post by agentsmith23 on 2008-06-14
I have already tried rmdir -r and it doesn't work. I get an error back that says:

```
rmdir: invalid option -- r
Try `rmdir --help' for more information.
```

Help doesn't really give me any help. I just gives me this:

```
Usage: rmdir [OPTION]... DIRECTORY...
Remove the DIRECTORY(ies), if they are empty.

      --ignore-fail-on-non-empty
                  ignore each failure that is solely because a directory
                  is non-empty
  -p, --parents   Remove DIRECTORY and its ancestors.  E.g., `rmdir -p a/b/c' is
                  similar to `rmdir a/b/c a/b a'.
  -v, --verbose   output a diagnostic for every directory processed
      --help     display this help and exit
      --version  output version information and exit

Report bugs to <bug-coreutils@gnu.org>.

```

---

### Post by Rocket2DMn on 2008-06-14
The command is not "rmdir", its "rm".  rmdir is for empty folders, rm is for files.  Using the recursive option, -r, deletes all files within the folder, then the folder itself.

---

### Post by agentsmith23 on 2008-06-14
> **powerpleb said:**
> Perhaps a safer. more visual way to do it would be to hit ALT + F2,
type ```
gksudo nautilus
```
This gives you the graphical file manager with sudo privileges.



Thanks that worked perfectly!

---

