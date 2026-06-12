---
title: "Stuck in Trash Can"
date: 2008-06-01
forum: General Help
---

### Post by mpgarate on 2008-06-01
I have two files in my trash bin which will not delete. i think they may be owned by root, but our in my trash can and not the root trash can. How would I go about removing them?

---

### Post by Bubba64 on 2008-06-01
> **mpgarate said:**
> I have two files in my trash bin which will not delete. i think they may be owned by root, but our in my trash can and not the root trash can. How would I go about removing them?

High light them hold down shift and hit delete on the keyboard.

---

### Post by mpgarate on 2008-06-01
I mean deleteing them from the trash can. Doing shift+delete gives me the same error

Error While Deleting, error removing file, permission denied

---

### Post by andrew.46 on 2008-06-01
Hi,

'Trash' files can usually be seen in: $HOME/.local/share/Trash/files and if you cannot delete them try:

```
$ cd $HOME/.local/share/Trash/files
$ ls -l
```

The -l option will show the owners of the files and their permissions and this will show why you are having trouble deleting them as an ordinary user. If you wish you can then *cautiously* delete each file individually with the command:

```
$ sudo rm filename
```

Directories can also be deleted from 'Trash' in this way but the command 'rm -rf filename' is one that need to be used with caution and precision.

          Andrew

---

### Post by mpgarate on 2008-06-01
ahhh that did it thank you!

---

### Post by WhiteStorm on 2008-06-03
Hmm... I am having this same problem. I downloaded a trial of photoshop cs2 to see if it would run in wine, and it didn't install after I unzipped it, so I deleted the folder. When I later emptied the garbage bin, a lot of the files (from the unzipped folder only) remain there and trying to delete them gives the message "there was an error deleting (filename)". It says this for all the ones remaining there.

I tried entering the code in this thread but I must do it wrong, for it says the folders are there but when told to delete them, it reads the name "Photoshop CS2" as two names and says they don't exist. Even though I copied this name from it when it said what was in there. Trying with an underscore instead of space it still says it doesn't exist.

Is there a way to make it read the space? Or did I do the wrong thing altogether?

---

### Post by ChameleonDave on 2008-06-03
> **WhiteStorm said:**
> Hit reads the name "Photoshop CS2" as two names and says they don't exist. Even though I copied this name from it when it said what was in there. Trying with an underscore instead of space it still says it doesn't exist.

Is there a way to make it read the space? Or did I do the wrong thing altogether?

Let's say you have a file located at "/home/fred/two words" that you want to delete.  There are two ways to do it.

```
rm "/home/fred/two words"
```

or

```
rm /home/fred/two\ words
```

---

### Post by ChameleonDave on 2008-06-03
> **andrew.46 said:**
> If you wish you can then *cautiously* delete each file individually

Except, since these are all files that you have decided to delete, there's no reason to be cautious.

```
sudo rm -fr ~/.local/share/Trash
```

That will totally zap your trashcan, no matter what.  I've never had ill effects from it.

To do the same for all users on the system, you'll have to enter the following:

```
sudo rm -fr /home/*/.local/share/Trash
sudo rm -fr /root/.local/share/Trash
```

Since I have a separate partition mounted at ~/Files, I have to do the following to completely get rid of all trashed files:

```
sudo rm -fr ~/Files/.Trash*
```

Just go on a deletion rampage!

---

### Post by WhiteStorm on 2008-06-03
Er... hmm...

I tried to do this, and it still says no such file or directory exists.

I thought, okay, I will look at it, and it seems it is true. I can go to local and share but there is no "Trash" there (even though it says in the terminal those files are there, like before). Also I ticked show hidden files when looking, just in case, and cannot see it.

EDIT: this was to the earlier post. The command "sudo rm -fr ~/.local/share/Trash" worked, thanks!

---

### Post by andrew.46 on 2008-06-03
Hi,

I see that your problem has been solved:

> **WhiteStorm said:**
> Is there a way to make it read the space? Or did I do the wrong thing altogether?

But there is another tool available to you for files with spaces in their names. As has been pointed out already by Chameleon Dave these spaces need to be escaped (that is have a "\" placed in front of the space) but this does not need to be done manually. Simply type in the first couple of characters and press the TAB key and the shell will fill it in for you, complete with all the escapes.

If it does not, or beeps at you, press TAB twice and it will show you that there are 2 or more files that start with the same few characters. Simply type a few more characters and press TAB again.

   Andrew

---

