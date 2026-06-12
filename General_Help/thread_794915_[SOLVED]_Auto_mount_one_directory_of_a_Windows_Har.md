---
title: "[SOLVED] Auto mount one directory of a Windows Hard drive"
date: 2008-05-15
forum: General Help
---

### Post by hosammy on 2008-05-15
I am using Hardy 8.04 LTS & Windows XP which they are installed with different hard drives and use grub to select the bootup.
I have referred to [http://psychocats.net/ubuntu/mountwindows](http://psychocats.net/ubuntu/mountwindows) to mount the Windows hard drive which can be read & write in Ubuntu now.
My question is, now if I want to access my Windows document folder, I need to click many times to click into the right folder/directory. I have now create a /WinDocs folder in Ubuntu and I want to know how to auto mount my Windows Documents' directory to /WinDocs in Ubuntu, my Windows document directory is:
/windows/Documents and Settings/user/My Documents

:confused:

---

### Post by mattress on 2008-05-15
It's probably easiest to create a symlink to the directory.

```

ln -s /windows/Documents\ and\ Settings/user/My\ Documents /WinDocs

```

The back slashes are there on purpose...

m

---

### Post by hosammy on 2008-05-15
> **mattress said:**
> It's probably easiest to create a symlink to the directory.

```

ln -s /windows/Documents\ and\ Settings/user/My\ Documents /WinDocs

```

The back slashes are there on purpose...

m

Thanks very much, it's easy ...
Problem solved.

---

### Post by ubuscout on 2008-05-15
maybe another way could be load at login a script with a command... something like this 
"mount --bind /windows/Documents and Settings/user/My Documents /windocs" 

but I think u must before insert option "user" in fstab line where u mount your windows disk...  (mount only root can do it, so u can load the script without password...)

---

### Post by hosammy on 2008-05-15
> **ubuscout said:**
> maybe another way could be load at login a script with a command... something like this 
"mount --bind /windows/Documents and Settings/user/My Documents /windocs" 

but I think u must before insert option "user" in fstab line where u mount your windows disk...  (mount only root can do it, so u can load the script without password...)
It's a good idea too, but where can I place this command when I login the Ubuntu so that this command can autorun? Also, do I need to add the back slashes between the space?

:confused:

---

### Post by ubuscout on 2008-05-15
I remember this post, it could help you in this way...

[http://ubuntuforums.org/showthread.php?p=3768173#post3768173](http://ubuntuforums.org/showthread.php?p=3768173#post3768173)

---

### Post by bodhi.zazen on 2008-05-15
Add an entry in fstab, at the end or under the line for your window partition :

```
# Mount --bind My Documents to WinDocs[FONT=monospace]
[/FONT]/windows/Documents\ and\ Settings/user/My\ Documents  /WinDocs   none   bind
```

---

### Post by hosammy on 2008-05-16
> **bodhi.zazen said:**
> Add an entry in fstab, at the end or under the line for your window partition :

```
# Mount --bind My Documents to WinDocs[FONT=monospace]
[/FONT]/windows/Documents\ and\ Settings/user/My\ Documents  /WinDocs   none   bind
```

Thank you, I have tried to add the above two lines but it seems not work, is it any mistake in the command?

:confused:

---

### Post by bodhi.zazen on 2008-05-16
I do not see one.

What happens when you :

```
sudo umount /WinDocs
sudo mount /WinDocs

ls /WinDocs
```

Any error message ?

---

### Post by hosammy on 2008-05-19
> **bodhi.zazen said:**
> I do not see one.

What happens when you :

```
sudo umount /WinDocs
sudo mount /WinDocs

ls /WinDocs
```

Any error message ?

Since /WinDocs has been used by the sybolic link, the "ln" command, in previous thread. I make another folder, namely, /home/sammy/DocsWin for this test purpose.

I type: [COLOR="Blue"]sudo umount /home/sammy/DocsWin[/COLOR]
Response: [COLOR="Purple"]umount:  /home/sammy/DocsWin not yet mounted
[/COLOR]
I type: [COLOR="Blue"]sudo mount /home/sammy/DocsWin[/COLOR]
Response: [COLOR="Purple"][mntent]: line 24 in /etc/fstab is bad
mount: unable to find /home/sammy/DocsWin in /etc/fstab or /etc/mtab[/COLOR]

I type: [COLOR="Blue"]ls /home/sammy/DocsWin[/COLOR]
No error message or other response

line 24 in /etc/fstab is:
[COLOR="DarkRed"]/windows/Documents\ and\ Settings/user/My\ Documents  /home/sammy/DocsWin   none   bind[/COLOR]


:confused::popcorn:

---

### Post by ubuscout on 2008-05-19
...as said... I've tried that option, and for me it works fine.

But it seem the problem is manage the "space" in fstab line. I tried simulate in my fstab and without them I confirm it work. Probably it's only a syntax problem...

---

### Post by ubuscout on 2008-05-19
ok here we are... workaround I find this post

[http://ubuntuforums.org/showthread.php?t=763495&highlight=fstab+space+line](http://ubuntuforums.org/showthread.php?t=763495&highlight=fstab+space+line)

here u find the explanation on syntax in the end of post...

writing something like this

/mnt/windows\040with\040space /home/myuser/windocs none bind

...for me has work fine also with space...  ! ;-)

bye

---

### Post by bodhi.zazen on 2008-05-19
> **hosammy said:**
> Since /WinDocs has been used by the sybolic link, the "ln" command, in previous thread. I make another folder, namely, /home/sammy/DocsWin for this test purpose.

I type: [COLOR=Blue]sudo umount /home/sammy/DocsWin[/COLOR]
Response: [COLOR=Purple]umount:  /home/sammy/DocsWin not yet mounted[/COLOR]

No problem here.

> I type: [COLOR=Blue]sudo mount /home/sammy/DocsWin[/COLOR]
Response: [COLOR=Purple][mntent]: line 24 in /etc/fstab is bad
mount: unable to find /home/sammy/DocsWin in /etc/fstab or /etc/mtab[/COLOR]

I type: [COLOR=Blue]ls /home/sammy/DocsWin[/COLOR]
No error message or other response

line 24 in /etc/fstab is:
[COLOR=DarkRed]/windows/Documents\ and\ Settings/user/My\ Documents  /home/sammy/DocsWin   none   bind[/COLOR]


:confused::popcorn:My guess is you need to change "user" to your actual windows user name

[COLOR=DarkRed]/windows/Documents\ and\ Settings/**user**/My\ Documents  /home/sammy/DocsWin   none   bind[/COLOR]

Otherwise is the path correct ? is it /windows .... or /media/windows ....

---

### Post by hosammy on 2008-05-20
> **bodhi.zazen said:**
> No problem here.

My guess is you need to change "user" to your actual windows user name

[COLOR=DarkRed]/windows/Documents\ and\ Settings/**user**/My\ Documents  /home/sammy/DocsWin   none   bind[/COLOR]

Otherwise is the path correct ? is it /windows .... or /media/windows ....

The actual line 24 in /etc/fstab is:
[COLOR="Blue"]/windows/Documents\ and\ Settings/sammy.SAMMYHO/My\ Documents  /home/sammy/DocsWin   none   bind[/COLOR]

Here the **user** is [COLOR="Blue"]sammy.SAMMYHO
[/COLOR]

I have used the NTFS support and view the Windows file in nautilus, the path is:
[COLOR="Blue"]/windows/Documents and Settings/Sammy.SAMMYHO/My Documents[/COLOR]

the ln symbolic link works but your option seems still have problem.

:confused::guitar:

---

### Post by Jose Catre-Vandis on 2008-05-20
I have tried this under Gutsy, but will only work if the "040"s are included, so for you sammyho, should look like:
```
/windows/Documents\040and\040Settings/sammy.SAMMYHO/My\040Documents none bind
```

But check how your Windows partition is mounted, normally in /media so you would need to add /media to the beginning of your command in fstab, like so:
```
/media/windows/Documents\040and\040Settings/sammy.SAMMYHO/My\040Documents none bind
```

My XP is mounted in /media/XP-Real so mine lloks like this:

```
/media/XP-Real/Documents\040and\040Settings/jose/My\040Documents none bind
```

---

### Post by hosammy on 2008-05-20
At line 24 of /etc/fstab:
/windows/Documents\040and\040Settings/sammy.SAMMYHO/My\040Documents  /home/sammy/DocsWin   none   bind
Reboot, then, type: sudo mount /home/sammy/DocsWin
Response: mount: special equipment /windows/Documents and Settings/sammy.SAMMYHO/My Documents does not exist

Rewrite line 24 of /etc/fstab:
/media/windows/Documents\040and\040Settings/sammy.SAMMYHO/My\040Documents
Reboot, then type: sudo mount /home/sammy/DocsWin
Response:
mount: special equipment /media/windows/Documents and Settings/sammy.SAMMYHO/My Documents does not exist

---

### Post by hosammy on 2008-05-20
I do it again in /etc/fstab line 24
I copy the path at nautilus, and paste at the line 24, then manually type \040 & delete the space. It works fine now. 
Now my line 24 in /etc/fstab is:
/windows/Documents\040and\040Settings/Sammy.SAMMYHO/My\040Documents  /home/sammy/DocsWin   none   bind

Problem really have alternative way to solve.

---

### Post by Jose Catre-Vandis on 2008-05-20
> /windows/Documents\040and\040Settings/sammy.SAMMYHO/My\040Documents /home/sammy/DocsWin none bind

> /windows/Documents\040and\040Settings/Sammy.SAMMYHO/My\040Documents /home/sammy/DocsWin none bind

You spotted your problem, eh?  **S**ammy not **s**ammy :)

If you want to test this in the future, you don't need to reboot, just type
```
sudo mount -a
``` at a command prompt.

And now it's in your fstab, it should come up automatically in your home directory after boot, so no need to manually mount it any more :)

---

### Post by hosammy on 2008-05-20
> **hosammy said:**
> Thanks very much, it's easy ...
Problem solved.

May I know how do I cancel the created symbolic link "ln -s" at #3 now since I don't want too much folders containing the same things in my directory.

:guitar::popcorn::lolflag:

---

### Post by ubuscout on 2008-05-21
...for your purpose  remember that command "mount -a", let u mount without reboot as explaned u above, but execute the lines in fstab not containing the option "noauto"...

...well done ;-)

---

### Post by bodhi.zazen on 2008-05-21
> **hosammy said:**
> May I know how do I cancel the created symbolic link "ln -s" at #3 now since I don't want too much folders containing the same things in my directory.

:guitar::popcorn::lolflag:

use the command unlink

unlink /path/to/link

---

### Post by hosammy on 2008-05-22
> **bodhi.zazen said:**
> use the command unlink

unlink /path/to/link

I use the following:
sammy@sammy-desktop:~$ [COLOR="Blue"]unlink /windows/Documents\ and\ Settings/Sammy.SAMMYHO/My\ Documents [/COLOR]
[COLOR="Purple"]unlink: unable to remove the “/windows/Documents and Settings/Sammy.SAMMYHO/My Documents” link: it is a directory
[/COLOR]

Please advise ...:confused:

---

### Post by Jose Catre-Vandis on 2008-05-24
You need to unlink the actual symlink not the original path to the link.

So to create the link you would use
```
ln -s  /windows/Documents\ and\ Settings/Sammy.SAMMYHO/My\ Documents ~/WinDocs
``` and to unlink you would use```
unlink ~/WinDocs
```

---

### Post by hosammy on 2008-05-26
> **Jose Catre-Vandis said:**
> You need to unlink the actual symlink not the original path to the link.

So to create the link you would use
```
ln -s  /windows/Documents\ and\ Settings/Sammy.SAMMYHO/My\ Documents ~/WinDocs
``` and to unlink you would use```
unlink ~/WinDocs
```
I type:

sammy@sammy-desktop:~$ [COLOR="Blue"]sudo unlink /WinDocs
unlink: unable to cancel the link of “/WinDocs” : it is a directory
[/COLOR]

:confused:

---

