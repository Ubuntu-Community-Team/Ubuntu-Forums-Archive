---
title: "[SOLVED] Trash can full, .Trash folder empty?"
date: 2007-07-14
forum: General Help
---

### Post by Cable on 2007-07-14
My trash can icon says it's full, and items are in it when I open it.  However, when I open the .Trash folder in my home directory, there are no files in it.  Further, when I tell the trash can to empty, it says that I do not have the permissions to do so.  These are files owned by root.  Problem is, when I go to my .Trash folder via terminal to do a
```

sudo rm -r whatever

```there are no files to delete.  Why does my trash can say files exist when my .Trash folder doesn't?  Any ideas?

---

### Post by davidjmayo on 2007-07-14
This comes with no guarantee as I never did it before (but a quick search on the forum which you should have tried first) gave these 2 links (and there are more I didn't check out-you can)

[http://ubuntuforums.org/showthread.php?t=491793&highlight=trash+root](http://ubuntuforums.org/showthread.php?t=491793&highlight=trash+root)

[http://ubuntuforums.org/showthread.php?t=486342&highlight=trash+root](http://ubuntuforums.org/showthread.php?t=486342&highlight=trash+root)

---

### Post by Cable on 2007-07-15
I did search the forum, and found the exact threads you have provided links to.  In my post above, I stated that I went to my .Trash folder via terminal to attempt using sudo to delete the files in the trash, but the .Trash folder is empty (the trash can, however, has items in it).

Neither of the threads you linked to involve the problem I am having.  They are *similar*, but not the same problem.

---

### Post by aysiu on 2007-07-15
Any chance there are hidden files in the trash? What's the output of these terminal commands? ```
cd ~/.Trash
ls -al
```

---

### Post by Cable on 2007-07-15
```

caleb@caleb-desktop:~/.Trash$ ls -al
total 12
drwx------  2 caleb caleb 4096 2007-07-15 03:28 .
drwxr-xr-x 96 caleb caleb 4096 2007-07-15 03:27 ..

```

---

### Post by aysiu on 2007-07-15
There's nothing in your trash.

Weird.

What about this? ```
cd /root/.Trash
ls -al
```

---

### Post by Cable on 2007-07-15
When I try to cd into /root/.Trash, it says permission denied.

---

### Post by sefs on 2007-07-15
Try to do that from the root terminal as opposed from the regular terminal. Launch the root terminal by going

```

gksudo /usr/bin/x-terminal-emulator

```

You will be promted for a password

Then go cd /root/.Trash

and see if anything is listed in there.

or if you want to use nautilus providing you are in gnome...

```

gksudo nautilus

```

and browse to the root folder and then the .Trash folder (remember) to turn on show hidden files in nautilus view menu.

> **Cable said:**
> When I try to cd into /root/.Trash, it says permission denied.

---

### Post by starsky on 2007-07-15
> **Cable said:**
> My trash can icon says it's full, and items are in it when I open it.  However, when I open the .Trash folder in my home directory, there are no files in it.  Further, when I tell the trash can to empty, it says that I do not have the permissions to do so.  These are files owned by root.  Problem is, when I go to my .Trash folder via terminal to do a
```

sudo rm -r whatever

```
there are no files to delete.  Why does my trash can say files exist when my .Trash folder doesn't?  Any ideas?

hi there :)
What window manager is this you're using ? gnome/kde/xfce or something else ?

---

### Post by Cable on 2007-07-15
```

root@caleb-desktop:~/.Trash# ls -al
total 8
drwx------  2 root root 4096 2007-07-15 11:43 .
drwxr-xr-x 20 root root 4096 2007-07-15 12:02 ..

```
Doesn't look like there's anything there either...this is so odd.
> **starsky said:**
> hi there :)
What window manager is this you're using ? gnome/kde/xfce or something else ?
I'm using gnome.

---

### Post by starsky on 2007-07-15
> **Cable said:**
> ```

root@caleb-desktop:~/.Trash# ls -al
total 8
drwx------  2 root root 4096 2007-07-15 11:43 .
drwxr-xr-x 20 root root 4096 2007-07-15 12:02 ..

```
Doesn't look like there's anything there either...this is so odd.

I'm using gnome.

is your icon lying to you ? I have a trash icon here in my gnome desktop . It shows me that it's full. but there's nothing inside. :)
It's just the icon design i guess.

And just to verify, if I delete any file from NAUTILUS, this goes to my ~/.Trash directory and "ls -al" shows the file but the icon of my TRASH on desktop doesn't change a bit. So i am guessing this is the same with you. :) So in essence could be the ICON design of TRASH in your particular GNOME theme.

HTH

---

### Post by Cable on 2007-07-15
Nope, it's definitely not the icon lying.  Attached are screen shots of the trash can and my .Trash folder.  Odd thing is, when I send new things to the trash and empty it via the trash **applet**, it empties only the new things, and not the items shown in the screen shot (no errors).  When I open the trash and click the "Empty Trash" button, it empties the new items and not the items in the screen shot, AND I get the attached error window.

---

### Post by starsky on 2007-07-15
ok let's give this a try

become root, delete the files
```


$ su -

$ cd ~/.Trash

$ rm -rf *


```

See how it goes

---

### Post by rodo-&gt;dave on 2007-07-15
Hi. Is /media/Stuf... attached to your system when you empty the trash?
Seems kinda like a link to another drive/device that is/was connected.

---

### Post by Cable on 2007-07-15
> **rodo->dave said:**
> Hi. Is /media/Stuf... attached to your system when you empty the trash?
Seems kinda like a link to another drive/device that is/was connected.
Yes it is.  It's just another partition on my internal HDD.

---

### Post by rodo-&gt;dave on 2007-07-15
Hmm.. the part that has me boggled is why it would be "/media/Stuf..." - does this partition have it's own .Trash somewhere?

I know on my USB, if I select a file and "move to trash" it puts the file in the USB .Trash folder.

---

### Post by Cable on 2007-07-15
That was the trick right there.  There was a .Trash folder on the partition itself, and the files were located in that folder.  All taken care of now.  I feel stupid.  :-P  Thanks for the help.  :-)

---

### Post by oomingmak on 2007-07-16
> **Cable said:**
> There was a .Trash folder on the partition itself, and the files were located in that folder.  All taken care of now.**  I feel stupid**.
No need to feel that way. 

You would have noticed what was going on if Nautilus bothered to provide users with a file path column in their file manager windows (because you would have seen where the file had been deleted from). As it is, you are left to guess where things are located.

---

### Post by soxs on 2008-02-20
I have the EXACT SAME problem. My GUI shows some data in Trash, but I allready remove all .Trash and .trash-1000 folders on EVERY partition! But it is still there.

---

