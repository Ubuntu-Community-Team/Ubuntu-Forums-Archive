---
title: "Create shortcut to folder in Lubuntu"
date: 2014-02-01
forum: General Help
---

### Post by Hvidemose on 2014-02-01
How can i create a shortcut for a folder (NOT TO DESKTOP)? Im using Lubuntu, and when i right clik on the folder, I dont get a "create link" option.

---

### Post by nerdtron on 2014-02-01
Open the terminal and let's create a symbolic link (shortcut)
```
 ln -s /path/to/target/folder /path/name/of/shortcut 
```

---

### Post by Hvidemose on 2014-02-02
Thanks mate, but unfortunately it only creates one or to unusable files there. Is there a way, to create a normal shortcut folder?

---

### Post by Bucky Ball on 2014-02-02
> **Hvidemose said:**
> Thanks mate, but unfortunately it only creates one or to unusable files there. Is there a way, to create a normal shortcut folder?

Then you're doing something wrong. That will create a symlink to your folder. When you click it you should be seeing the contents of the folder you've symlinked to. If you're not, then the command was incorrect. :-k

Say you want to link to /media/underpants. Then you would:

```
sudo ln -s /media/underpants /home/user/underpants

```
That will create a symlink to the folder 'underpants', which is mounted in media, in your /home/user directory. Call the symlink what you like.

---

### Post by Hvidemose on 2014-02-02
Yeah, obviously I'm doing something wrong.
I'm writing this, with this response:
```
:~$ sudo ln -s /media/diacska/CE04DC1404DBFE01/Documents and Settings/Hum/My Documents /home/diacska
ln: failed to create symbolic link ‘/home/diacska/Documents’: File exists
ln: failed to create symbolic link ‘/home/diacska/Documents’: File exists
```

And the it creates two files, that cant be opend. Their are called "and" and "my".
What am I doing wrong?

---

### Post by Impavidus on 2014-02-02
You have to escape the spaces or enclose the arguments in quotes:```
sudo ln -s "/media/diacska/CE04DC1404DBFE01/Documents and Settings/Hum/My Documents" /home/diacska/linkname
```
Besides, better not to use sudo here.

---

### Post by Hvidemose on 2014-02-02
thanks mate. So now I have a "symbolic link", but how do i open it?

---

### Post by stinkeye on 2014-02-02
You can do this graphically the same as you would in nautilus.
Open 2 pcmanfm windows and while holding down ctrl+shift drag and drop the folder you want to link to into the location you want the link to appear.
You should see a little chain link icon while dragging.

---

### Post by Hvidemose on 2014-02-03
> You can do this graphically the same as you would in nautilus.
Open 2 pcmanfm windows and while holding down ctrl+shift drag and drop  the folder you want to link to into the location you want the link to  appear.
You should see a little chain link icon while dragging.

But this seems like its copying the files?
Isn't there a way to open the symbolic link, or make a traditional folder shortcut?

---

### Post by Bucky Ball on 2014-02-03
I don't quite understand this:

```
/media/diacska/CE04DC1404DBFE01/Documents and Settings/Hum/My Documents /home/diacska
```

If you want to create a symlink 'Documents' in /home/diacska linking to the existing /media/diacska/CE04DC1404DBFE01/Documents directory you would have:

```
ln -s /media/diacska/CE04DC1404DBFE01/Documents /home/diacska/Documents
```

You need to delete the directory /home/diacska/Documents before this if one exists.

---

### Post by stinkeye on 2014-02-03
**@Bucky Ball**...it appears to be a link to **My Documents** on a windows partition.


> **Hvidemose said:**
> But this seems like its copying the files?
Isn't there a way to open the symbolic link, or make a traditional folder shortcut?
Works for me to create a link to **My Documents** on my xp partition.
When drag and dropping release the mouse then release ctrl+shift.
Are you seeing the link icon while dragging?

Notice the size of the symlink....0 bytes  
and the symlink has an arrow icon.

---

### Post by Hvidemose on 2014-02-03
> **Bucky Ball said:**
> I don't quite understand this:

```
/media/diacska/CE04DC1404DBFE01/Documents and Settings/Hum/My Documents /home/diacska
```

If you want to create a symlink 'Documents' in /home/diacska linking to the existing /media/diacska/CE04DC1404DBFE01/Documents directory you would have:

```
ln -s /media/diacska/CE04DC1404DBFE01/Documents /home/diacska/Documents
```

You need to delete the directory /home/diacska/Documents before this if one exists.

Ok, this actually created something that looks like a folder shortcut, but when I double click on it (open with PCManFm) nothing happens... Any idea why? The partition is mounted.

---

### Post by stinkeye on 2014-02-03
I believe the directory your trying to link is **/media/diacska/CE04DC1404DBFE01/Documents and Settings/Hum/My Documents**

so....
```
ln -s "/media/diacska/CE04DC1404DBFE01/Documents and Settings/Hum/My Documents" "/home/diacska/My Documents"
```

---

### Post by Hvidemose on 2014-02-03
Ok, but no matter what I try, I cant open the folders/files I create. I also tried other file managers...
Any idea why?

---

### Post by stinkeye on 2014-02-03
> **Hvidemose said:**
> Ok, but no matter what I try, I cant open the folders/files I create. I also tried other file managers...
Any idea why?
As a test create  a shortcut to your Downloads folder on your Desktop
```
ln -s ~/Downloads ~/Desktop/Downloads
``` 

Can you open that link?

Is your windows partition mounted?
How do you mount your windows partition?

---

### Post by Bucky Ball on 2014-02-03
File manager should make no difference. I use PCmanFM and no issue.

---

### Post by Dennis N on 2014-02-03
> **Hvidemose said:**
> Ok, but no matter what I try, I cant open the folders/files I create. I also tried other file managers...
Any idea why?

Link may be broken. A way to check the link for validity (possible broken link):

In the terminal, cd to the folder containing the link you created.

type the command [FONT=Courier New]**ls -l**[/FONT]

find the link in the listing, and check the target (the part after the arrow). If the target or path is not correct, the link and target are usually color coded (red in my xfce4 terminal) to show the link is _broken_. I created link1 with target folder1 and link2 with target folder2. But folder2 doesn't exist.
```

good link:
**lrwxrwxrwx 1 dn dn    7 Feb  3 20:16 [COLOR="#00FFFF"]link1[/COLOR] -> [COLOR="#4B0082"]folder1[/COLOR]**
broken link:
**lrwxrwxrwx 1 dn dn    7 Feb  3 20:20 [COLOR="#FF0000"]link2[/COLOR] -> [COLOR="#FF0000"]folder2[/COLOR]
```**folder1 does exist - good link. folder2 did not exist - a broken link.

---

### Post by Hvidemose on 2014-02-04
> **stinkeye said:**
> As a test create  a shortcut to your Downloads folder on your Desktop
```
ln -s ~/Downloads ~/Desktop/Downloads
``` 

Can you open that link?

Is your windows partition mounted?
How do you mount your windows partition?

This link can be created and accessed without problems, so it seems like the problem has to do with the link between the two partitions...
I can access the other partition with a simple click in the file manager. The XP partition is mounted on startup, so there shouldn’t be any problem there... - or???

---

### Post by Bucky Ball on 2014-02-04
No, there shouldn't be. I thought of this before and not sure if I mentioned it ... just wondering if the spaces in the symlink are causing a problem? Stab in the dark, but we're getting to that point. As in:

/Documents and Settings/

Just a thought. Not sure whether spaces are permitted with symlinks.


* My stab was on target at this end. When I create the folder 'hello dolly' and create a symlink to it I get *two* ***files***, not folders, that are still called symbolic links with the correct target, but one is called 'hello' and one is called 'dolly'.

When I rename the folder to 'hello_dolly', not an issue; I get _one_ symlinked folder icon, all present and correct.

I couldn't find anything about this online so just thought, why not try it myself! Doh! :-k

Just wondering; do your failed links look like files but the one that worked is a *folder* with and arrow?

---

### Post by stinkeye on 2014-02-04
**@Bucky Ball**

I can create a link to **My Documents** on my XP partition with
```
ln -s "/media/glen/XP/Documents and Settings/glen/My Documents" "/home/glen/My Documents"
```

Can also create using drag and drop with ctrl+shift.
I mounted the XP partition by just clicking on the entry in the left pane of the file manager.
Feel the issue may be the way **Hvidemose** automounts the partition in fstab.

---

### Post by Bucky Ball on 2014-02-04
Hmm. Perhaps you're right about the mounting. Odd I can't make one. But then, I am not doing from an NTFS disk. Perhaps that's my issue. I'll give it a go with one later.

 Hvidemose, could you do this and post the file, please:

```
nano /etc/fstab
```

---

### Post by Hvidemose on 2014-02-04
> I thought of this before and not sure if I mentioned it ... just wondering if the spaces in the symlink are causing a problem?

Well for me it didnt make any difference... But thanks.

> **stinkeye said:**
> **@Bucky Ball**

I can create a link to **My Documents** on my XP partition with
```
ln -s "/media/glen/XP/Documents and Settings/glen/My Documents" "/home/glen/My Documents"
```

Can also create using drag and drop with ctrl+shift.
I mounted the XP partition by just clicking on the entry in the left pane of the file manager.
Feel the issue may be the way **Hvidemose** automounts the partition in fstab.

I tried both ways to mount, but no difference... its really strange...

---

### Post by stinkeye on 2014-02-04
Can you navigate to My Documents in pcmanfm and set it as a bookmark?

Came across this in a post....
> I suspect you're trying to look inside the equivalent of "C:\Documents and Settings\$YourUser", but it's only a symlink in Windows 7 and Vista. Your documents are really located in C:\Users\$YourUser\Documents.

I only have XP so can't test.
Maybe have a look in  **/media/diacska/CE04DC1404DBFE01/Users/Hum/Documents** and see if  that contains your files and if so try and symlink that directory.

---

### Post by Hvidemose on 2014-02-06
> **Bucky Ball said:**
> Hmm. Perhaps you're right about the mounting. Odd I can't make one. But then, I am not doing from an NTFS disk. Perhaps that's my issue. I'll give it a go with one later.

 Hvidemose, could you do this and post the file, please:

```
nano /etc/fstab
```

Could be the filesystem. The disk uses NTFS.
Yes of course :-)

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda6 during installation
UUID=5fc5562d-e8ee-4f28-ad81-a7c75b777539 /               ext4    errors=remoun$
# swap was on /dev/sda5 during installation
UUID=3bcf01d7-b9bf-4b0c-ba0f-4d18241d4cfe none            swap    sw           $
/dev/disk/by-uuid/CE04DC1404DBFE01 /mnt/CE04DC1404DBFE01 auto nosuid,nodev,nofa$

```

---

### Post by Bucky Ball on 2014-02-06
Just a point; I notice there are only EXT* partition in your fstab, no NTFS. How is the NTFS partition getting mounted? Silly question, but the NTFS partition is mounted when you are attempting to make the symlink? If not, no go ... :-k

---

### Post by shaquille on 2014-09-21
> **nerdtron said:**
> Open the terminal and let's create a symbolic link (shortcut)
```
 ln -s /path/to/target/folder /path/name/of/shortcut 
```

Thanks. Works for me fine. :)

---

