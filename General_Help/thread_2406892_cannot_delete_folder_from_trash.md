---
title: "cannot delete folder from trash"
date: 2018-11-27
forum: General Help
---

### Post by jgw on 2018-11-27
I was deleting all pia files from my system before I re-installed.  I managed to move the /opt/pia folder to trash instead of a plain delete.  I now have this folder in my trash and cannot remove it .  I also have, now, another /opt/pia folder which I am using so I can't restore it.  This gets very strange.  If I goto trash I can see the folder.  If I right click on it I get a box which says "pia Properties" and "basic" on another line and then the name, number of items and size.     The one currently installed, when right clicked gives the normal stuff including permissions (root owner, user, etc)  I have tried to delete this by going to the file with the terminal.  I cannot see the file no matter what I do (including using gio).  I have tried to remove it with "sudo" followed by everything I could find but it refuses to be even seen let alone getting deleted.  

This is pretty mysterious.  I found several entries on how to delete something from the trash and tried them all to no avail.  I have not done the trash-cli thing as I thought I had better get some advice before I REALLY screw things up.

Thoughts?

---

### Post by MoebusNet on 2018-11-27
I'm pretty sure you can format the partition you're going to install/reinstall during the installation process itself where you select the installation location. You might have to do a manual partition to tell it to format the partition you're using if you're not using the whole HDD/SSD. Formatting will destroy all the files in the formatted partition(s).

---

### Post by jgw on 2018-11-27
Thanks for the reply.
I really don't want to format my partition, seems a bit of overkill to me and I am not that adventurous nor do I know, exactly, where all the files are buried.  There are over 1100 of them and I fear I would be reformatting my HD which would mean I would have to reinstall, etc.

---

### Post by MoebusNet on 2018-11-28
If the files are important to you, they should be backed up to a different storage device (different HDD/SSD, flash drive, CD/DVD, cloud, etc.) If you are determined to reinstall your OS, if/when you lose all the previous files, you can recover them from your backup. As far as deleting the /opt/pia folder from trash, I believe you can ```
 gksudo *nautilus* 
``` to open *nautilus* (replace *nautilus* with the file manager your desktop environment is using) as root. That should give you the permissions necessary to delete the /opt/pia folder from Trash.

---

### Post by jgw on 2018-11-28
Tried that - what happened is that the folder did not appear (this one is REALLY strange!)

---

### Post by MoebusNet on 2018-11-29
Are you sure this isn't a hidden file folder? Example: './opt/pia' instead of '/opt/pia'? You might need *yourfilemanagerhere*>View>Show Hidden Files. Another question - I was assuming (we all know what happens when you assume) that you meant to reinstall the OS, but I am beginning to believe you meant reinstall PIA VPN application. Just to be sure, which one? If you just want to reinstall the application that would certainly explain your reluctance to reformat the partition! if this isn't the case, then it looks like you'll need to change the file system properties to allow deletion; I'm not familiar how to do that, but I suspect researching the *chroot* command would be a start.

---

### Post by jgw on 2018-11-29
nope, its not a hidden file.  The file, when active, however, was owned completely by root.  As I said when I started this - its VERY strange!  My tip off was when I tried to get the details and, instead, got a formatted and two colored box giving me  the physical attributes whilst not giving me the permissions

---

### Post by MoebusNet on 2018-11-30
In your shoes, I think I would consult the PIA support forums; I find it difficult to believe you are the first to run into this. Since they designed the application, it would make sense that they know how to install/delete/reinstall it.

---

### Post by Ars_Ivci on 2018-11-30
> **jgw said:**
> I was deleting all pia files from my system before I re-installed.  I managed to move the /opt/pia folder to trash instead of a plain delete.  I now have this folder in my trash and cannot remove it .  I also have, now, another /opt/pia folder which I am using so I can't restore it.  This gets very strange.  If I goto trash I can see the folder.  If I right click on it I get a box which says "pia Properties" and "basic" on another line and then the name, number of items and size.     The one currently installed, when right clicked gives the normal stuff including permissions (root owner, user, etc)  I have tried to delete this by going to the file with the terminal.  I cannot see the file no matter what I do (including using gio).  I have tried to remove it with "sudo" followed by everything I could find but it refuses to be even seen let alone getting deleted.  

This is pretty mysterious.  I found several entries on how to delete something from the trash and tried them all to no avail.  I have not done the trash-cli thing as I thought I had better get some advice before I REALLY screw things up.

Thoughts?

Maybe you can temporarily rename /opt/pia to /opt/pia.new, restore the file in trash, cd into /opt and remove it via terminal:
sudo rm -rf pia/. You can then rename pia.new back to pia.

---

### Post by MoebusNet on 2018-12-01
According to the PIA VPN Support Forum ([https://www.privateinternetaccess.com/helpdesk/search?q=linux+uninstall](https://www.privateinternetaccess.com/helpdesk/search?q=linux+uninstall)) To uninstall our application you can simply run the following terminal command ```
 rm -rf ~/.config/PrivateInternetAccess 
```

This next command removes the start or application menu icon (useful if you're just uninstalling the PIA app and not reinstalling it)

```
 rm ~/.local/share/applications/pia_manager.desktop 
```

After that you will then need to remove the following :

```
 sudo rm -rf /opt/pia 
```

```
 rm -rf ~/.pia_manager 
```

I'm not sure, but I think that should remove /opt/pia from its present location, even in Trash. Have you tried running these commands in Terminal?

---

### Post by MoebusNet on 2018-12-04
If you still have /opt/pia in Trash, it looks like you could ```
cd ~/.local/share/Trash
sudo -rf /opt/pia 
```

if I correctly interpret [https://askubuntu.com/questions/102099/where-is-the-trash-folder](https://askubuntu.com/questions/102099/where-is-the-trash-folder)

If that doesn't work then I would try ```
cd ~.local/share/Trash/files
sudo -rf /opt/pia 
```

---

### Post by jgw on 2018-12-04
Thank you for the thought.

I am not at that machine right now but I have put your suggestions on a stick drive and will test them tonight and get back with the results

thanks again!

---

### Post by jgw on 2018-12-04
I am a bit paranoid about this whole thing.  Below is what I have done and the results of the whole thing.  What I found makes no sense to me.  If you tell me to go ahead I will but take a look:

```

bash: cd: /root/local: No such file or directory
root@movies:/home/greg# cd /home/greg/.local/share
root@movies:/home/greg/.local/share# ls
root@movies:/home/greg/.local/share# cd /Trash
bash: cd: /Trash: No such file or directory
root@movies:/home/greg/.local/share# cd Trash
root@movies:/home/greg/.local/share/Trash# ls
directorysizes  expunged  files  info
root@movies:/home/greg/.local/share/Trash# cd /files
bash: cd: /files: No such file or directory
root@movies:/home/greg/.local/share/Trash# cd files
root@movies:/home/greg/.local/share/Trash/files# ls
pia

Now, for the heck of it, check /root again

root@movies:/home/greg/.local/share/Trash/files# cd /root/.local
root@movies:~/.local# ls

so, now we have .local at ~/.local but directly from /.root (getting mysterious)
Anyway, ls tells us there really is a share but from ~/.local which really is /home/greg/.local (maybe?)
Here is the results of ls from ~/local
share

Now we go to that share and then do another ls:
root@movies:~/.local# cd share
root@movies:~/.local/share# ls
nano  nautilus  webkitgtk

So, basically, this mysterious ~/.local holds something entirely different from the /home/greg/.local/share/Trash/files# ls which got is 'pia'

Your suggested command:
sudo -rf /opt/pia

I thing was supposed to be?  so, I can get the pia in files and run that command but, before I do I wanted to check and make sure I am right on that one.

cd :/home/greg/.local/share/Trash/files
rm sudo -rf pia

```

---

### Post by MoebusNet on 2018-12-07
I am not a command-line expert; most of what I do with CLI is cut-and-paste. That is why I gave you the link to the PIA support forum. What little I know about removing files by CLI is from reading [http://manpages.ubuntu.com/manpages/bionic/man1/rm.1.html](http://manpages.ubuntu.com/manpages/bionic/man1/rm.1.html) which, if I understand correctly, would make the removal command ```
 cd /home/greg/.local/share/Trash/files
sudo rm -f pia 
```

I recommend that you  read the man page for the *rm* command and confirm it for yourself, but it appears to me that it will remove file *pia* from *~/.local/share/Trash/files* only.

---

### Post by jgw on 2018-12-07
thanks for the reply...........

I did read the man page on rm and am aware of the stuff on pia (I finally got it running with the icon <g>)

I will give this one a try and see what happens - thanks again!

---

### Post by jgw on 2018-12-11
I did the:
cd /home/greg/.local/share/Trash/files
sudo rm -rf pia

It worked, thanks for all the help!

My basic problem was the location of the file, ie  /home/greg/.local/share/Trash/files instead of /home/greg/local/share/Trash

---

### Post by MoebusNet on 2018-12-20
Yeah, CLI tends to be unforgiving of those minor typos. Glad you got it sorted! When you get a chance, please mark this thread 'SOLVED' using 'Thread Tools' in the upper-right of the web page.

---

