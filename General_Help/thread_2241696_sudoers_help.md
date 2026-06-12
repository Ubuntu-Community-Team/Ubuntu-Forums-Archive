---
title: "sudoers help"
date: 2014-08-27
forum: General Help
---

### Post by chase7 on 2014-08-27
Alright I am still very new to Linux so please forgive me.

I own a hosted dedicated server and run some games on it. One of these games is "7 Days to Die" and in order for the admins on this server to start and stop the server i need to give them the permission to run specific commands because i dont want them to have root access.

To do this i have been reading i should add them to the sudoers file however the more i read about it the more and more lost I am.

I know their is a way to create a group alias and allow them access to run specific scripts and this is what i want to do

Alias = SDTD = username, username

No as far as scripts this is what i want them to be able to do.
7dtd.sh instances edit <instancename> 
7dtd.sh instances list
7dtd.sh start <instancename>
7dtd.sh kill <instancename>
7dtd.sh status <instancename>

7dtd.sh is in /usr/local/bin/7dtd.sh

Their are a few other scripts but i dont really want them to have access to them such as creating and deleting instances

Any insight on this would help being ide rather not mess with the sudoers file until i know what i am doing id correct.

---

### Post by chase7 on 2014-08-27
I have it working but they can run all of the 7dtd.sh commands is their a way to deny access to some?

---

### Post by sotiris2 on 2014-08-28
If I understand correctly there is actually one script (7dtd.sh) and it accepts arguments? 

[Apparently]("http://www.atrixnet.com/allow-an-unprivileged-user-to-run-a-certain-command-with-sudo/") writing the command with it's arguments in the sudoers file, will only allow the command to be run with these SPECIFIC arguments.

You 'll need multiple entries I think. Also it will probably need some wild-card for the <instancename> (or if you want to limit the user to specific instances you could the exact instance as an argument on the sudoers file) because if you write ```
joe ALL=(ALL) NOPASSWD: /full/path/to/7dtd.sh start
``` 
The Admin trying ```
sudo 
``````
/full/path/to/7dtd.sh start <instance>
``` will probably have his command rejected by sudo. So you 'll have to put ```
joe ALL=(ALL) NOPASSWD: /full/path/to/7dtd.sh start *
``` This will allow them to run ```
sudo /full/path/to/7dtd.sh start <anything>
``` so they can pass <instance> to the script. You can limit a bit what kind of arguments they can pass using [wildcards]("http://www.sudo.ws/sudoers.man.html#x57696c646361726473")

I have not actually tested this though, so backup and try it with care.

---

### Post by Lars Noodén on 2014-08-28
> **chase7 said:**
> I have it working but they can run all of the 7dtd.sh commands is their a way to deny access to some?

I'm pretty sure you have to make two command aliases, one for each group.  One group gets all the options, the other group gets the restricted subset.

---

### Post by chase7 on 2014-08-28
Thanks guys ill go revise my file and see how that works.

---

