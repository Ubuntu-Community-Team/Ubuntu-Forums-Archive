---
title: "Linux Virus?"
date: 2008-04-01
forum: General Help
---

### Post by kender42 on 2008-04-01
I'm having a problem with FF and Ubuntu in general as well. I started Firefox this morning and I got a "Unresponsive Script" error in FF. My home page is set to blank. After I clicked the stop script button FF closed out completely and then Ubuntu popped up an error of "You are using 99% of your / drive" but when I checked the stats I have a 35.5GB drive and then I start watching the free space diminish as I watch it. When I started this post I had 2.3 GB free now I have 68mb.

---

### Post by Patness on 2008-04-01
Can you tell us more? What kind of machine are you using (desktop, laptop, etc)? What processor, how much RAM, etc. We've got the hard disk size, so you don't need to contribute that.

It's a very strange problem.

---

### Post by girto on 2008-04-01
Or maybe a Firefox April fool's add-on is at work? :)
Check in Firefox Tools/Add-ons for any strange installed add-ons.

---

### Post by misterhead on 2008-04-01
Yeah, What's the specs? How fresh is the install, and what was done since then? (updates, extra packages)

---

### Post by kender42 on 2008-04-01
I am running a laptop. Toshiba Satellite P4. I dont know how much ram there is on it, and I dont know how to even find out. I am also running Ubuntu 7.10 gutsy with the most recent updates.

---

### Post by kender42 on 2008-04-01
There arent any strange addons installed. I've cleaned up all old packages that were unneeded, I have emptied my trash. The more I try to uninstall the less space I have.

---

### Post by ibuclaw on 2008-04-01
checked the "**.Trash**" folders in your **/home** directory?

This is what I found...

```

~/$ cd /home
/home$ ls -a
.Trash-0  .Trash-root
/home$ du -sh .Trash-0
3.9G	.Trash-0

```

3.9 GB!?!
I can't access it... And I don't have a user named "**0**" either....

hmm...

I think I might invoke root and remove it!

Regards

[EDIT]
As I posted in the other thread:
[B] o Reboot your PC. Stops any running scripts
 o Remove the ".mozilla" folder in your home directory. Next time you start Firefox will be on a clean sled.[/B]

---

### Post by kender42 on 2008-04-01
I am checking /home folder and it says that I have a new folder in my home folder called No name

When I click on it I get:

Couldn't open "/home/.directory"
This location is not a folder

Is this supposed to be there? 

And now FF wont start after I reinstalled it.

My free disk space is now down to 48k and its dropping fast.

I am now rebooting to see if this fixes the problem.

---

### Post by ibuclaw on 2008-04-01
To find out the size of the files/folders in your home directories:

Try pasting this into a text file:
```

#!/bin/bash

for i in *; do
        du -sh "$i"
done

for j in .*; do
        du -sh "$j"
done

```

save it as **fsize.sh** for example, and mark it executable.
```
 chmod +x fsize.sh 
```
Then to execute it use the command:
```
 ./fsize.sh | less 
```
Then use the up and down arrow keys to browse through the printed list and take note of anything that has a **M** or a **G** after its size.
ie:
```
832M    Music
29M     Pictures
806M    Public
32G     .VirtualBox
```

If the sizes seem suspicious, check them out, and if there is something there that clearly shouldn't, then remove it.

IF you are unsure, **ask us** first!

Also, ignore these folder names:
```

[B]37.7G    .
37.7G    ..[/B]

```
They just display the size of the entire home directory.

Regards
Iain

---

### Post by kender42 on 2008-04-01
> **tinivole said:**
> To find out the size of the files/folders in your home directories:

Try pasting this into a text file:
```

#!/bin/bash

for i in *; do
        du -sh "$i"
done

for j in .*; do
        du -sh "$j"
done

```

save it as **fsize.sh** for example, and mark it executable.
```
 chmod +x fsize.sh 
```
Then to execute it use the command:
```
 ./fsize.sh | less 
```
Then use the up and down arrow keys to browse through the printed list and take note of anything that has a **M** or a **G** after its size.
ie:
```
832M    Music
29M     Pictures
806M    Public
32G     .VirtualBox
```

If the sizes seem suspicious, check them out, and if there is something there that clearly shouldn't, then remove it.

IF you are unsure, **ask us** first!

Also, ignore these folder names:
```

[B]37.7G    .
37.7G    ..[/B]

```
They just display the size of the entire home directory.

Regards
Iain

The reboot solved the FF issue, but not the drive space problem. Yesterday I had 50% of my drive space empty.

I dont have enough disk space to save that file.

According to the disk usage analyzer the folder /home/[user]/.cache/tracker is taking up 100% of my drive. as well as / is also taking up 100%

---

### Post by ibuclaw on 2008-04-01
Then I seriously suggest you boot from the gutsy LiveCD.

And fix the problem externally.

Regards
Iain

---

### Post by prshah on 2008-04-01
> **kender42 said:**
> I am running a laptop. Toshiba Satellite P4. I dont know how much ram there is on it, and I dont know how to even find out. I am also running Ubuntu 7.10 gutsy with the most recent updates.

"free" will give your current RAM usage; "df" will give your current disk usage summary.

"top" will list the currently active programs in your computer, sorted in order of CPU usage.

Details from all three commands will go a long way in figuring this out.

If this is an AFD joke, then there is a reformatter virus attached to this message.

---

### Post by ibuclaw on 2008-04-01
> **kender42 said:**
> According to the disk usage analyzer the folder /home/[user]/.cache/tracker is taking up 100% of my drive. as well as / is also taking up 100%

```
 killall trackerd 
```

Then remove the folder.

If it is taking up all of your filesystem, then I am right to assume that you don't have a separate home partition. (ie / and /home share the same space)
So this makes sense that 100% of your space may be taken up.

And I agree with prshah, if this is a joke, this isn't funny.

I'm probably right in saying that nobody here has experienced this sort of behavior from Linux in the past, and we'll all agree that drive space isn't easily consumed by programs, given that you got them from reliable sources. (ie: the Ubuntu Repository).

---

### Post by kender42 on 2008-04-01
> **tinivole said:**
> ```
 killall tracker 
```

Then remove the folder.

I tried that and I got:

tracker: no process killed

After removing the folder the disk usage analyzer now says that I have 1.8 gigs free. I tried to save a text file that says "hello world" and it wouldnt let me save it. I got the message that told me I have no disk space available.

I did get all of my packages from the Ubuntu repository, so I am really confused as to why and how this happened.

(edit)
file browser says that I only have 20k space left while the disk usage analyzer says that I have 2.3 gigs now. And I still cant save anything.

---

### Post by ibuclaw on 2008-04-01
Boot from your Gutsy Live CD and remove all hidden folders in your home partition.

While in the live environment, your file system will be mounted to:
```
 /media/**sd[$#]**/home/**[username]**
Where $# is your drive **Letter** and partition **Number**.
username being your **Username**. Of course...

In Nautilus, enter this directory and hit **Ctrl+H**

Remove all files and folders beginning with a **"."** dot.

ie:
[CODE]
**.**mozilla
**.**bashrc
**.**etc

```

Then go up and into the root folder ( **/media/sd$#/root** ) and copy all **"."** dot files and folders from there into your home account directory.

Then chown everything to your username

Open up a terminal, find your way to " **/media/sd$#/home/**", and enter this:
```

chown **[username]**:**[username]** **[username]** -R

```

That will fix everything, will the side effect of resetting your entire account back to factory settings. (ie Wallpaper, Compiz)

If you have anything to backup, **back it up**! (Music, Pictures, Documents + Public Folders, etc)

Sorry, but it may be the only way.

Regards
Iain

---

### Post by kender42 on 2008-04-01
I tried to backup my system both with gnome baker and also brasero but I got an error that my dvd burner doesn't have write permissions.

I tried to change the permissions to read/write but it says I don't have permissions to do that so I entered my admin pass and was told that my password is invalid.

What do I do now. I can't back anything up

I'm afraid I'll have to reinstall and lose everything

---

### Post by kender42 on 2008-04-01
Problem solved

Found a tar.gz file that was downloaded yesterday. It had the name "--" It wouldnt open when I tried to look at what was in the file. ARK said it was not an archive. I dont know what was in it, but I deleted it and now I have 29 gigs free. 

Thank you all for your help. I would have had to reinstall without you. I love the opensource/linux community!

---

### Post by kender42 on 2008-04-01
Just for knowledge sake, does anyone have any theories of what it could have been (a corrupt file, deranged script, etc) and how I might take care of things in the future so I don't have to go through damage control.

---

### Post by ibuclaw on 2008-04-02
Yeah, don't download anything from untrusted sites...

:lolflag:

Regards
Iain

[QUOTE=http://linuxreviews.org/software/p2p/]
Linux users who are hopelessly inexperienced with computers and life in general, unquallified to use a Linux system and stupid enough to run programs with unknown origin are also exposed to viruses, worms and other evil.
[/QUOTE]

---

