---
title: "I want to rename my DVD"
date: 2007-01-10
forum: General Help
---

### Post by mistypotato on 2007-01-10
Right now, my DVD drive is called CDROM0

But I want it to be "DVD", not cdrom

Is there anyway to change this?

And what did I do if I ran "ln -s cdrom0 DVD" ???

Thanks

---

### Post by bruenig on 2007-01-11
First your dvd drive is not called cdrom0, that is where it is mounted, there is a difference. 

Secondly the command that you put up creates a symbolic link so that when you go to DVD it will actually send you to cdrom0 which is pretty much the same thing as having it mounted there. The problem is that symbolic links need absolute paths. So you would need to change it to say something like
```
sudo ln -s /media/cdrom0 /media/DVD
```
or where /media/DVD is, you could put anywhere on the filesystem you wanted it to be.

Another solution would be to just change the fstab entry to have it mount somewhere else.
```
gksudo gedit /etc/fstab
```
Change where it says /media/cdrom0 to /media/DVD or again wherever you want it to mount on the filesystem save the fstab and exit. After you do that, you would need to make sure to make that directory.
```
sudo mkdir /media/DVD
```
Or again /media/DVD is anywhere you want it to be just make sure it is the same.

Don't do both of those solutions, that would create some weird results I am sure.
I should also mention that the command you used could be an issue depending on where you did it. I assume since there is no sudo that you must have issued it in /home/username and if that is the case then you will just have a broken symlink floating around in your home directory, not that big of a deal. But if you did that after you had changed into the /media directory (this would make more sense) there might be some problems because if you did change into /media before running those commands you will have a broken symbolic link at /media/DVD and since that is the same name as the symlink I am offering for you to use and the same name as what I told you to change your fstab to, there are some obvious problems. Find that symlink if you can and delete it especially if it is /media. Or if you aren't sure just use /media/DVD0 or whatever else you want instead of /media/DVD in all of that stuff above.

The last solution is just don't worry about it. Don't really see this as a big issue. cdrom0 is where your dvd drive mounts, not really a big deal. Risk/Reward here is very disproportionate.

---

### Post by mistypotato on 2007-01-11
Thank you VERY much for this detaild and helpful reply :-D 

I'm going over it and trying your suggestions.


Take care!

---

