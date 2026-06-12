---
title: "How to create script for run sudo mount -a"
date: 2015-07-15
forum: General Help
---

### Post by suchart on 2015-07-15
Hello everybody 

I'm very very new for ubuntu. I have one raspberry with ubuntu-mate os. Now I got one problem with it.

I edit fstab on /etc/fstab  for mount share folder form windows server. Ok  work fine after I do sudo mount -a.

but after reboot it can't mount on Startup. I must to open terminal and run command  "sudo mount -a" every time after reboot.

How can I do the script for run "sudo mount -a" when ubuntu start.

Or I can do the script for run  "sudo mount -a" just dubble click look like .bat for windows OS

many Thank sir.


Sorry for my English

---

### Post by branau on 2015-07-16
Hey there,  to make the double-clickable file on your desktop, you'd want to write a shell script. Call it whatever-you-want.sh. Just make sure it has the .sh ending. In it, write this command: 

```
 #!/bin/bash sudo mount -a 
```  

Then, save that somewhere and create a file on your desktop called whatever-you-want.desktop. Again, make sure you got that .desktop ending. In that file, you'll want to write the following:  

```
 
[Desktop Entry] 
Name=Mount 
Comment=Run tool to automatically mount. 
Exec=/home/you/path/to/your-file.sh 
Terminal=true 
Type=Application

```  

After that, run this: 

```
 sudo chmod +x your-file.sh 
```  

That should do the trick, but you should always right click the .desktop file and open the properties, and then make sure that on the Permissions tab you have the box that says "Allow executing file as a program" checked. After that, double-click your file, and you should get a terminal window that pops up and asks you for your password, and then the command will execute.  I'll have to do a little research to help you figure out how to make this command run on startup. I'm not sure if you could get it to work though, as it does require you to run a sudo command, which in turn, requires you to input your password.

---

### Post by suchart on 2015-07-16
Thank you so much sir.
I already do it.but when I dubble click on my.desktop file.I got an error 

"Therr was an error launching the application.
Detail:Failed to execute child
process "xterm" (No such file or directory)

when I edit 

terminal=true >  terminal=mate ( I use mate-terminal )

I don't got any error but nothing happen. 

It's don't mount my windows share drive.

Thank you.

---

### Post by bytr on 2015-07-16
You can add a command to */etc/rc.local*. It will be automatically run at system startup.

---

### Post by tgalati4 on 2015-07-16
Put a delay in your script.  It's possible that the Windows file server is slow to mount.  Perhaps post your /etc/fstab to see if there is an error.

In your /etc/rc.local:

```


#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.


sleep 30
mount -a

exit 0


```

Welcome to the forums.

---

