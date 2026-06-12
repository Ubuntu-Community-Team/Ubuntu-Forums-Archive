---
title: "Lost ownership of home directory after making samba share"
date: 2014-08-17
forum: General Help
---

### Post by Last_Ship on 2014-08-17
I've located similar threads here [http://ubuntuforums.org/showthread.php?t=1885884&highlight=lost+ownership+home](http://ubuntuforums.org/showthread.php?t=1885884&highlight=lost+ownership+home) and here [http://ubuntuforums.org/showthread.php?t=1655511](http://ubuntuforums.org/showthread.php?t=1655511), but the solutions for each don't seem to work in my case. I believe I have the added complication of having full disk encryption enabled. 


I lost ownership of my home directory after pointing my samba config file to it in an attempt to share it (very stupid in hindsight, I know) . 

I now cannot login with the GUI.

I did exactly as the first thread linked above, CTRL + F1 so login via the commandline and then executed "sudo chown hpcompaq -R /home/hpcompaq/

(my username is hpcompaq)

I rebooted and when i try to login the screen flickers for a moment and kicks me back to the login screen. 

When I login via command line, I get this message upon login:

[255.343626] Mount of device (uid 65534) not owned by requested user (uid: 1000)
[255.364059] Reading sb failed; rc = [-1]
mount: Operation not permitted

Then, if I do "ls", I see two files:
Access-Your-Private-Data.desktop, and README.txt

The readme file indicates: THIS DIRECTORY HAS BEEN UNMOUNTED TO PROTECT YOUR DATA.
from the command line, run:
ecryptfs-mount-private

So when i run that command and enter my passphrase, i get:

Inserted auth tok with sig [alpha_numeric_string_is_here] into the user session keyring
fopen: No such file or directory

If I login using a guest session (which does work graphically), and  browse the file system to hpcompaq's home folder, it indicates that root  still owns it and the group is root as well.

I've also dropped into a root shell in recovery mode, cd'd into hpcompaq's home directory, and get the same results as described. 

Any insight would be greatly appreciated.

---

### Post by Last_Ship on 2014-08-20
Anyone have any ideas? At this point I'm really just trying to recover the files from my (well, now root's) home directory.

---

### Post by bab1 on 2014-08-21
> **Last_Ship said:**
> Anyone have any ideas? At this point I'm really just trying to recover the files from my (well, now root's) home directory.

What is the location of this directory?  Root only *has* only one home directory.  It's at /root (e.g it's own home directory).  The root user can  manipulate almost anything if it needs to in Linux.  You can always use sudo to change the ownership of any directory.  An *example *of this would be```
sudo chown user:user <some directory or file>
```.  If you wanted to do this along the entire file system (recursively) for the user *john* you would do something like this```
sudo chown -R  john:john /home/john
```

You can read more about chown at ```
man chown
```

---

### Post by oldfred on 2014-08-21
I avoid encryption. But if you have to have it, really good backup procedures are required.

 Includes chroot:
[https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory](https://help.ubuntu.com/community/EncryptedPrivateDirectory/#Live_CD_method_of_opening_a_encrypted_home_directory)
[http://ubuntuforums.org/showthread.php?t=2028865](http://ubuntuforums.org/showthread.php?t=2028865)
[http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/](http://www.howtogeek.com/116297/how-to-recover-an-encrypted-home-directory-on-ubuntu/)

---

### Post by Last_Ship on 2014-08-21
bab1 -- thank you for the response, I appreciate that. yes, I am familiar with the chown command. I've tried it here to no avail.

 I cannot login with the graphical interface, upon doing so I'm kicked back to the login screen. If I do ctrl+alt+F1 and log in via commandline, i receive the message "[255.343626] Mount of device (uid 65534) not owned by requested user (uid: 1000)"

Also, as i mentioned, if I login as a guest session and navigate to hpcompaq's home directory to inspect the properties, here is what i see:

[IMG]http://i.imgur.com/RDoszJe.jpg[/IMG]


I'm not sure what to make of this. One last bit that I'll add that I didn't mention before--the last command that I MIGHT have executed while trying to share my home directory with samba is 
chmod 777 ~/home/hpcompaq/  -- like I said, I'm not sure I did in fact execute that, BUT I just wanted to add that in the event that it would make a difference here.

Thanks again.

---

### Post by Last_Ship on 2014-08-21
Thanks Fred. Yes, I did have most everything backed up, unfortunately not everything though. Thanks for the links, I will go through these now. Just trying to determine if this is an ownership issue or an encryption issue first.

---

### Post by oldfred on 2014-08-21
There are places where root is correct. All NTFS partitions are that way as they do not support ownership & permissions and just inherit from mounting.

Not sure about encrypted partitions, as you do have to un-encrypt them before you can use them, so they might be. Since I do not have encryption, I cannot check.

Normal ownership & permissions of /home is like this. 
Occasionally I have to reset a folder.
       # Note that the -R is recursion and everything below is changed, do NOT run on any system partitions, or else you just might have to reinstall.

    sudo chown -R fred:fred /home/fred/new_directory 
sudo chmod -R a+rwX  /home/fred/new_directory 

 sudo chmod -R a+rwX,o-w /folder
All directories will be 775.
All files will be 664 except those that were set as executable to begin with.

But some files in /home do need unique settings.
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

### Post by bab1 on 2014-08-21
> **oldfred said:**
> ...
Not sure about encrypted partitions, as you do have to un-encrypt them before you can use them, so they might be. Since I do not have encryption, I cannot check.

It is important to note that encryption has been set and root **does not** provide the keys as the original user set the encryption.  If you can't login as the user that encrypted the data then you have little or no chance to recover the data.

This is one of the reasons I'm not a big fan of encrypting everything in your home directory.  There simply is no need.  Whether you recover any of the data or not.  I recommend you only encrypt the data that is sensitive and all in one subdirectory.

---

### Post by Last_Ship on 2014-08-21
Fred -- I followed the instructions you provided and I think I've ruled out encryption as being my issue. I booted from a live disk, recovered my encrypted drive as instructed, browsed to hpcompaq's home directory and received a 'permission denied' message. I tried this via terminal with the same results. Here are the properties that the home directory is displaying when viewing it while booted from a live disk: 
[http://i.imgur.com/ANvTUoh.jpg](http://i.imgur.com/ANvTUoh.jpg)

---

### Post by steeldriver on 2014-08-21
I'm not sure I understand the GUI presentation of attributes but that looks like dr-x------ (octal mode 500) instead of the default drwxr-x-r-x (755)

---

### Post by Last_Ship on 2014-08-22
steeldriver -- I apologize, but I don't know what that means.

---

### Post by deadflowr on 2014-08-22
> **Last_Ship said:**
> steeldriver -- I apologize, but I don't know what that means.

I believe what Steeldriver means is that the term used *Access Files* typically stands to mean that the permission are read and execute, but not write.
noted as r_x, the d meant directory.
A directory with full rights would have drwx for read/write and execute.
From what I notice, folders with full rights usually say something like create and delete files/folders in the gui properties box.
FWIW

edit: added I'm trying not to step on any toes, I apologize if it seems I have...
Also
```
man chmod
```
can give you a base idea of the permission schemes used in linux.

---

### Post by oldfred on 2014-08-22
When you boot from a live installer user 1000 is correct.

When you boot are you able to log in as your original user? 

I did have a case where I copied my link over a data folder the link referred to. At that point restore from backup was the easiest, but I had a few files not currently backed up and had to run photorec to restore data.

---

### Post by Last_Ship on 2014-08-28
All,
I am happy to report that a combination of OldFred's advice, using the chmod command along with recovering the encrypted drive while booted from a live CD, has allowed me to at least recover my files. When I login using my original username, I still get the error message [255.343626] Mount of device (uid 65534) not owned by requested user (uid: 1000)

But, I have my files so I can just do a fresh install. Although the problem is not fixed per se, I would consider this solved for my purposes. If someone could please advise whether marking this thread "solved" here is appropriate that would be very much appreciated.

Thank you everyone very much for your help. As always, I appreciate all of your effort and wisdom.

---

### Post by Last_Ship on 2014-09-02
I am marking this threat as "Solved", even though I have not regained ownership of my home directory. I will leave the computer in question in its current state in the event that anyone comes across a similar problem or is simply feeling ambitious and wants to continue working on it. Thanks again.

---

