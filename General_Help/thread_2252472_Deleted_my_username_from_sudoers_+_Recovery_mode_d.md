---
title: "Deleted my username from sudoers + Recovery mode doesn't work"
date: 2014-11-12
forum: General Help
---

### Post by Dio82 on 2014-11-12
So it seems I unleashed a perfect storm...

I accidentaly deleted my username from the sudoers group. When I try to make a sudo su, it says "user is not in the sudoers file.  This incident will be reported."

I tried to fix it following this post [http://www.maketecheasier.com/fixing-sudo-error-in-ubuntu/](http://www.maketecheasier.com/fixing-sudo-error-in-ubuntu/) but when I enter in recovery mode, the screen goes fuzzy and I cannot see anything. 

As an alternative, I tried this method, booting from a live usb (both usb and my system are 64-bits), following this post, [http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/](http://www.howtogeek.com/howto/linux/reset-your-ubuntu-password-easily-from-the-live-cd/), but when I try to chroot, it gives me this error: "chroot: failed to run command &#8216;/bin/bash&#8217;" so I cannot edit my sudoers file and/or use the command usermod.

Any idea of how to solve it? Thanks in advance

PD: My system is ubuntu 14.10

---

### Post by Yulra on 2014-11-12
Try this: [http://www.psychocats.net/ubuntu/fixsudo](http://www.psychocats.net/ubuntu/fixsudo)

Edit. You're going to need recovery mode though...

Else, back up your data and reinstall.

---

### Post by Dio82 on 2014-11-12
Thanks for the try, but when I enter the recovery mode the image goes fuzzy and I cannot see anything. I tried to do the usermod trick without "seeing", but it didn't work...

---

### Post by btindie on 2014-11-12
You can just manually edit the group files from a live system.

Boot the Live CD/USB and mount the root partition from your hard disk
```
sudo -i
mkdir /mnt/root
mount /dev/sdaX /mnt/root
```
where sdaX is your root partition.

Then just use nano or vi to edit your /mnt/root/etc/group /mnt/root/etc/gshadow files
```
sudo -i
nano /mnt/root/etc/group
nano /mnt/root/etc/gshadow
```

For /mnt/root/etc/group it should look like
> sudo: x:27:USERNAME
where the usernames are separated by commas, if there's multiple.

and for /mnt/root/etc/gshadow
> sudo:*::USERNAME

with nano, press Ctrl-O Enter to save the changes, Ctrl-X to eXit Then reboot back into your system.

---

### Post by Dio82 on 2014-11-12
It went well until I opened 
> /mnt/etc/group

The file was empty, anyway I edited it but when I tried to save I had this messsage:
> Error writing /mnt/etc/group: No such file or directory

---

### Post by btindie on 2014-11-12
Sorry, my mistake. There was a typo in that. I've now updated my original post.

Basically /mnt/etc/* should be /mnt/root/etc/*

---

### Post by Dio82 on 2014-11-12
Still nothing.

I edited both gshadow and group files (they were both empty when I opened them). I rebooted again in my hard drive and the problem is still there...

I checked (now also under my hard drive - normal system)  in /etc and there is now up to 3 files called "group":
- One called "group" where I am not in the sudo group (I am just here in the "users" group)
- Another one called "group~" where I am in the sudo group (as well as in several others)
- And a third one called also group~ that I cannot even open (it says it is locked).

Edit: and when I did the mount under the live usb environment, I just could see one group file and it was empty. I could not find any of my personal files either.

---

### Post by ajgreeny on 2014-11-12
You can't have three files in the same folder all with the same name; the system will not allow that.  It looks for your description as if you have a backup file (group~) and maybe a lock file as you have one of the other group files open.

Can you copy the files you've found back here and we can try to tell you which one is most likely to be correct.  The lock file, if that is what it is, will disappear when you close the file of that name, so you may only really have two files on disk not three as you thought.

---

### Post by mc4man on 2014-11-12
If you simply *had removed your entry in /etc/group/* then you're using unnecessarily complicated methods
Plus avoid writing to empty files as root, generally that means you've created a new file somewhere.

So if 1st. line above is correct - 
boot to live session
open nautilus, make sure your current install's volume is visible & mounted, if not mounted for some reason then click on icon to do so
Then - 
alt+F2 > enter  below command
```
sudo -H nautilus
```
navigate to your install volume > /etc, find the group file, d. click on & edit yourself back in, typically - 
```
sudo:x:27:[COLOR="#0000FF"]username[/COLOR]
```

---

### Post by Dio82 on 2014-11-12
Thanks, did it the graphical way, changed both group and gshadow and finally it works :)

Thanks to all who helped!

---

