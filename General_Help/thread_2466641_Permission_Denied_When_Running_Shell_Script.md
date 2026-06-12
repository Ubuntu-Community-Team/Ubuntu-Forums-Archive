---
title: "Permission Denied When Running Shell Script"
date: 2021-09-01
forum: General Help
---

### Post by wilsonht on 2021-09-01
[COLOR=#232629][FONT=-apple-system][FONT=inherit][FONT=inherit][FONT=inherit]I'm using Ubuntu Server 20.04 LTS. When I run a shell script, I get the following error: ```
-bash: ./install.sh: Permission denied
```. I've looked at a similar post on this forum and none of those answers solved the problem. My terminal input and output are below. If anyone can help, that'd be very appreciated.

Terminal: [https://pastebin.com/ZbkKNYLd](https://pastebin.com/ZbkKNYLd)[/FONT][/FONT][/FONT][/FONT][/COLOR]

---

### Post by tea for one on 2021-09-01
[COLOR="#0000FF"]Permission denied[/COLOR] usually means that you need sudo (elevated) privileges.

Are you trying to install a software package?

---

### Post by TheFu on 2021-09-01
```
wilsont@bzoit:/media/wilsont/disk$ chmod [s]u+r+x [/s]install.sh
```
That isn't a valid command.
You want either
```
chmod 700 install.sh
```
or 
```
chmod u+rx install.sh
```

```
wilsont@bzoit:/media/wilsont/disk$ ./install.sh
-bash: ./install.sh: Permission denied
```
Cannot execute scripts that don't have the correct permissions.

Use```
 ls -l install.sh
```
to see the permissions.


BTW, sudo ain't gonna help with the permissions in this situation.
If you have trouble with Unix permissions, any Unix tutorial on permissions is 100% valid for Linux too.  Any beginning Unix book from 1990 will have a chapter on it for $0.50.  Or google "linux permissions tutorial", and spend 15 minutes working through that, then another 30 minutes in a play directory - perhaps /tmp/foo/ on your own system with 3 userids, 2 groups then setup files and subdirectories with every possible combination of owners, groups, and file permissions.  Go from 000. 001, 002, 003, 004, 005, ..... to 771, 772, 773, 774, 775, 776, 777 ... and check out how each change allows or prevents access for the owner, group members, others and people outside the group.  You'll see the pattern quickly and then you'll "have it" for the rest of your life.

Or spend hours, days, weeks, months, years being frustrated over little issues like the above.  Your choice.

---

