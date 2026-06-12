---
title: "how to set up gmailfs"
date: 2008-01-06
forum: General Help
---

### Post by brett611 on 2008-01-06
I have installed fuse and gmailfs.  However I have NO clue what to do next.  For baseline purposes I'm used to installing it in XP and then just seeing GDrive as a drive in My Computer.  So basic instrux are requested.
Thanks!

---

### Post by mannih2001 on 2008-01-07
How about [http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem-using.html](http://richard.jones.name/google-hacks/gmail-filesystem/gmail-filesystem-using.html) ?

---

### Post by brett611 on 2008-01-07
Looks perfect!  However, it mentions fstab, which I've mangled in the past so I want to be extra carefull w/r/t the following part of the instrux:

---
To use fstab, create an entry /etc/fstab that looks something like:

/usr/local/bin/gmailfs.py /path/of/mount/point gmailfs noauto,username=gmailuser, password=gmailpass, fsname=zOlRRa
Note: If you cut and paste this entry remember to remove the spaces after the commas

The username and password fields speak for themselves. The fsname is the name of this Gmail filesystem. It is important to choose a hard-to-guess name here - because if others can guess the fsname, they can corrupt your Gmail filesystem by injecting spurious messages into your Inbox.

To mount from the command line, do:

mount -t gmailfs /usr/local/bin/gmailfs.py /path/of/mount/point -o username=gmailuser, password=gmailpass, fsname=zOlRRa 
---

My questions are:
The only things I need to edit in the fstab entry are the gmail user name, password and the fsname?  That is I can just paste the entire line and customize those values and leave the rest the same (except for the spacing)

Does it matter where in fstab I put this line?

what is the fsname?  does it 'appear' anywhere?  he mentions a hard to guess name...why wouldn't I put in a 64 char randomly generated name then?

Mounting - am I going to have to enter that mount command every time I reboot?  are the only edits needed the user name, password and fsname? That is I can just paste the entire line and customize those values and leave the rest the same (except for the spacing)

Thanks!!

---

### Post by brett611 on 2008-01-10
<bump>

---

### Post by Mark Nikkels on 2008-01-10
Is it working?

---

### Post by brett611 on 2008-01-11
Haven't tried yet as I have questions regarding editing fstab, etc and have bad experiences with trying to guess how to edit it correctly

---

### Post by brett611 on 2008-01-21
As expected, the instructions at that site assume I know what i'm doing.  I edited fstab and nothing happened.  I tried the mount command and got errors.  I'm attaching both for your entertainment...and assistance. 

Baseline knowledge = WinXP double click .exe files and things work.  So if it involves more than a double click I need explicit instrux.

Thanks in advance

---

### Post by brett611 on 2008-01-23
<bump>

---

### Post by tact on 2008-01-24
Just looked into the error text.  Problem is your mount point does not exist.

Not scolding or calling you silly.  Teaching - when you want to mount something you have to mount it somewhere that exists.    " /path/to/mount/point" is not a directory path that exists on your PC.

The instructions you followed assumed that you would know you need to create a mount point (make a directory).   Still in teacher mode:  There is a directory on your machine /media.  Pretty much any file system you mount on any subdirectory in /media will automatically show up as a drive icon on your desktop.  So if you want your gmail gdrive to show up on your desktop (and in menus) as a drive then make a folder in /media for it and mount it to that folder.   


You can do all this using a GUI but its painful to type the reams of text needed to explain where to click etc.  If its ok to use CLI then it goes like this:
```
sudo mkdir /media/gdrive
```

At the moment it is owned by root not you.  You take ownership like this:  (Replace "brett611" with whatever your username is):
```
sudo chown brett611 /media/gdrive
```

Now you want to make that folder read/write to you as a user.  
```
sudo chmod 0700 /media/gdrive
```

Now your mount command should look like this....
mount -t gmailfs /usr/local/bin/gmailfs.py /media/gdrive -o username=gmailuser, password=gmailpass, fsname=zOlRRa

---

### Post by brett611 on 2008-01-24
Tact - you rock.  That's exactly what I needed to hear.  I've never mounted something using this method, the only other 'mount' i've dealt with is for a usb hard drive, which appears automagically.

I'll try it later tonight and let you know.
Thx again

---

### Post by tact on 2008-01-26
I thought I would give gmailfs a shot to see for myself what its like.  Instead of following that guide you mention I had a quick look in synaptic to see if there is anything in the repositories.  gmailfs and the libgmail packages are there in the gutsy repo so I installed from there...  so easy.

Having installed I found I could not mount the gmailfs file system and did some reading here.  People suggesting that the libgmail supplied has some problems and need to update it.  I followed instructions and did that.  After that I managed to get the gmail file system mounted but only in a "root session"...

It seems pretty buggy and not so useful for me so I uninstalled and let it be - happy to be a little wiser for having tried.  :)

Good luck with it if you press forward.  :)

---

