---
title: "Mount a network folder via shortcut"
date: 2008-02-15
forum: General Help
---

### Post by Meta8 on 2008-02-15
Hi,
I'm trying to create a shortcut that'll simply execute the line
sudo mount -t cifs //family/music ~/music -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777
It simply mounts the SMB network folder "music" to my local folder.
Anyways, this works when I type it in the console. So, I thought, why not create a shortcut to do it instead of going to the terminal? So, I created a "Custom Application Launcher" with the line above as command but it doesn't work. I tried putting both type "Application" and "Application in Terminal."
When it's as type "application", nothing at all happens. When it's as type "Application in Terminal", the terminal shows up asking for the root password, but doesn't do anything after that (even though it looked like it did).
So... what am I doing wrong?

PS: No, I do not want to make the mount permanent :)

---

### Post by SpaceTeddy on 2008-02-15
first, is the mount imparative (i.e. do you need it in your file structure because some programms can only work on local file system) or do you just want to use "normal" acces...

in that case, vfs is quite enough... I don't know what it is called in english, but you can put shortcuts to remote folders on your desktop. Use the Places -> connect to server button then select windows share and put in your credentials... that worked for me every time i had to access windows or samba shares. 
But it does not acctually mount the share... so programs not being able to read vfs will NOT be able to use it... i.e. vlc cannot use vfs... only totem can.

is that what you wanted ?

---

### Post by Meta8 on 2008-02-15
Yeah, I need it for programs that can't access the share (mainly VLC). ANd it also feels nicer when it's mounted :)
I just thought of something. What is the equivalent of a batch file in Ubuntu (like in Windows). Or is there any kind of script I could write that would just execute the command?

---

### Post by SpaceTeddy on 2008-02-15
for the script, you can pretty much any interpreter you want... i personaly perefer perl, but you can use anything really...

also, if you just create a textfile and write command in it like you would normally do in a terminal, it will run like a batch file... (just have to make it exectuable)

i personally would suggest you do not use mount over a wireless or any other media that is not stable - it can mess up your computer pretty bad when the share is gone, but nautilus does not notice or know it... that's why i don't really like fixed mounting.

i have another idea how it could - maybe - work... but i'd have to research it myself first... really... maybe it is possible to use cifs in the fstab... maybe...

i'll see what i can find out - tomorrow !

---

### Post by outofnicks on 2008-02-15
How about just a simple shell script:
```
#!/bin/bash
sudo mount -t cifs //family/music ~/music -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=07 77
```

Save as a plain text file, with permissions of -rwxr--rwx ( 755 )

---

### Post by Meta8 on 2008-02-15
> **outofnicks said:**
> How about just a simple shell script:
```
#!/bin/bash
sudo mount -t cifs //family/music ~/music -o guest,rw,iocharset=utf8,file_mode=0777,dir_mode=07 77
```

Save as a plain text file, with permissions of -rwxr--rwx ( 755 )

Thanks! How do I set the permissions?

---

### Post by kaginken on 2008-02-15
Simple!

sudo chmod 755 <scriptname.sh>

you can then run this script from the command line in the shortcut.

Alternatively, I've always got a terminal open, so I opted to just do them by creating an alias.

When I want to mount my music share, I type 'mmusic' and that works for me because I have an alias like this:

alias mmusic="blah blah long command line to mount share here blah blah"

6 of one, half dozen of the other, take your pick!  Rock on!  :guitar:

---

### Post by Meta8 on 2008-02-16
OK, so I made the file, changed the permissions and created a shortcut to the script. Clicking it still does nothing :(
I can't say it doesn't surprise me since I didn't put my root password anywhere at all during the whole process. Unless that was supposed to be taken care of through the permission changes? I don't know.
I feel like I'm missing something obvious and ridiculously simple here. It can't be that hard!! GahhH!!!!

---

### Post by SpaceTeddy on 2008-02-17
did you put a "gksu" infront of your command sepcified in the button ? that is what you will need to do, since you will need to be root to mount (the only thing i know where you do not need to be root is when you use fuse).

so let's say your file is /home/me/mountnetwork, then your starter should have the command gksu /home/me/mountnetwork...

PS:gksu is the same sudo - just for grafics :)

---

### Post by AgentZ86 on 2008-02-17
> **SpaceTeddy said:**
> for the script, you can pretty much any interpreter you want... i personaly perefer perl, but you can use anything really...

also, if you just create a textfile and write command in it like you would normally do in a terminal, it will run like a batch file... (just have to make it exectuable)

i personally would suggest you do not use mount over a wireless or any other media that is not stable - it can mess up your computer pretty bad when the share is gone, but nautilus does not notice or know it... that's why i don't really like fixed mounting.

i have another idea how it could - maybe - work... but i'd have to research it myself first... really... maybe it is possible to use cifs in the fstab... maybe...

i'll see what i can find out - tomorrow !

Hi all

I"m currently using LInNeighborhood which solves my problem on this topic, however it does not mount my shares automatically I have to open/run the LinNeighborhood program which is ok to do it manually evertime I guess. But I prefer this method mentioned, however I'm concerned about the topic of: > (messing up your computer pretty bad

I don't have a wireless computer connected that is using these shares, but only hard wired thru the switch to the gateway which is acting as router.

Anyhow please advise on the cons of doing this ? is there  potential problem with mounting the network shares from hardwired connection ? when the shares are gone ?

Please advise 
Thanks

---

### Post by SpaceTeddy on 2008-02-17
disappearing shares are alyways a problem... and no, i don't think it is much more dangerous to use a share via mount that via vfs or something else... it is the windows shares that i always had trouble with. 

Novell and sshfs shares can always be unmounted if they, by any chance, disappear. A samba/windows share gave me severe trouble a couple of times when trying to unmount them after they were gone. nothing helped short of rebooting (which will always reset your connections - the hard way)

i have never user LinNeighbourhood, but it looks like a decent tool. If it works in all environments, i don't know. But i will not test it since i do not have any windows shares anymore... they are all moved to ssh. 
In general, you will not be able to "break" your system permanently by mounting network shares, only temporarily. A reboot will always fix these problem in the worst case. So i would not worry about it too much if you don't mind rebooting once a share or two are gone :)

---

### Post by AgentZ86 on 2008-02-17
Great thanks

I don't really want the shares to be windows, however I think with SME server my shares are automatically Samba even though it's a linux server.

I'll toy with the mounting some more and see how it goes.

LinNeighborhood works good with all programs, but it's not letting me set my shortcut deeper into the tree that I want. But it does work with all programs.

Thanks for the info

---

### Post by SpaceTeddy on 2008-02-20
did not see your post :)

if you have a linux server, and you have an ssh login, you can ALWAYS use sshfs, which even comes with fuse, so you don't need to be root to mount anything. 

if you want, you can always give it a try... install the needed package> sudo apt-get install sshfs

and make sure you are in the group fuse (can be changed via the User Management)

once that is done, restart your x-server or your computer, and watch the magic happen...
just using your normal ssh login you can mount anything on the server that your login has read rights on with
> sshfs username@host:/path/to/dir /local/mountpoint
to unmount (this is not very consistent) you can use
> fusermount -u /local/mountpoint

notice how there is no sudo here... it can all be done as a user with just the membership in the group fuse.

---

### Post by AgentZ86 on 2008-02-22
SpaceTeddy- thanks

Let me ask, If I don't login on my local machine with the same user/pass that is part of a group on the server. will that change how this mount command works ??

So (sshfs username@host:/path/to/dir /local/mountpoint) would be my username on that server, not the username of my login to the local computer ??? right ??

Please advise
Thanks

---

### Post by dark_phantom on 2008-02-22
> **AgentZ86 said:**
> SpaceTeddy- thanks

Let me ask, If I don't login on my local machine with the same user/pass that is part of a group on the server. will that change how this mount command works ??

So (sshfs username@host:/path/to/dir /local/mountpoint) would be my username on that server, not the username of my login to the local computer ??? right ??

Please advise
Thanks
From [http://fuse.sourceforge.net/sshfs.html](http://fuse.sourceforge.net/sshfs.html)
> 
> sshfs hostname: mountpoint

Note, that it's recommended to run it as user, not as root.  For this to work the mountpoint must be owned by the user.  If the username is different on the host you are connecting to, then use the "username@host:" form.  If you need to enter a password sshfs will ask for it (actually it just runs ssh which ask for the password if needed).  You can also specify a directory after the ":".  The default is the home directory.

---

### Post by SpaceTeddy on 2008-02-23
you handle sshfs as a normal ssh login... so naturally, the login needs to be of the remote computer. but the directory you are mounting it in the local filesystem (the mountpoint) must be owned by the user you are currently logged in on your local machine (since it is locally mounted)

---

### Post by AgentZ86 on 2008-02-25
Great, thanks to all, I'll try it out and see how it goes.

Thanks again.

---

### Post by eliash87 on 2008-05-22
I have the same problem as AgentZ86 on Xubuntu.

I am using sshfs. I am able to mount from the command line, but when I try to do it from a shortcut, it just doesn't work. I have tried to write the command directly in the box for the launcher and in a separate script. I have tried with and without "run in terminal", and with and without "sh" before the filename. I have tried the script with and without "#!/bin/bash" and with permissions 755 and 775. I have tried putting a "wait" and a sleep statement after the sshfs statement, to no avail. It asks for my remote password, but gives no error message or confirmation. The same very script works well when I run it manually from the terminal.

What is this? Is it normal? Am I stupid? :confused:

---

