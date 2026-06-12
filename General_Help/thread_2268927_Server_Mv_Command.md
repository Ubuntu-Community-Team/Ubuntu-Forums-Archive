---
title: "Server Mv Command"
date: 2015-03-12
forum: General Help
---

### Post by jnap2 on 2015-03-12
Hello

First post here.

Today when making some cleaning at my personal server, i typed something like this (get distracted :/)

```
jnap@MyServer:ActualFolderThatIWantedToMove$ sudo mv /* /folderName
```

So now I'm stuck with the ssh connection where i made the mistake, can't access with ftp, sftp, etc...

Can't execute any command, the error message is not found, LS, MV, SUDO, WHICH, CP, none... the folders where moved so it's expected...
The only command that works it's the CD. I can navigate to the /folderName/bin, /folderName/sbin, /folderName/user/bin or /folderName/user/sbin folders but the commands still doesnt work... the mv command changed the executable attribute? or what?

Someone can help me with a brilliant idea? Or the only solution it's rebooting the machine with a boot cd/pen and then try to restore everything to the right place?

I'm trying to solve the problem remotely, only tomorrow I'll be able to access phisically to the machine.

Thanks

---

### Post by spjackson on 2015-03-12
> **jnap2 said:**
> Hello

First post here.

Welcome to the forums. To undo,
> 
```
jnap@MyServer:ActualFolderThatIWantedToMove$ sudo mv /* /folderName
```

as you still have a logged in session, I would do
```

sudo /folderName/bin/mv /folderName/* /

```

---

### Post by Holger_Gehrke on 2015-03-12
The executables were moved to a directory that's not in the $PATH, so the shell doesn't find them. Unless they need some libraries (which were also moved, weren't they ?) you can just call them with a path, something like:
```

./bin/mv bin/ /

```
has a chance of working. If that doesn't work (because of moved libraries, probably) than the second thing you can try is using 'busybox', which normally should be linked statically. busybox is an All-in-One program containing minimal versions of all the usual tools (busybox --help gives a list), so try
```

./bin/busybox mv bin/ /

```

---

### Post by jnap2 on 2015-03-12
@[**[COLOR=#000000]spjackson[/COLOR]**]("http://ubuntuforums.org/member.php?u=1128302")
No i can't do that, the sudo command, returns the file command or directory doesnt exist... Cant access any command.

@[**[COLOR=#000000]Holger_Gehrke[/COLOR]**]("http://ubuntuforums.org/member.php?u=1961578")
I understand that the environment var it's outdated, so i thought that executing the commands directly from the new location, they should work... if they didn't any libraries, like the LS command just to check the "damages", but they don't.
Like i wrote i can navigate to the bin and sbin folders in the new location, and tried to run inside the folder, outside the folder, with ./ prefix to execute... but the same problem. 
The busybox has the same problem... 

Thanks for the replies.

---

### Post by jnap2 on 2015-03-12
Finally get the busybox to work, but now i can't move the folders, need to be root to do that... 
The sudo command doesnt work, there's another way to make busybox run as root, or force to move the folders?!

Thanks

---

### Post by SeijiSensei on 2015-03-12
Reboot, then when you see the menu of options, put the cursor over "Ubuntu" and hit enter.  Choose the option to boot into "[Recovery Mode](https://wiki.ubuntu.com/RecoveryMode)."  Choose "root shell" when offered.  You'll end up at a prompt but you won't be able to save anything because the file system will be mounted read-only.  To fix that, run
```
mount -o remount,rw /
```
(Note there is no space after the comma.)  Now you should be able to fix the problem.

---

### Post by jnap2 on 2015-03-12
@[**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195")
Thanks, but for that i need to be near the computer, need to connect a screen and a keyboard, and like i wrote, only tomorrow... :)

I'm just trying to solve the problem today. :)

---

### Post by spjackson on 2015-03-12
> **jnap2 said:**
> @[**[COLOR=#000000]spjackson[/COLOR]**]("http://ubuntuforums.org/member.php?u=1128302")
No i can't do that, the sudo command, returns the file command or directory doesnt exist... Cant access any command.

Ah yes, I should have said:
```

/folderName/usr/bin/sudo /folderName/bin/mv /folderName/* /

```
but now I realise that won't work. sudo won't work without /etc/sudoers and other /etc files. I think you are snookered - recovery it is.

---

### Post by jnap2 on 2015-03-13
After several tests, the only thing that worked was busybox, but didn't do anything without root permissions... 
So the final solution, was the ubuntu cd, boot in recovery mode, and put everything in the right place. 
Now it's working fine.

Thanks everyone.

---

