---
title: "Hardy Transfred Files Locked"
date: 2008-04-27
forum: General Help
---

### Post by rustyz on 2008-04-27
did a clean install of HH...

transfered backup files off a disk...

draged to desktop...

and they are "Locked" files now...

never had a problem on 7.6 or 7.10

any thoughts, sugestions, or help?

tried opening in root, it can be done, just they stay locked when moved...

thanks

---

### Post by themattjon on 2008-05-04
Same here, double help?

---

### Post by virtuallinux on 2008-05-04
Ok, so if I understand correctly, the files you put on your desktop have the little lock on the Icon.  The fastest way to fix this would be to:
1) open a terminal
2) navigate to your home directory: type "cd"
3) use the chown command to change the ownership of all the files on your desktop:
type ```
chown -R yourusername Desktop
```

for more on the chown command, go [here.]("http://en.wikipedia.org/wiki/Chown")

Alternatively, you could use the chmod command to change the permissions of all the files on your desktop:
type ```
chmod -R 777 Desktop/
```

note that this will change all of the files on your desktop so that anyone can read, write, or execute them.  

if you want different permissions for certain files, then after you've opened the terminal, navigate to your desktop (type "cd Desktop" from your home directory), and you can use the chmod command on each file or directory individually. If you're using it on a file, leave out the -R option. If you want to set different permissions for the file, you change the number part.  For more information on chmod, go [here.]("http://en.wikipedia.org/wiki/Chmod")

---

