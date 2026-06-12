---
title: "[SOLVED] Can't empty trash can due to files permissions"
date: 2008-05-14
forum: General Help
---

### Post by Tasc0 on 2008-05-14
I can't empty the trash can because I moved a folder with read-only permissions. I tried restoring the folder back to my desktop and I can't. I also tried modifying the permissions to create and delete, but it says it can't be done. This is the error I get:
> 	
The backend does not support the operation.


How can I fix this? Thanks in advance.

---

### Post by Thirtysixway on 2008-05-14
Use 
```

sudo rm -rf ~/.Trash/*

```

This will do the trick. :)

---

### Post by macaholic on 2008-05-14
> **Thirtysixway said:**
> Use 
```

sudo rm -rf ~/.Trash/*

```

This will do the trick. :)
Not if he is on hardy it won't. The trash directory is now in ~/.local/share.Trash/files
So the command would be ```

sudo rm -r ~/.local/share/Trash/files/

```

---

### Post by Tasc0 on 2008-05-14
Thanks for replying, but I read on this forum that I should not run any command containing "rm".

---

### Post by MaindotC on 2008-05-14
Yeah I reported both posts.

---

### Post by macaholic on 2008-05-14
> **strAlan said:**
> Yeah I reported both posts.
Reported them? I didn't realize he added the "f", and I fixed my post and now it is just "r", which isn't nearly as bad. And secondly theres nothing wrong with using the rm command itself, its just when people misuse it and delete their entire home directory.

Using the rm command is the easiest way to delete those files, unless you want to screw your GUI up and run gksu nautilus, navigate to the files and delete them that way.

---

### Post by MaindotC on 2008-05-14
I'm kidding - you guys didn't do anything wrong, just OP is newb and rightfully thinks you're trying to get him to do something to damage his system.  Let him figure it out.

---

### Post by macaholic on 2008-05-14
> **strAlan said:**
> I'm kidding - you guys didn't do anything wrong, just OP is newb and rightfully thinks you're trying to get him to do something to damage his system.  Let him figure it out.
Well him being a noob and all, you shouldn't make him think that everytime someone tells him to run a rm command that he is going to nuke his system, that's just not true. People believe things that you tell them more often then you would think. 

Also just for the record, NEVER run sudo rm -rf unless you know exactly what your about to delete. You can get 90% of your removing needs with just -r without the f.

---

### Post by MaindotC on 2008-05-14
I'll keep it to a PM next time.

---

### Post by Tasc0 on 2008-05-14
In what directory can I found the trash can and its files?

---

### Post by drs305 on 2008-05-14
> **Tasc0 said:**
> Thanks for replying, but I read on this forum that I should not run any command containing "rm".

Tasc0,

In answer to your last post, the trash files in hardy are in ~/.local/share/Trash/files/ (that is /home/username/.local/share/Trash/files)

It is good to be wary of commands you see on the Internet, although this group is the best I've ever seen on a forum.

The advice concerns using the rm (remove command) in combination with the root ( / ) directory, the -rf switches and sudo. The -rf tells the remove command to remove all subdirectories (and files) recursively, which means every subdirectory as well. So a 'rm -rf' is going to start at the current directory and delete everything from there on down. The / would start at the top of the root directory, the worst possible starting point, as it would wipe out all your system files. And using 'sudo' would give you, the ordinary user, the temporary power to do all those things.

The 'rm' command isn't evil, but there are just combinations you must avoid. As you did, if you ever have a question about a command, wait until you have confirmed it with other users.

---

### Post by MaindotC on 2008-05-14
Right here:

> **macaholic said:**
> Not if he is on hardy it won't. The trash directory is now in ~/.local/share.Trash/files


---

### Post by drs305 on 2008-05-14
Actually, there was a typo in an earlier post: it's ... share/Trash/files, not share.Trash/files

---

### Post by Tasc0 on 2008-05-14
> **drs305 said:**
> Tasc0,

In answer to your last post, the trash files in hardy are in ~/.local/share/Trash/files/ (that is /home/username/.local/share/Trash/files)

It is good to be wary of commands you see on the Internet, although this group is the best I've ever seen on a forum.

The advice concerns using the rm (remove command) in combination with the root ( / ) directory, the -rf switches and sudo. The -rf tells the remove command to remove all subdirectories (and files) recursively, which means every subdirectory as well. So a 'rm -rf' is going to start at the current directory and delete everything from there on down. The / would start at the top of the root directory, the worst possible starting point, as it would wipe out all your system files. And using 'sudo' would give you, the ordinary user, the temporary power to do all those things.

The 'rm' command isn't evil, but there are just combinations you must avoid. As you did, if you ever have a question about a command, wait until you have confirmed it with other users.
I can't navigate to that direction, right?

---

### Post by MaindotC on 2008-05-14
Right-click the folder and select "Show Hidden Files" or it will be in "View" in the menu bar.

---

### Post by drs305 on 2008-05-14
> **Tasc0 said:**
> I can't navigate to that direction, right?

Sure. In terminal:

```
rm -rf /home/yourusername/.local/share/Trash/files
```
or 

```
rm -rf ~/.local/share/Trash/files
```

If there is a file in the trash that is not owned by you, then first run this command:
```
sudo chown username -R /home/yourusername/.local/share/Trash
```
That command will change the ownership of all the trash in that file to you, so you can then delete it ;-)

---

### Post by MaindotC on 2008-05-14
Dude read his post above lol he's newb and he thinks that's gonna f up his system :)

---

### Post by ibuclaw on 2008-05-14
[QUOTE=strAlan]Dude read his post above lol he's newb and he thinks that's gonna f up his system[/QUOTE]
Yes, it is!

Here, is the newb friendly way...

Using the GUI equivalent of chown in a controlled environment!

Hit **Alt+F2** and copy and paste this instruction:
```
gksu nautilus ~/.local/share/Trash
```
Type in your password, and the Nautilus file browser should open in your Trash Location.

Right click on the "files" folder, and go into properties.
Select the "Permissions" tab make sure the "Owner" and "Group" dropboxes have your username in.

Then click "Apply Permissions to the Enclosed Files".

Close nautilus and you may now empty your trash-can.

[EDIT]
Why did no one ever think to say this before me?

Regards
Iain

---

### Post by Tasc0 on 2008-05-14
The thanked post in this thread solved the problem. Appreciated.

---

### Post by stankopp on 2008-05-15
The only way to see the .local directory (and its sub-directories) in your home directory is to view hidden files.  It is best to delete the files as suggested with the sudo rm -r command (as above the one without the -rf).  You can even cut and paste it into your open terminal.

---

