---
title: "How to allow user to run script and only that"
date: 2014-11-27
forum: General Help
---

### Post by xathras1982 on 2014-11-27
Hello All, I am trying to create a Linux terminal menu by way of a simple script. Within the script it will have some commands that will submit a job (a shell script for example) as another user without password prompt.  
For the sake of this. Here is what I have:

[LIST=1]
[*]Username temp1, which is the user that will be running the menu.  uid=1001(temp1), gid=1001(temp1), groups=1001(temp1)

[*]Username wayne, which is the user that the script must be submitted as to run the job uid=1000(wayne), gid=1000(wayne),groups=1000(wayne),4(adm),24(cdrom),27(sudo),30(dip)...

[*]Script script1.sh, script2.sh owned by wayne. 
-rwxr-xr-x script1.sh
-rwxr-xr-x script2.sh
[*]If I try to go to /home/wayne as temp1 user I get permission denied (expected)

[*]I set the scripts to chmod 700 for wayne. So technically no one can run them other than wayne.

[*]I have edited sudo file and have the following entry:
temp1 ALL(wayne) NOPASSWD: /home/wayne/script1.sh
[*]When I run command su -c "/home/wayne/script1.sh" -s /bin/sh wayne the script runs (as expected)

[*]When I run command su -c "/home/wayne/script2.sh" -s /bin/sh wayne the script runs (not expected).
[/LIST]
Any ideas?

---

### Post by dragonfly41 on 2014-11-27
This might be regarded as overkill .. but you could deploy webmin (it is in Ubuntu Software Centre) and define custom commands for your user(s).

---

### Post by nerdtron on 2014-11-27
What is the difference on the contents of the scripts1 and scripts2?

---

### Post by xathras1982 on 2014-11-28
Nerdtron, for this example I have script 1 and 2 output to a filename file1.txt (script1.sh) and file2.txt (script2.sh).
The purpose is to prevent the user from being able to run other scripts for the same user

---

### Post by xathras1982 on 2014-11-28
Yes I could. However, surely there is a much better way to control?

---

### Post by Lars Noodén on 2014-11-30
You could look into [rbash](http://manpages.ubuntu.com/manpages/trusty/en/man1/rbash.1.html) and maybe setting that as their shell along with read-only home directory files (.bashrc, .profile).  Then by setting the script you want them to run in an unwriteable directory that is the only content of $PATH you can prevent them from running other programs.

---

### Post by xathras1982 on 2014-11-30
Thanks Lars - I will take a look. What I don't understand how is it even remotely possible to execute this script? I guess out of all this, this is the point I don't understand

---

### Post by xathras1982 on 2014-11-30
Ok, I worked it out and recognize how much of a plonker I am.

I was executing su -c "home/wayne/script2.sh" -s /bin/sh wayne which was essentially authenticating me as wayne and running.
If I change to sudo -u wayne '/home/wayne/sript2.sh' it doesn't work and I get the appropriate error message!

---

