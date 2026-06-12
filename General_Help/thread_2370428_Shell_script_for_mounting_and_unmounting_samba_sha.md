---
title: "Shell script for mounting and unmounting samba share"
date: 2017-09-03
forum: General Help
---

### Post by asmox79 on 2017-09-03
Hello!

I have a USB drive connected to RaspberryPi and I share the whole disk with Samba. Since the data is quite important for me, I want to avoid auto-mounting, just in case. In another words, every time the share is about to be mounted, I want to be asked for password.
On the other hand, typing every time command for mounting is quite tiring. So I want to have kind of script I can click or put it's name in terminal (instead of writing full mounting command). I inspire with this post:
[https://bbs.archlinux.org/viewtopic.php?id=105333](https://bbs.archlinux.org/viewtopic.php?id=105333)
But for some reasons this solution doesn't work for me. Let's start from my actual version of script:

```
#!/bin/sh
echo "This is a custom script for mount my grubas share"
echo " "
read -p "Password: " mypassword


if grep "grubas" /etc/mtab &>/dev/null; then
    echo "if1"
    grep "grubas" /etc/mtab | awk '{print "Grubas is already mounted on " $2}'
else
        echo "if2"
        sudo mount -t cifs //192.168.1.50/grubas /mnt/grubas -o username=pi,password="$mypassword" && echo "Grubas is now mounted" || echo "unable to mount Grubas"
        
fi
exit

```

Grubas is Polish name for my share :)
Actually there are 2 problems:
[LIST=1]
[*]I cannot hide the password entry. When I try adding -s parameter to *read *command I get the error:
```
$ ./mountgrubas.sh
This is a custom script for mount my grubas share
 
./mountgrubas.sh: 4: read: Illegal option -s
```
According to the similar problem solved here: [https://stackoverflow.com/questions/36214969/read-illegal-option-s-in-shell-scripting](https://stackoverflow.com/questions/36214969/read-illegal-option-s-in-shell-scripting)
I wonder if I should use *bash* instead of *sh*? I am not similar with Linux script and it's my first time. What more, I cannot use *run* command in my terminal.
[*]The script doesn't even try to mount. For some reasons it behaves like the share was already mounted even though it isn't that's why I put *echo "if1"*, it made me see that script is going to first part of *if statement*.
```
$ ./mountgrubas.sh
This is a custom script for mount my grubas share
 
Password: lolololo
if1
```
[/LIST]
Can you please help me to make this script working?

---

### Post by TheFu on 2017-09-03
bash is available on most Unix-like systems.  It has some nice features which might be useful.

Try:
```
#!/bin/bash -x
```

That lets you see every statement evaluation.
There isn't any need for awk. Loading another process is wasteful.

Don't ever pass a password on any command line. NEVER.  Don't put a password into a script either.
So ... the mount command has a way to deal with credentials for us.  Just use normal Unix file permissions to control who can access those credentials stored in a file.

Mount options example:
```
,credentials=/etc/samba/win7lap-D.credentials
```
These can be used on a mount command, in a script, or like I do, in an automount config file.

But ... if you are sharing files between Unix systems, then I'd strongly suggest using NFS and normal file/directory permissions can be used to control access.  If you really want to limit access, use NFSv4 with kerberos auth.


I would simply ask grep for a count of the found lines.
```
FOUND_CNT=`mount|grep -c grubas`
```
Then check if the count is 0 or not.  Using the mount command is better than checking the mtab, btw.  Always prefer APIs over checking a specific file.

Your 'ifs' seem wrong.  

```
if [ "0" -eq "$FOUND_CNT" ] then ; do  # integer comparison; also note the single brackets used.

else

fi

```
[http://tldp.org/LDP/abs/html/comparison-ops.html](http://tldp.org/LDP/abs/html/comparison-ops.html) is useful.
But really, **prefer NFS over cifs when both sides are Unix variants**.

---

### Post by untrustytahr on 2017-09-03
> **asmox79 said:**
> 
On the other hand, typing every time command for mounting is quite tiring. So I want to have kind of script I can click or put it's name in terminal (instead of writing full mounting command). 

This looks like a good use for aliases

In your .bash_aliases file (create it with a text editor in your home directory if it doesn't yet exist-and note it's a hidden file starting with a period) type these two lines:


alias mount-grubas='gvfs-mount smb://192.168.1.50/grubas/'
alias umount-grubas='gvfs-mount -u smb://192.168.1.50/grubas/'


save it. then you need to source it (for terminals that are already open, you will not need to do this after future reboots).


source .bash_aliases


Now you can just type 'mount-grubas' & 'umount-grubas' to connect to the samba share.  It will prompt you for the password.  Creating a script is over-engineering the solution IMHO.

---

