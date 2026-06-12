---
title: "mv files from windows share?"
date: 2007-08-02
forum: General Help
---

### Post by Alein on 2007-08-02
Hello and thanks for helping;

I have 7.04 desktop running and connecting to a Windows XP share. Everything works fine in the GUI, I can copy, paste etc. What I am having trouble doing is using the CLI to do the same things. I have the share mounted on the desktop and have tried;

```
mv //XPBox/ShareName/foo.txt /home/user
mv smb://XPBox/ShareName/foo.txt /home/user
```

My goal is to move the files/files to Ubuntu, but terminal just returns that it 'cannot stat' the source.

Obviously I must be screwing up something simple in the syntax since the same thing works in the GUI. I know I can just use the GUI but I need this to run automatically on a schedule which is why I want to use the CLI.

All sugestions are appreciated.

Al

---

### Post by gerbman on 2007-08-02
> **Alein said:**
> I have 7.04 desktop running and connecting to a Windows XP share. Everything works fine in the GUI, I can copy, paste etc. What I am having trouble doing is using the CLI to do the same things. I have the share mounted on the desktop and have tried;

```
mv //XPBox/ShareName/foo.txt /home/user
mv smb://XPBox/ShareName/foo.txt /home/user
```



A couple things. I'm assuming your XP share is an NTFS partition, in which case you'll first need to install NTFS write support if you want to move files from your XP partition to your Ubuntu partition. If you simply need to copy them from NTFS, there's no need for write support. Also, the command to move files should be the following:```
mv /path/to/xp/share/foo.txt /home/user
```

---

### Post by Alein on 2007-08-03
Thanks gerbman,
 
The share is NTFS but 7.04 appears to have support built-in for it since I have made no effort to add it and I can use the GUI to connect, copy, create and delete files with no difficulty. Unfortunately your suggested syntax does not work as you can see from the attached screenshot.jpg. You will also notice the mounted share and copies of the test files on the desktop. As far as I can tell, mv and cp should work in terminal. Any other suggested syntax would greatly be appreciated. ;)
 
[IMG]http://www.thepaddlecompany.com/Screenshot.jpg[/IMG]

---

### Post by Alein on 2007-08-04
[COLOR=black]Johnny Chadda said 2 hours ago: [/COLOR]
[COLOR=black]The GUI filesystem tools are using the Gnome VFS layer, which is unavailable from the command-line.To mount a remote Windows share from the command-line, install smbfs by running "sudo apt-get install smbfs". Then mount the share in an empty directory:[/COLOR]
[COLOR=black]sudo mount -t smbfs //server/share /mnt[/COLOR]
[COLOR=black]You may specify a username with the "-o username=MyUsername" flag if necessary.[/COLOR]
[COLOR=black]Now you should be able to navigate to the /mnt directory either from the command-line or even the GUI and see the files. To unmount the share when you are done, just run "sudo umount /mnt".[/COLOR]
 
 
 
[[COLOR=black]Alein[/COLOR]]("https://answers.launchpad.net/~al562ein")[COLOR=black] said 5 seconds ago: [/COLOR]
[COLOR=black]I thought in Linux all file devices were always available from the CLI, I see now this may not always be the case.[/COLOR]
[COLOR=black]Thank you for answering my question Johnny.[/COLOR]

---

