---
title: "Help with data drive and mountpoints"
date: 2007-09-13
forum: General Help
---

### Post by timzak on 2007-09-13
I just did a fresh install of 7.04 on a 2nd computer (I've had Feisty since April on my main machine) and I mistakenly set the mountpoint on my data drive (a 2nd physical drive in the computer) to /data during the Gparted process of installation.  I really just want this drive to show up separately in the File Browser (and be named "data"), but the way I did it, it's a folder named "data" inside of /root.  I don't want it inside of /root.  I know I need to use Gparted to fix this, but I'm not sure what I should do.  Can anyone help?

Thanks very much!

---

### Post by anaconda on 2007-09-13
Just edit your /etc/fstab -file and change the mount point to be whatever you want.  Just remember to create the folder where you want to mount the drive.

sudo gedit /etc/fstab
 will let you edit the fstab.
and after rebooting it will be mounted to the new pplace.

Atleadt I think you can safely remove the /root/data -folder.. newer heard of such a folder, so it cant be needed..

---

### Post by timzak on 2007-09-13
How do you make a physical hard drive show up as a physical drive icon, separate from the Filesystem icon in Places->Computer?  For example, on my main computer, my Windows partitions show up as physical drive icons in Places->Computer.  I'd like this drive to show up as a separate physical drive in Places->Computer.

Thanks for pointing me to the fstab file, I'm just not sure what to change the mount point to in this file to make it do what I describe in the paragraph above.

---

### Post by timzak on 2007-09-13
Wow, I appear to have screwed things up.

I tried the changes you suggested (editing fstab) and saw no difference, so I decided to go into gparted and reformat hda2 (the physical drive I accidentally mounted as /data).  After doing this, I could not boot into Ubuntu anymore.  I got a command prompt which I exited out of via CTRL-D, then when I manually selected GNOME session (I wasn't able to log in until I did this, it was telling me my home directory was missing!), I was able to boot normally to the desktop.  While at the command prompt, I received the following error:

```
fsck 1.40-WIP (14-Nov-2006)
/dev/sda2: clean, 819/1474560 files, 91661/2943911 blocks
fsck.ext3: Unable to resolve 'UUID=f4b0d54e-e230-4699-baf8-dc5b3fef002b'

fsck died with exit status 8
```

/dev/sda2 is actually my home folder!  So what did I do wrong and how do I fix this?

Now, whenever I power the system on, I get the above error and a command prompt (full screen terminal).  I then hit CTRL-D and can log in normally.  Everything appears fine, so why do I get the command prompt instead of going straight to the log in screen?  Despite the error message about "unable to resolve...", my home folder appears to work fine as long as I jump through a few hoops to get to the login screen.

Here are my mount points:

sda1 = /
sda2 = /home
hda1 = swap
hda2 = my data drive (I think it's /media/disk but this seems to be up in the air too)

Hopefully someone can help me?

---

### Post by timzak on 2007-09-14
*bump*

Anyone?  I'm about ready to reinstall since I don't know how to fix my mistake.  I would appreciate any way to avoid this if at all possible.

Thank you in advance.

---

### Post by psusi on 2007-09-14
It sounds like you accidentally reformatted your /home partition instead.  To get the other drive to show on the desktop you just have to change its mount point in /etc/fstab to /media/data, and sudo mkdir /media/data.

---

### Post by timzak on 2007-09-14
I think the part that I didn't do that I should've done was "sudo mkdir /media/data".  However, I am confident that I did not format the /home drive.  It is there and accessible once I jump through the login hoops on system startup:

```
fsck 1.40-WIP (14-Nov-2006)
/dev/sda2: clean, 819/1474560 files, 91661/2943911 blocks
fsck.ext3: Unable to resolve 'UUID=f4b0d54e-e230-4699-baf8-dc5b3fef002b'

fsck died with exit status 8
```

FYI, /dev/sda2 is my /home partition.  I don't know what that UUID not being resolved part means.  But once I hit CTRL-D from the command prompt, this continues loading to the login screen, and from there, I manually select "GNOME" as my session and it logs into the OS as if everything is fine.  I can fully access /home and everything works as it should.  It just seems that somehow the UUID of the /home partition got messed up somehow and it's throwing things off.

---

### Post by timzak on 2007-09-15
This thread can be closed.  I didn't get any help so I just reinstalled on top of my first install and correctly mounted my data drive this time as /media/Data.

Thanks to anaconda and psusi for trying to help.

I'm not sure what has happened to these forums but back in April and May I used to get tons of responses when I'd have a problem.  The last 5 times or so I've posted with problems, I almost never got help, even after bumping my question a couple of times.   Not wanting to be a nag, I even asked in the Forum Feedback area if it was appropriate to bump your posts and they encouraged me to do so at least a few times before giving up.  Pretty sad when posts die with no responses from people who genuinely need help, while controversial topics that aren't helping anyone get tons of replies.  One exception was a kind person called MrC who tried very hard to help me through some networking issues.  MrC if you're reading this, thank you.  I ended up using Samba for my networking.  It was easier for me to understand and just get done what I needed to get done.

---

