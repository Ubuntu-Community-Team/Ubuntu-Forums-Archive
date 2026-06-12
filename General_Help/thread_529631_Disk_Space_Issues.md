---
title: "Disk Space Issues"
date: 2007-08-19
forum: General Help
---

### Post by themusicwave on 2007-08-19
I gave been having a pretty annoying problem lately.

I recently maxed out my Ubuntu Partition, causing gnome to no longer load.

So I figured big deal I can just use Crt-alt F2 and delete some stuff.

So I deleted a few hundred MB of files, and went to empty the .Trash folder, funny thing is there was nothing in these if if I did ls -a

So out of suspicion I did a df and saw I was still at 100% usage.  I deleted more files and the same thing is happening.  The disk space never frees, but the files are gone.  I have no idea what is going on here.

I have thought about just reinstalling Ubuntu, but that seems a bit extreme.  I also looked in the tmp folder, it's totally empty as well.

So my questions are:

1) What is happening to my disk space
2) How do I get it back
3) How much space does Gnome need to load

Thanks,
Jon

---

### Post by gobbles414 on 2007-08-19
Howdy themusicwave,

What directory are you using for the trash? Here is how I move files to the trash:

sudo mv FILENAME /home/USERNAME/.Trash

Here is how I empty the trash:

sudo rm -rf ~/.Trash/*

Please let me know if this helps.

---

### Post by themusicwave on 2007-08-19
I have no idea what directory I am using as the Trash.  I am just using rm to delete things

for example:
sudo rm fileName

or sudo rm -r directory

I assumed this just either erased the file or sent it to .Trash.

The trash folder is am checking is home/username/.Trash and it is empty.  Where else would Ubuntu dump my erased files.  

This is driving me nutz, I have to use Windows now because of this....

---

### Post by gobbles414 on 2007-08-19
Hi themusicwave,

I've never had to use the rm command myself, but I don't think that the rm command will delete directories. It will only delete files by default. Also, I made one little error with the trash directory. Assuming that you want to delete a folder called STUFF from your desktop to the trash, and your username is AIRPLANE, you would type.

sudo mv /home/AIRPLANE/Desktop/STUFF /home/AIRPLANE/.Trash

Notice the space between STUFF and the /. Then you would execute the following command:

sudo rm -rf ~/.Trash/*

---

### Post by themusicwave on 2007-08-19
rm -r made the directories disappear, so either they are erased or does Ubuntu just thinks they are?

From what I have read rm -r is a recursive delete that basically removes everything in a directory and then the directory itself.  At least thats what I tink they were saying....

All the directories I used the command on are gone.  So it did something.

Also, in your example you say to use the rm -rf command which is a recursive delete with the force option.

Could it be that I used rm wrong and somehow th files are sill there?  That might explain the disk space not freeing up. 

Now the only problem is how do I now if they are still there and how do I delete them if they are?  Quite a predicament...

Thanks for the info so far

---

### Post by HermanAB on 2007-08-19
A reboot should sort out the file system and the missing space should come back.

Cheers,

Herman

---

### Post by themusicwave on 2007-08-19
Even after a reboot the files are still gone.

Interestingly, if I run a df before and after I delete something the results change.  Here is what happens:

Used decreases by that file's size as expected
Available remains 0 every time
Usage remains at 100%


So basically the space is no used, but is also not available.  So what is it then??  This is all very confusing to me, thank you both for continuing to help me sort it out.

Any ideas?

---

### Post by gmaniac on 2007-08-19
rm command doesn't have the courtesy to hold anything back for a second thought ;), so you probably deleted them but maybe you have deleted small files and you have a big drive.

Use the force ```
 du -h | sort -n -r | head -10
``` 

( this will show you the 10 most space hungry files you have in the current directory and all it's subdirectories).
Try it on you home folder.. see there what you can delete
Try it  on your root folder BUT BE CAREFULL WHAT YOU DELETE !!!
Don't over do it :)

---

### Post by themusicwave on 2007-08-19
I'll go reboot and give it a shot.  Until then can someone explain what the columns in df mean?

I thought that total - used = available, but it isn't adding up

Right now I have a 50000 byte difference between the total and the used space.  However I still have 0 bte of available space.  Weird....50mb should be enough for gnome to load shouldn't it?

I still can't get gnome to load as I still have 0 bytes available.

Thanks again for the help!

---

### Post by gobbles414 on 2007-08-19
Hi all,

All of the info I have posted in this thread I borrowed from various pages on the web. I didn't even notice that I was using the rm command to empty the trash until themusicwave mentioned it!

Anyway, would it be possible to use a LiveCD to delete some more files?

---

### Post by gmaniac on 2007-08-19
You could clean old packages that are left from upgrades
```
sudo aptitude autoclean
```
you could use clean instead of autoclean for all cached packages.

Another thought is removing large packages you have and don't need
use ```
sudo aptitude
``` for a graphical menu.

---

### Post by themusicwave on 2007-08-22
Well I did end up deleting some bigger files.  However one of them was apparently rather inmportant to gnome.

So I backed up my data and reinstalled, problem solved!

Thanks for all the help guys!

---

### Post by trishacupra on 2007-09-12
Hi. I found my thumbnails folder (hidden in your home folder) is what grows too big for my hard drive. Try cleaning that out.

---

