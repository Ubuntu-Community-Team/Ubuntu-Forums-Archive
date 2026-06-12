---
title: "Distinct user"
date: 2021-08-31
forum: General Help
---

### Post by oli020202 on 2021-08-31
How can I have distinct user on my computer ? I want all users to have their own apps and other users not to have access to them. Can we do that with the terminal ?
[COLOR=#202124][FONT=&quot]I want all users to have their own app and other users not to have access to it[/FONT][/COLOR][COLOR=#202124][FONT=&quot]I want all users to have their own app and other users not to have access to it[/FONT][/COLOR][COLOR=#202124][FONT=&quot]I want all users to have their own app and other users not to have access to it[/FONT][/COLOR][COLOR=#202124][FONT=&quot]I want all users to have their own app and other users not to have access to it[/FONT][/COLOR]

---

### Post by TheFu on 2021-08-31
If you want different applications per user, then control that via file and directory permissions.
Each user can manually install programs under their own userids.

There are methods to limit which major applications each userid can run, but setting that up is non-trivial.  Start by reading this: [https://linuxcommand.org/tlcl.php](https://linuxcommand.org/tlcl.php)

If you make a list of the exact name (including the directory) for each application you want each userid to run, that would be a start.

Of course, all their data will always be separate, so there isn't any concern about userA and userB deleting each other's data ---- unless they are in the same group and specifically setup the data files to allow that.

---

