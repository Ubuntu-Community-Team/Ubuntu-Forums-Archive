---
title: "Home folder permission"
date: 2007-10-10
forum: General Help
---

### Post by MarshyTheKid on 2007-10-10
Similar problem as [this thread.]("http://ubuntuforums.org/showthread.php?t=565934") 

I caused this by changing my permissions of my / folder so I could change files, instead of only root.

I changed my home folder permissions to 766, then when to change my permissions for my username directory to 755. 
```
root@ubuntu:/media/disk/home# chmod 755 marshythekid/
root@ubuntu:/media/disk/home# 

```
Nothing came back in the terminal, so I assumed it worked, but in the file browser, my user directory doesn't show up as a folder, but a blank file and will not display the permissions.
I'm running on a live CD, trying to fix it.
Any clue what to do?

Is this the easiest way to fix my mistake? I don't really want to reinstall. Is there a way to just repair the permissions?

---

### Post by MarshyTheKid on 2007-10-10
Okay, I am able to get into my user directory, but it will not list anything
I have tried ```
chown -R marshythekid.marshythekid marshythekid/
```
But it says 
```
chown: 'marshythekid.marshythekid': invalid user
```

---

### Post by finferflu on 2007-10-10
First off, I would strongly recommend you to never allow the normal users to access your /. You have sudo for handling privileged files. It's a security thing.

Secondly, try to chown the folder instead, like this:
```
sudo chown <yourusername> marshythekid
```

also, to see what is going on, run this command:
```
ls -la /media/disk/home
```

and post the output here.

EDIT:
What are you trying to achieve with that command, is that period supposed to separate the user from the group? If so, you should use a colon:
```
chown -R marshythekid:marshythekid marshythekid/
```

---

### Post by MarshyTheKid on 2007-10-10
Still comes back with invalid user.
```
sudo chown {login_name} {user_folder}
```
Right? 




```
ubuntu@ubuntu:~$ ls -la /media/disk/home
total 12
drwxr-xr-x  3 root root 4096 2007-10-03 21:55 .
drwxrwxrwx 21 1000 1000 4096 2007-10-10 16:05 ..
drwxrwx--- 49 1000 1000 4096 2007-10-10 23:08 marshythekid
ubuntu@ubuntu:~$ 

```

Once I get into my user folder, how can I set all the permissions correctly?

---

### Post by finferflu on 2007-10-10
Are you still running that command from the liveCD? Of course it will not find your user, since it's not configured on the liveCD, you have to do this operation from the actual system you have installed, if possible. 

Also, in order to set the same permission on all the folder's contents you run chmod recursively on your home folder:

```
chmod -R 775 ~
```
if you want to change them to 775. 

Also, as a reference, this page might come handy to you: [http://www.linuxcommand.org/lts0070.php](http://www.linuxcommand.org/lts0070.php)

---

### Post by MarshyTheKid on 2007-10-10
In order to log in I need to change the permission on ,dmrc
I should be able to have that work right?

---

### Post by bodhi.zazen on 2007-10-10
You should do this from the hard drive (boot to recovery mode).

---

### Post by MarshyTheKid on 2007-10-11
Okay, I booted into recovery mode and set the permissions of my Home to 755 and for .dmrc, yet I still get the same errors.



Edit: Hmm. Perhaps 775 would work. My bad. I hate having to keep rebooting like this. So annoying. I feel like I'm on Windows.

---

### Post by bodhi.zazen on 2007-10-11
.drmc file permissions, in a terminal: (use first set)

> 	sudo chmod 644 .dmrc
	sudo chown user_name .dmrc
	sudo chmod 755 /home/user_name
	sudo chown -R user_name /home/user_name

	OR, if that fails:

> 	sudo chown -R user_name /home/user_name 
	sudo chmod 755 /home/user_name
	sudo rm -rf /home/user_name/.dmrc

You do not need sudo if you are in recovery mode ...

---

### Post by MarshyTheKid on 2007-10-11
What do the permissions need to be for /?
I had changed them which is what caused this all to happen.

---

### Post by bodhi.zazen on 2007-10-11
IMO, if you changed the permissions for / and all sub directories, best re-install.

---

### Post by MarshyTheKid on 2007-10-11
Ugh. I was afraid it would come to that. I just got done with a reinstall and was trying to get everything working properly.

Would importing settings work, or not since I ****** up the permissions? I want to do this as easily as possible. I had my laptop before to steal my Firefox stuff from. Not anymore. 
How can I back up all of my files from my user folder? I had some important files that I don't want to lose. I can't get to it from the file browser.

Also should I reformat everything, or just reinstall? I don't know if I am able to reinstall without reformatting.

---

### Post by finferflu on 2007-10-11
Can you see your files with the ls command from a terminal? Like this:

```
ls ~
```

If so, the best thing to do is to use a usb stick and copy all the stuff via terminal. 

```
cp -R ~/* /path/to/usb_drive
```

That copies all the contents of your home folder in the usb stick. Notice that you might need sudo if the permissions are messed up. Once you have copied all you need, I suggest you to copy the files from the usb stick to your newly installed system selectively, setting the right permissions to every file and folder. To know what the right permissions were, just run

```
ls -l ~
```

and you will see the permissions in terms of rwx. The link I gave you earlier on ([http://www.linuxcommand.org/lts0070.php](http://www.linuxcommand.org/lts0070.php)) explains how to read that and how to set them. 
I'm not entirely sure this is the best way to restore your backup files, but it works at least.

---

