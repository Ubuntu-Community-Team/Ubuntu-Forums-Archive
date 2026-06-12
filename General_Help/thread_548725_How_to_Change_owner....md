---
title: "How to Change owner...?"
date: 2007-09-11
forum: General Help
---

### Post by naviuk on 2007-09-11
Hi

I'm new to this OS and am trying to change the owner of a folder so i can edit the permissions. the current owner is set to www-data and i have tried all i know and could play around and see but nothing has worked.

Does anyoe know how i can go about changeing the owner? or just deleteing a folder without being the owner?

thanks :)

---

### Post by merlinus on 2007-09-11
sudo chown -R username:username /folderlocation/foldername

where username is your login id.

---

### Post by flatwombat on 2007-09-11
Here's a good tutorial on CLI that might help: [http://www.linuxcommand.org/](http://www.linuxcommand.org/)  Pay attention to Chapter 7 for what your after and remember that in Ubuntu, you access root permissions by starting the commands with 'sudo' (i.e. 'sudo chown yourname document1).  Watch what you do and keep careful track in case you have to un-do things.  Chmod might be a better option, depending on what you're after, and if it's a directory, you might read up on -R options.

You can also get info from a terminal by typing "man chown" and "man chmod"   When done reading, hit "q" to quit the manual.

---

### Post by mcduck on 2007-09-11
Be aware that you shouldn't usually change permissions or ownerships of files/directories outside your home. Changing them will at least compromise your security, and in worst cases might actually break your system.

I suppose your problem is now that you have a web server and you need to add files to it's directory? The best way to do that would be to add yourself to the www-data group so you'll always have write privileges there ('sudo adduser YOURUSERNAME www-data'). The other way is to just open the file manager with root privileges by running 'gksudo nautilus' and then using that to move the files.

Since you don't seem to be familiar with the use of 'sudo' in Ubuntu, you might want to read this: [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by RichPicker on 2007-10-13
I'm gettting this when I enter the command in the terminal.

chown: missing operand after `

Help.

---

### Post by bodhi.zazen on 2007-10-13
What command did you enter exactly ?

---

### Post by RichPicker on 2007-10-13
rich@rich-laptop:~$ sudo chown -R rich:rich/Desktop/alsa-lib-1.0.14a
Password:
chown: missing operand after `rich:rich/Desktop/alsa-lib-1.0.14a'
Try `chown --help' for more information.
rich@rich-laptop:~$

---

### Post by defrex on 2007-10-13
You'll want: 
*sudo chown -R rich:rich /home/rich/Desktop/alsa-lib-1.0.14a* 

Though if it's on your desktop you're already the owner, so it's a little redundant...

---

### Post by RichPicker on 2007-10-13
That did it. Thank you very much. Incidentally. I have had files in my Trash that I did not have permissions to delete. Oh well... The files are off my desktop now, and I have written down the command structure. Thank you.

---

### Post by RichPicker on 2007-10-13
Here is an example of a file located 'somewhere' in my trash bin, that I can not delete. This is the error message I get when I try to remove them from the trash.

"/home/rich/.../gspca.mod" cannot be deleted because you do not have permissions to modify its parent folder

I've searched for this file, but can not find it. Such a puzzle.

---

### Post by bodhi.zazen on 2007-10-13
Try the command line :

```
cd ~/.Trash
sudo rm -rf <file>
```

Or with nautilus :

```
gksu nautilus
```

---

### Post by RichPicker on 2007-10-13
Here's the message:

"/home/rich/.../gspca.mod" cannot be deleted because you do not have permissions to modify its parent folder.

And I do not see any icons in the trash folder.

---

### Post by bodhi.zazen on 2007-10-13
Is it a link ?

---

### Post by ke4ram on 2007-10-13
I just returned from the site explaining the reason sudo is used and why root is locked away safely to protect us from ourselves. I gotta give it to you security types.  It's secure...

Exactly from what I'm not sure of but it's so dammed secure One cannot format a floppy or change the boot up sequence of Grub easily, One of the first things I did with my Red Hat system was to make a boot floppy. This highly important issue is for some reason, (Probably Security issues), avoided in Unbuntu.  I have run as root for 9 years on my server... no crashes :guitar:

You'd think we were using systems that if messed up might somehow jeopardize the security of our 'homeland' :)

Hey guys,,, this is supposed to be fun... remember :confused:

If I screw it up I'll reload :popcorn:

---

### Post by RichPicker on 2007-10-13
Here is the screen shot.

---

