---
title: "Create new User with limited access"
date: 2008-04-02
forum: General Help
---

### Post by oxhaksi on 2008-04-02
Hi everyone

I am creating an ubuntu vsftpd server so that people  can log in and put files in and take files out.

Admins[LIST=1]
[*]Right to access anything from other users
[/LIST]

Users
[LIST=1]
[*]Home directory = /home/newfolder/<user>
[*]Have right to read/write in/out of their folder
[/LIST]

My main goal is to have a script that would allow an administrator to select user or admin. The following script show our current setup in another linux box (fedora). This script works with fedora but not ubuntu. Any suggestion on how I can fix it!! :confused:


```

#!/bin/bash

 

echo "Please make a selection:"

 

OPTIONS="1"

select opt in $OPTIONS; do

if [ "$opt" = Admin ]; then

       echo "Please enter new admin name:"

       read admin_name  

       dirname=/home/riverlogic

       useradd -g ftpuser -G adm -d $dirname  -M -n $admin_name

       passwd $admin_name

       echo "New admin "$admin_name" created successfully!"

       exit

elif [ "$opt" = User ]; then

       echo "Please enter new user name:"

       read user_name  

       dirname=/home/riverlogic/$user_name

       mkdir $dirname

       chgrp ftpuser $dirname

       useradd -g ftpuser -d $dirname  -M -n $user_name

       passwd $user_name

       chown $user_name $dirname

       chmod 770 $dirname

       echo "$user_name" >> /etc/vsftpd/chroot_list

       echo "New user "$user_name" created successfully!"

       exit

else 

echo "Bad option, please select one of the following:"

echo "1) Admin"

echo "2) User"

 

fi

done

```


Thank you in advance

---

### Post by Rocket2DMn on 2008-04-02
Do you know where it is breaking down?
Have you created the group called "ftpuser"?

---

### Post by oxhaksi on 2008-04-02
Yes i have created the ftpuser group and when i run the script i get this error message.

sshserver@sshserver:~$ sh ./ftpscript

Please make a selection:

./ftpscript: 6: select: not found

Bad option, please select one of the following:

1) Admin

2) User

./ftpscript: 34: Syntax error: "done" unexpected

sshserver@sshserver:~$

---

### Post by Rocket2DMn on 2008-04-02
It is a bash script, not using "sh" - bash is the default shell in the Debian/Ubuntu terminal, anyway.  What happens if you just run
```
./ftpscript
```
If you still need "sh", normally when you preceed a script with a command, you don't need the ./ with it.  (I'm not on a linux machine to test that out for you, unfortunately).  So it would look like this:
```
sh ftpscript
```
Also, do you need to read in "$opt" before your if statement?

---

