---
title: "Using Rsync to copy files to new server"
date: 2014-04-01
forum: General Help
---

### Post by Alan_Killian on 2014-04-01
[SIZE=3]Hello,
I am setting up a new server and want to migrate my users /home directories to the new server preserving the permissions and group settings. I saw this command online [/SIZE][SIZE=4][COLOR=#000000][FONT=Calibri][COLOR=windowtext][COLOR=windowtext]but I am getting this error when I try to copy the directory to the new server:[/COLOR][/COLOR]
[/FONT][/COLOR][/SIZE][SIZE=3]
alank@Ubuntu-Server:/home/**$ sudo rsync -avuz /home/** alank@172.16.178.7:/homealank@172.16.178.7's password:
sending incremental file list
**/
rsync: recv_generator: mkdir "/home/**" failed: Permission denied (13)
*** Skipping any contents from this failed directory ***


sent 522 bytes  received 22 bytes  64.00 bytes/sec
total size is 20429  speedup is 37.55
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.9][/SIZE]
[SIZE=3]alank@Ubuntu-Server:/home/**$

Thanx[/SIZE]

---

### Post by slickymaster on 2014-04-01
> **Alan_Killian said:**
> [SIZE=2]Hello,
I am setting up a new server and want to migrate my users /home directories to the new server preserving the permissions and group settings. I saw this command online [COLOR=#000000][FONT=Calibri][COLOR=windowtext][COLOR=windowtext]but I am getting this error when I try to copy the directory to the new server:[/COLOR][/COLOR]
[/FONT][/COLOR]
alank@Ubuntu-Server:/home/**$ sudo rsync -avuz /home/** alank@172.16.178.7:/homealank@172.16.178.7's password:
sending incremental file list
**/
_[COLOR=#ff0000]rsync: recv_generator: mkdir "/home/**" failed: Permission denied (13)[/COLOR]_
*** Skipping any contents from this failed directory ***


sent 522 bytes  received 22 bytes  64.00 bytes/sec
total size is 20429  speedup is 37.55
rsync error: some files/attrs were not transferred (see previous errors) (code 23) at main.c(1070) [sender=3.0.9]
alank@Ubuntu-Server:/home/**$

Thanx[/SIZE]

It seems that you don't own the destination folder, root does.

You'll have to use the _chown_ command on the destination folder to make yourself the owner of it, instead of root.

---

### Post by Alan_Killian on 2014-04-01
If I run the command as root@172.16.178.7:/home and then enter my sudo password will that work and create and copy the users directories and files to new server. It seems silly to have to change /home ownership. I'm sure I'm not the first person to want to move a whole /home directory without having to recreate it first.

---

### Post by SeijiSensei on 2014-04-01
Usually this shouldn't require anything more than:
```
sudo rsync -av /home/ server:/home/
```
The trailing slashes are important to insure that all files below /home are correctly transferred.  However the problem is authenticating on the remote machine.

On an Ubuntu box, the root user doesn't have a password.  You can circumvent this issue by creating an SSH key for root on the source machine and copying it to the remote's /root/.ssh/authorized_keys file.  Personally, I give root a password to simplify matters, but that's not the official Ubuntu way.

Remember that you'll need to copy over /etc/passwd, /etc/group, and /etc/shadow to the new box to preserve the users and groups.

---

### Post by Alan_Killian on 2014-04-01
Yes I've already copied over the users to the new server. But is there no easier way to do this. Maybe rsync isnt the command I want? Surely people have wanted to copy over whole /home directories before without having to go thru this and preserve the user settings?

---

### Post by Alan_Killian on 2014-04-01
Here's what worked for me:
[COLOR=#000000][FONT=Calibri][COLOR=windowtext][COLOR=windowtext]To copy over /home directory must do this as user root because that's who owns /home directory. Issue commands[/COLOR] [/COLOR]
[/FONT][/COLOR][COLOR=#000000][FONT=Calibri][COLOR=windowtext][COLOR=windowtext]on [/COLOR][COLOR=windowtext]*remote server*[/COLOR][COLOR=windowtext]:[/COLOR] [/COLOR]
[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri][COLOR=windowtext][COLOR=#222222][FONT=Courier New]example@ubuntu:~$[/FONT][/COLOR][COLOR=#CC0000][FONT=Courier New]**sudo passwd **[/FONT][/COLOR][COLOR=#CC0000][FONT=Courier New]*root*[/FONT][/COLOR][FONT=Courier New] 
[/FONT][COLOR=#222222][FONT=Courier New][sudo] password for example:[/FONT][/COLOR][FONT=Courier New] 
[/FONT][COLOR=#222222][FONT=Courier New]Enter new UNIX password:[/FONT][/COLOR][FONT=Courier New] 
[/FONT][COLOR=#222222][FONT=Courier New]Retype new UNIX password:[/FONT][/COLOR][FONT=Courier New] 
[/FONT][COLOR=#222222][FONT=Courier New]passwd: password updated successfully[/FONT][/COLOR][FONT=Courier New] 
[/FONT][COLOR=#222222][FONT=Courier New]example@ubuntu:~$[/FONT][/COLOR][/COLOR]
[/FONT][/COLOR]

[COLOR=#000000][FONT=Calibri]**[COLOR=#111111]Now can issue command using syntax on local server to copy /home directory to remote server:[/COLOR]**

[/FONT][/COLOR]
[COLOR=#000000][FONT=Calibri][COLOR=windowtext][COLOR=#111111][FONT=Consolas]example_local@ubuntu:~$[/FONT][/COLOR][COLOR=windowtext][FONT=Consolas]**sudo rsync -avuz**[/FONT][/COLOR][COLOR=windowtext][FONT=Consolas]*/home/ root@172.15.18.85:/home/*[/FONT][/COLOR][/COLOR]
[/FONT][/COLOR]
[FONT=Calibri][COLOR=#000000]it's not the official Ubuntu way but is the most [/COLOR][/FONT][FONT=Calibri][COLOR=#0d0e00]expedient[/COLOR][/FONT][FONT=Calibri][COLOR=#000000] one[/COLOR][/FONT]

---

### Post by Lars Noodén on 2014-04-01
> **Alan_Killian said:**
> Yes I've already copied over the users to the new server. But is there no easier way to do this. Maybe rsync isnt the command I want? Surely people have wanted to copy over whole /home directories before without having to go thru this and preserve the user settings?

If you need sudo, you can use rsync with sudo by means of **--rsync-path**.

```

rsync -e "ssh -t" --rsync-path='sudo rsync' -av /home/ bkupacct@www.example.org:/home/

```

Note that for sudo to work that way, you have to have just that set of options enabled to run without a password.  You'll need to modify /etc/sudoers something like this on the target machine:

```

%alank ALL=(ALL:ALL) NOPASSWD: /usr/bin/rsync --server -vlogDtpre.iLs . /home/

```

The exact string can be gotten by running ssh with the **-v** option first.  When you are done, you may wish to rem out or erase that line from /etc/sudoers.

---

