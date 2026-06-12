---
title: "Command workin in terminal not working in basic How to debug this problem advise plse"
date: 2019-06-27
forum: General Help
---

### Post by Neill_R on 2019-06-27
Hello

I wonder if you can spot my mistake in using the SHELL() function to run a bash script with elevated privileges
Thank you

```

               [B]astring="bash -c ` echo """ & gotpassword & """ | sudo -S /home/neill/Documents/get_package_list_in_file.sh " & Filename & "`" 
               x = Shell (astring)[/B]

```

[B]astring becomes 

bash -c `echo "mypassword" | sudo -S /home/neill/Documents/get_package_list_in_file.sh /home/neill/Documents/pkg.txt`
[/B]
In a fresh terminal the code below produces the desired output file The code in the basic shell call does not

```


neill@HDD-Mint-64:~$ **echo "mypassword" | sudo -S /home/neill/Documents/get_package_list_in_file.sh /home/neill/Documents/pkg.txt**
[sudo] password for neill: neill@HDD-Mint-64:~$ 

neill@HDD-Mint-64:~$ **echo "mypassword" | sudo -S /home/neill/Documents/get_package_list_in_file.sh /home/neill/Documents/pkg.txt**
neill@HDD-Mint-64:~$ 

#Second call does not need password hence need to wait or to start again in a fresh terminal 

and


neill@HDD-Mint-64:~$ ls -lat **/home/neill/Documents/get_package_list_in_file.sh**
[SIZE=4][FONT=arial]**-rwxrwxr-x 1 neill neill 68 Jun 27 09:15 /home/neill/Documents/get_package_list_in_file.sh**[/FONT][/SIZE]
neill@HDD-Mint-64:~$ 
neill@HDD-Mint-64:~$ 
neill@HDD-Mint-64:~$ cat** /home/neill/Documents/get_package_list_in_file.sh**
[B]#!/bin/bash
## dpkg -l > /home/neill/Documents/pkg.txt
dpkg -l > $1[/B]


```

---

### Post by TheFu on 2019-06-27
I would just allow the userid to run the specific command via sudo without being prompted for credentials. This is a common thing controlled via the sudoers file.

---

