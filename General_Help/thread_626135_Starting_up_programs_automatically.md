---
title: "Starting up programs automatically"
date: 2007-11-28
forum: General Help
---

### Post by APMT19 on 2007-11-28
I have a batch file or at least thats what they call it on windows. How do I make it so that it launches that file automatically when I log on? Running 7.10 Desktop

---

### Post by BtJizzle on 2007-11-28
im not 100% sure but have you ever tried this?


System > Preferences > Sessions

And from there add an additional startup program......

in command, type in the location of the executable.

Hope it works?

---

### Post by scott_g on 2007-11-28
1. Go to System > Preferences > Sessions.

2. Click "Add".

3. Enter a name describing it.

4. For the command, type: "sh /path_to_file/file.sh", where path_to_file is the directory the file is in, and the file has a .sh file extension.

5. Click "OK".

That should do it... never actually tried it, but in theory it should work.

Note: If you want commands executed everytime the machine starts regardless of who logs in, add the commands to the /etc/rc.local file.

Hope it helps,
Scott

EDIT: Beat to it....

---

