---
title: "Adding new users command..."
date: 2015-10-01
forum: General Help
---

### Post by james_l2 on 2015-10-01
I know how to add a group, and then I know how to add 1 user and add to the group, is there a way to add a list of users on the one command?

Instead of having to type **[COLOR=#000000]useradd [/COLOR]**[COLOR=#000000]multiple**[COLOR=#000000] [/COLOR]**times? and **-g**[/COLOR]

---

### Post by TheFu on 2015-10-02
Why not script it with bash and a loop?
No need to type things so much.

That's how admins have been doing this stuff for 40 yrs, a 3 line  bash script.

---

### Post by The Cog on 2015-10-02
Here's a useful link:
[http://stackoverflow.com/questions/10929453/bash-scripting-read-file-line-by-line](http://stackoverflow.com/questions/10929453/bash-scripting-read-file-line-by-line)

---

### Post by efflandt on 2015-10-02
Unless these are non-login users for applications or something, the way to add login users with a proper home directory is **adduser** instead of **useradd** (read man pages for both).

---

### Post by TheFu on 2015-10-02
I always get those mixed up and have the check the manpages to get the one I want too - after 20+ yrs of being an admin.

---

### Post by sisco311 on 2015-10-02
You can use gpasswd to add multiple users to the same group:
```
gpasswd -M user1,user2,user3... group
```

---

### Post by james_l2 on 2015-10-08
Ok, the most sufficient way would be to run a batch file...
How would it be best to add users

[I][SIZE=2]** #!/bin/sh **
**groupadd NEWGROUP**
**usermod -G NEWGROUP $USER **
**done**

[/SIZE][/I][SIZE=2]or [/SIZE][I][SIZE=2]

[FONT=arial]** #!/bin/sh **
[B]groupadd NEWGROUP
gpasswd -M user1, user 2, NEWGROUP
done[/B][/FONT][/SIZE][/I]


I'm trying to find the best command to run the script, create a new group and add in new users in simplest way... the users have yet to be created..

I there a way to create list of users and add them to a new group in one line?

---

### Post by TheFu on 2015-10-08
#3 above answers that.

---

