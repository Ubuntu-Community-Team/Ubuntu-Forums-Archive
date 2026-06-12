---
title: "saving in multiple locations"
date: 2007-08-16
forum: General Help
---

### Post by limberlegs on 2007-08-16
Hi there!

I've been exclusively using Ubuntu 7.04 for about a month now, and I have to say I don't think that I'll be swtiching back to Windows this time!  Anyway, I had a question regarding saving files and backing up files, etc.  Is it possible to have a file saved to a specific folder automatically saved to an additional folder or folders?  For example, if I'm working on my dissertation, and I save the file locally to by /home folder, can I have that also automatically save to an external drive, or a network drive, or both?

Thanks for your help!

---

### Post by ddrichardson on 2007-08-16
A simple bash script will do:
```
#!/bin/sh
cp $1 path1/.
cp $1 path2/.
echo $1

```
Just save it as say backup and ```
chmod +x backup
``` Replace path1 and path2 with wherever you want it.

---

### Post by limberlegs on 2007-08-17
Thanks for your response.  I'm still a bit of a Linux rookie, so would you mind just talking me through exactly what those commands do?  Or perhaps you can direct me somewhere where I can learn a little more about the sytax?

Thanks!

---

### Post by ddrichardson on 2007-08-17
Chmod can change a file to make it executable. cp copies files. $1 is the first argument passed to the shell script. So in the example, ```
./backup filename
``` Will copy the filename to two locations.

---

