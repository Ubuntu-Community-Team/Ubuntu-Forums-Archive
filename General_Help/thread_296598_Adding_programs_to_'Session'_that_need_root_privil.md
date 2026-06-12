---
title: "Adding programs to 'Session' that need root privilege"
date: 2006-11-09
forum: General Help
---

### Post by pauljwells on 2006-11-09
I know this is possible, because I had it working on an old installation of Hoary, but have long since forgotten what I did...

How can I add a program to the 'System/Preferences/Session/Startup Programs' tab that runs with root permissions?

The command I want to run is hid2hci -1 to make my bluetooth mouse work.

---

### Post by karlbowden on 2006-11-09
have you tried 'sudo hid2hci'

---

### Post by dannyboy79 on 2006-11-09
i am a newbie so i may be wrong but wouldn't you just add su beofre the command?

su hid2hci -1

or maybe sudo before it?

or I don't know if this would be bad but could you change the owner of your command so that a normal user could run it? i think that command is setuid. or maybe make it executable by you as the user? let me know if I am close to helping ya?

---

### Post by tomchuk on 2006-11-09
Run `sudo visudo` and add the following:

```

ALL     ALL=NOPASSWD: hid2hci

```

you can now add `sudo hid2hci -1` to your session startup and not have to worry about entering a password.

---

### Post by pauljwells on 2006-11-10
@tomchuk

that's the one! thank you, although the syntax I had to use was

```
%admin ALL=(ALL) ALL, NOPASSWD: /usr/sbin/hid2hci
```

since I am the only user on the machine, and hence a member of the admin group anyway

then in the sessions list, I added the startup program

```
sudo hid2hci -1
```

Now it all works perfectly!

---

