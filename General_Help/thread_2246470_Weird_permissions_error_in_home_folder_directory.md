---
title: "Weird permissions error in home folder directory"
date: 2014-10-01
forum: General Help
---

### Post by impinball on 2014-10-01
A little while back, I downloaded a FUSE driver made to interface with a specific cloud storage provider, and I want it to mount on startup with standard user privileges to a specific subdirectory of my $HOME. My biggest problem (and I don't believe this to be a software bug) is that my permissions are showing up like this when I run `ls -alf`:


    ```
d?????????   ? ?     ?          ?            ? <folder>/
```


If I run the same command as root (I can only view it with root access), I get this:


    ```
drwxrwxr-x   2 <username> users   4096 Aug 12 00:19 <folder>/
```


I can't change the group at all to my username, either, even through root. I've tried both `sudo chown <user>:<user> <folder>` and `sudo chgrp <user> <folder>`, neither to any avail. It is deletable, though.


Could I get any help on this?


Note: this is when the FUSE pseudo-partition is mounted.

---

### Post by steeldriver on 2014-10-01
Check that you have execute permission for the **parent** directory

---

### Post by impinball on 2014-10-02
I have execute privileges all the way to root.

---

### Post by matt_symes on 2014-10-02
Ho

> **impinball said:**
> A little while back, I downloaded a FUSE driver made to interface with a specific cloud storage provider, and I want it to mount on startup with standard user privileges to a specific subdirectory of my $HOME.

Which cloud storage provider ? Where did you get the driver from ? Please provide a link.

> My biggest problem (and I don't believe this to be a software bug) is that my permissions are showing up like this when I run `ls -alf`:

    ```
d?????????   ? ?     ?          ?            ? <folder>/
```


What is the mount command you are using ? Are you using fstab ? Please supply the fstab entry.

Please detail all the steps you have taken so far as you have not really provided enough information to provide useful support.

Kind regards

---

### Post by impinball on 2014-10-06
The FUSE driver is gdrive-ocaml-fuse (shouldn't be hard to look up). Here's my /etc/fstab entry:

```
gdfuse#default /home/<name>/GoogleDrive fuse uid=1000,gid=100 0 0
```

I've tried the following commands on that folder:

```

sudo chown <name>:<name> ~/GoogleDrive # And variants per-user/group
sudo chmod 0775 ~/GoogleDrive
sudo setfacl -b ~/GoogleDrive

```

I also tried fixing the GID (supposed to be 1000) in the /etc/fstab entry (it was incorrect), and it didn't work.

Currently, only root can access the contained files when mounted.

I would also like to mention that [FONT=courier new]sudo stat -c "%a" ~/GoogleDrive[/FONT] correctly returns 775.

---

### Post by matt_symes on 2014-10-06
Hi

I was not aware of that fuse filing system. Thanks.

To start with i should state i am using 14.04 - i'll let you guess which flavour. 

Anyway, by following these instructions here (that also look pertinent to 14.04) ....

[http://www.ubuntugeek.com/how-to-mount-google-drive-in-ubuntu-linux-using-google-drive-ocamlfuse.html](http://www.ubuntugeek.com/how-to-mount-google-drive-in-ubuntu-linux-using-google-drive-ocamlfuse.html)

...i can mount my Google Drive directory under a folder i created in my home directory called google_drive.

```
google-drive-ocamlfuse ~/google_drive
```

As standard, i had to allow and authorise google-drive-ocamlfuse and get a valid token to mount it.

Interestingly, when i authorised google-drive-ocamlfuse to get the token, it did say the token would only be valid for 30 days. I good security measure, however, it looks like it will need to be reauthorised every 30 days.

So some questions.

Do you have a valid authorisation token and has that token expired ?

Ignoring mounting through fstab for the moment, can you mount using the command google-drive-ocamlfuse as i did above and as detailed in the link ?

Also, i should highlight this from the linked web page.

> If something still doesn't work, try starting from scratch removing  everything in ~/.gdfuse/default. In this case you will need to  reauthorize the application.

Kind regards

---

### Post by impinball on 2014-10-08
Reply inline in bold.

> **matt_symes said:**
> Hi

I was not aware of that fuse filing system. Thanks.

To start with i should state i am using 14.04 - i'll let you guess which flavour. 

**I personally use Ubuntu GNOME 14.04.**

Anyway, by following these instructions here (that also look pertinent to 14.04) ....

[http://www.ubuntugeek.com/how-to-mount-google-drive-in-ubuntu-linux-using-google-drive-ocamlfuse.html](http://www.ubuntugeek.com/how-to-mount-google-drive-in-ubuntu-linux-using-google-drive-ocamlfuse.html)

...i can mount my Google Drive directory under a folder i created in my home directory called google_drive.

**I have been using** [FONT=courier new]mount ...[/FONT] **instead. Maybe setting it via a user cronjob may be the more optimal route here. I'll post a second thread if this doesn't work. I'll simply delete the mount folder and fstab entry.**

```
google-drive-ocamlfuse ~/google_drive
```

As standard, i had to allow and authorise google-drive-ocamlfuse and get a valid token to mount it.

Interestingly, when i authorised google-drive-ocamlfuse to get the token, it did say the token would only be valid for 30 days. I good security measure, however, it looks like it will need to be reauthorised every 30 days.

**I'm pretty sure that's the Google API at work, not the FUSE driver.**

So some questions.

Do you have a valid authorisation token and has that token expired ?

**It likely has.**

Ignoring mounting through fstab for the moment, can you mount using the command google-drive-ocamlfuse as i did above and as detailed in the link ?

**I'm currently not on my home computer, but I'll post a separate thread if that doesn't work.**

Also, i should highlight this from the linked web page.



Kind regards

---

### Post by matt_symes on 2014-10-08
Hi

Hmm. I did not expect you to make only thee posts in a week as i was going to take the step by step approach. However, at this rate we will be here till Christmas and beyond :)

> gdfuse#default /home/<name>/GoogleDrive fuse uid=1000,gid=100 0 0

To start with then, did you really mean gid=100 ? Are you sure you did not mean gid=1000

Anyway, i have spent the last 10 minutes playing with it with the help of some instructions.

The technique to mount it is similiar to a technique i used to mount an encfs folder at boot time before i decided to manually enter the password each time i wanted to use the folder.

I have it working to the point to where i can mount it manually. I have not tried a reboot to see if that works as i don't intend to reboot until the weekend. Also, i cannot mount it in Thunar yet so i need to look into that as well.

But this is what i did.

First install google-drive-ocamlfuse

```

sudo add-apt-repository ppa:alessandro-strada/ppa
sudo apt-get update
sudo apt-get install google-drive-ocamlfuse
```

Next i ran...

 ```
google-drive-ocamlfuse
``` 

...from the command line. 

This will open up a browser where you can allow google-drive-ocamlfuse to access your Google drive account and acquire an authentication token.

I made a directory in my home folder to mount Google Drive onto.

```
mkdir ~/google_drive
```

I did not need to but you can then add yourself as a member of the fuse group.

```
sudo usermod -aG fuse $USER
```

Reboot after this.

Then open a terminal again and copy and paste this entire block into it.

```

sudo bash -c 'cat>/usr/bin/gdfuse<<"EOF"
#!/bin/bash  
google-drive-ocamlfuse -label $1 $* 
exit 0
EOF'

```

Enter your password when prompted. It will not be echoed to the screen.

This creates a file that will mount your Google Drive onto the directory mount directory - in my case ~/google_drive that i created earlier. The above script gets called by the mount command and is referenced in /etc/fstab.

I Made the above script executable (you can, of course, change the permissions).

```
sudo chmod 755 /usr/bin/gdfuse
```.

Next google-drive-ocamlfuse, when run as root, needs to know the whereabouts of the credentals file that contains the authentication token as root will be mounting it so i created a symlink from ~/.gdfuse to /root.

```
sudo ln -s /home/$USER/.gdfuse /root
```

Finally, i added an entry to fstab

```
echo "gdfuse#default  /home/$USER/google_drive     fuse    allow_other,uid=1000,gid=1000   0       0" | sudo tee -a /etc/fstab
```

This contains a reference to the file we created earlier.

Finally i can mount it, the files and folders look good and i can create a file on Google Drive.

```

matthew-laptop:/home/matthew:3 % mount | grep google
matthew-laptop:/home/matthew:3 % sudo mount ~/google_drive
matthew-laptop:/home/matthew:3 % mount | grep google      
google-drive-ocamlfuse on /home/matthew/google_drive type fuse.google-drive-ocamlfuse (rw,allow_other)
matthew-laptop:/home/matthew:3 % ls -ld google_drive/general
drwxrwxr-x 2 matthew matthew 4096 Apr  6  2014 google_drive/general/
matthew-laptop:/home/matthew:3 % ls google_drive/general/test
ls: cannot access google_drive/general/test: No such file or directory
matthew-laptop:/home/matthew:3 % touch google_drive/general/test
matthew-laptop:/home/matthew:3 % ls -l google_drive/general/test
-rw-rw-r-- 1 matthew matthew 0 Oct  8 21:22 google_drive/general/test
matthew-laptop:/home/matthew:3 % sudo umount ~/google_drive
matthew-laptop:/home/matthew:3 % mount | grep google           
matthew-laptop:/home/matthew:3 % 
```

As i said, i have not tried rebooting and seeing if it will automount on boot. Anyway, I would generally not want fstab to automount it when booting up as i may not be connected to the Internet. To stop it mounting at boot, try adding the noauto option to the line in /etc/fstab.

I usually prefer to mount network mounts manually either from Thunar or from the command line but, as i said, Thunar is not mounting it at the moment. I will look into that.

See what i have done and compare it to what you have done and post back.

BTW: I used $USER as i don't know your username so you should just be able to copy and paste the commands.

**EDIT: **

If you need to clear the cache you can run this run the terminal.

```
google-drive-ocamlfuse -cc
```

Kind regards

---

### Post by impinball on 2014-10-10
Well, the installation instructions on the [project's installation page]("https://github.com/astrada/google-drive-ocamlfuse/wiki/Automounting") are clearly wrong. This completely resolved the problem. I'm going to delete this fstab entry and create a user cronjob.

---

