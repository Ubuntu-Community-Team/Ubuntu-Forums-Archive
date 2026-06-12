---
title: "Switching to root user with bash script?"
date: 2017-05-20
forum: General Help
---

### Post by peter1897 on 2017-05-20
How to switch to root user using a bash script? I guess one line of the script will be 'su root' but i don't know how to implement the password input part.

---

### Post by TheFu on 2017-05-20
You should use **sudo**, not su.

If this is for a 1-time command in the script and you believe it is safe for anyone, you can make that specific command with the exact specific options available to all users, so no password is needed.  That is controlled by the sudoers file.

You cannot change the current userid in a running script. The solution is to have multiple scripts.  One that runs as the userid and calls out to another that runs for elevated privilege needs -- called by sudo -- then returns to the _main_ script at the completion.

---

### Post by &amp;KyT$0P# on 2017-05-20
Would it work to make the script re-execute itself as root if needed?  Putting this at the beginning seems to do the job -
```
if [ $(id -u) -ne 0 ];then
  echo "You don't seem to be root.  Re-executing script as root"
  sudo -H "$0" "$@"
  exit
fi

```

---

### Post by peter1897 on 2017-05-20
What about switching users only with one line command? Something like login to mysql console. Is that possible?

---

### Post by &amp;KyT$0P# on 2017-05-20
That is what TheFu explained how to do.

What problems are you hitting with the password input?

---

### Post by TheFu on 2017-05-20
Use **read** to get inputs in bash, but often passwords **must** come from a secured TTY and will not be allowed as input.  Most tools that work in that way would also have a credentials file capability.  Samba does. openvpn does.  I don't use mysql, but postgress and mariaDB do.  Passing a password on a command line is a poor security technique. That is way most tools which deal with different users support the credentials file.
[https://dev.mysql.com/doc/refman/5.7/en/password-security-user.html](https://dev.mysql.com/doc/refman/5.7/en/password-security-user.html) explains how mysql deals with passwords. I wouldn't use the command line or environment variable options. The solution I've seen is placing the credentials into a file and locking down the permissions to that file.> 
 Store your password in an option file. For example, on Unix, you can list your password in the [client] section of the .my.cnf file in your home directory:

[client]
password=your_pass

To keep the password safe, the file should not be accessible to anyone but yourself. To ensure this, set the file access mode to 400 or 600.

---

### Post by peter1897 on 2017-05-20
> **halogen2 said:**
> That is what TheFu explained how to do.

What problems are you hitting with the password input?

I don't know how to use the 'read' command. Should be something like: su root && read 'pass' ?

---

### Post by TheFu on 2017-05-20
Don't use su.  Use **sudo**.  That should remove the need to enter a password, if you setup the sudoers, as I attempted to explain before.

We really aren't supposed to post google answers here. It is assumed that the OP can use google., but if you insist on doing it the non-secure, way ... 
[https://stackoverflow.com/questions/13202074/how-to-secure-read-with-the-bash-read-command](https://stackoverflow.com/questions/13202074/how-to-secure-read-with-the-bash-read-command)

There are times, probably, when doing it that way is best. I just can't think of any now or in the last 20 yrs I've been a Unix admin.

---

### Post by peter1897 on 2017-05-20
> **TheFu said:**
> Don't use su.  Use **sudo**.  That should remove the need to enter a password, if you setup the sudoers, as I attempted to explain before.

We really aren't supposed to post google answers here. It is assumed that the OP can use google., but if you insist on doing it the non-secure, way ... 
[https://stackoverflow.com/questions/13202074/how-to-secure-read-with-the-bash-read-command](https://stackoverflow.com/questions/13202074/how-to-secure-read-with-the-bash-read-command)

There are times, probably, when doing it that way is best. I just can't think of any now or in the last 20 yrs I've been a Unix admin.

Not sure what you mean by not use su, but sudo. Isn't su for 'switch user'? If i type 'sudo root' instead of 'su root' i get 'sudo: root: command not found'.
Also, if i understand correctly even if i use 'read' i still have to type a password, which is not what i need.

---

### Post by lisati on 2017-05-20
The "preferred" method of temporarily elevating permissions here is by prefixing the commands with "sudo."

Have a read [here]("https://help.ubuntu.com/community/RootSudo") for basic information.

---

### Post by peter1897 on 2017-05-20
This is the script i managed to came up to but it is not working:

```
#!/bin/bash

su root
read -r var < pass.txt
echo $var
```

The pass.txt file contain the password for the root user, but when i execute the script it still ask my to enter the password.

---

### Post by lisati on 2017-05-20
Did you read the information at the link I provided? [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by TheFu on 2017-05-20
Seems we are talking passed the OP.  I suspect this is more about getting someone to enter the root password (which Ubuntu doesn't use) than solving an issue to run a command with elevated permissions.  Which is exactly what sudo does.

Seems all my effort to lead towards a viable, better, more secure, solution has failed. It is my failure. Someone else will have to try now.

---

### Post by raleigh3 on 2017-05-20
This is how you can run any root command.

echo "your password" | sudo -S thunar

---

### Post by efflandt on 2017-05-21
One way to run something as root (or another user) if you do not have terminal access to enter a password is suid permission. However, for security reasons suid is ignored for scripts, so you would need an suid c wrapper (binary program with suid permission) to run the script as root (or another user). That is what I needed to do for CGI scripts on a webserver that runs as a non-privileged user (that I did not control) to write data to a file that only I would have write permission for. I used to do those CGI scripts in Perl and there was a Perl script to create and compile the c wrapper to run each CGI script as me once I set suid permission on the c wrapper. In my case "others" needed execute permission for the c wrapper, but no group permissions. But in your case if you wanted certain user(s) to execute it, you could create a group with execute permission for the group and only members of the group could run it.

---

### Post by peter1897 on 2017-05-21
I am not sure i explained clear enough what i am trying to achieve. I want to create a script, for example switch_root.sh, and when i run the script (./switch_root.sh), to switch to root user without entering the password, the script have to take care of that. Beside that i am very noob in bash scripting, so i will appreciate if you can give me an example of how the script should look, so i can have some orientation.

---

