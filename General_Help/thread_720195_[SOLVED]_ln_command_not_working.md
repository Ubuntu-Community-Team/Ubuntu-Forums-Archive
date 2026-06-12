---
title: "[SOLVED] ln command not working"
date: 2008-03-10
forum: General Help
---

### Post by Samrat Rao on 2008-03-10
hello,
i am just learning linux. my 'ln' command is not working. i have 7.10 (32 bit version) installed in my desktop. the error message i get is 'operation not permitted'. even using with sudo does not help. the ln command works only when i am in my 'filesystem' and the link is to be done when the files are in the same folder. in other drives i cannot even do that. 'ln' works in my friend's desktop and he has the same version of ubuntu. pl help.:(
thanks in advance....

---

### Post by erginemr on 2008-03-10
OK, but please tell us what you exactly want to do (i.e. the very command that involves ln)...

---

### Post by Samrat Rao on 2008-03-10
well, i wish to create symbolic links like this:
ln -s filename linkname
i need to create a large number of symbolic links for compiling a complex programme.

even hard links are not getting created.

---

### Post by erginemr on 2008-03-10
No no, what I mean is for you to give an example, a specific file in a specific directory.

Anyway, please note that you had better use absolute paths (beginning with /) such as:
```
sudo ln -s /usr/local/share/target_file /usr/share/new_link
```

for both the target file and the new symbolic link for a proper linking across directories. sudo is necessary to get the root permissions to be able to write to the directory where you want to link the target file.

Secondly, note that unlike symbolic links, hard linking does not work across different partitions.

Finally, note that there should be no existing "new_link" file at the desired symbolic link location, otherwise it won't work. To make sure that any existing links are overwritten, you can force the linking with:
```
sudo ln -sf /usr/local/share/target_file /usr/share/new_link
```

---

### Post by frankos44 on 2008-03-10
I find it much easier to use a symbolic link to a folder eg.

$ ln -s /path/to/foldername ./myfolder

I say this because if your links are deleted or broken for some reason, it is easy to bring all the files in the linked folder back again in one hit, where as linking on an individual file by file basis is time-consuming and you may miss one when re-creating them.

Make sue you have permissions to access the folder you want to link to.

---

### Post by frankos44 on 2008-03-10
My post was being created while other posts were added thus I never got to see them until I clicked submit . Sorry for the duplication ... Wow this is an enthusiastic forum!!! lol

---

### Post by Samrat Rao on 2008-03-10
i'll try what you said.
i need to make symbolic links. i created a file 123.txt and in the same directory i typed:
ln -s 123.txt 1.txt. i get the message 'operation not permitted'. 1.txt does not exist previously. i tried on another machine and it works, but not in my desktop.
to be more specific, i am executing a file 'setup' (a C shell script) and this needs to create symbolic links to files in a directory 'common'. these symbolic links are to be placed in another directory in the same partition. the command used in the file setup is: ln -s ../common/* .     the file 'setup' works on other desktops.
i am using a bash shell but i have csh installed as well.
i hope i convey more this time....

---

### Post by frankos44 on 2008-03-10
> **Samrat Rao said:**
> i'll try what you said.
i need to make symbolic links. i created a file 123.txt and in the same directory i typed:
ln -s 123.txt 1.txt. i get the message 'operation not permitted'. 1.txt does not exist previously. i tried on another machine and it works, but not in my desktop.
to be more specific, i am executing a file 'setup' (a C shell script) and this needs to create symbolic links to files in a directory 'common'. these symbolic links are to be placed in another directory in the same partition. the command used in the file setup is: ln -s ../common/* .     the file 'setup' works on other desktops.
i am using a bash shell but i have csh installed as well.
i hope i convey more this time....

Check you have access permissions, you will need read permissions for the source and read/write permissions for the destination link. Also check your group permissions, maybe you are excluded somehow. 

What about testing by creating 2 folders from scratch in your home directory, create some files in one of them them and symbolic links in the other. If that works it can only be permissions.

---

### Post by Samrat Rao on 2008-03-10
the permissions cannot be a problem as i have logged in as root itself. it is my PC and there is no network connection to it either.

---

### Post by frankos44 on 2008-03-10
Is the source and target on the same PC?

---

### Post by Samrat Rao on 2008-03-11
yes the source and target is on the same pc, same partition.

i just figured that the problem is deeper. when i try to untar a file say 'foo.tar.gz' using: tar -xvvzf foo.tar.gz , it untars the file but i get the message: 'Cannot untime: Operation not permitted'. when i right click on the file and use the option 'Extract here', i get the message 'command line error'. likewise, even when i use the command 'ln -s' for creating symbolic links to files i get the message 'Operation not permitted'.
so i suppose there is a basic problem in some of the commands. please suggest a solution.

---

### Post by frankos44 on 2008-03-11
> **Samrat Rao said:**
> yes the source and target is on the same pc, same partition.

i just figured that the problem is deeper. when i try to untar a file say 'foo.tar.gz' using: tar -xvvzf foo.tar.gz , it untars the file but i get the message: 'Cannot untime: Operation not permitted'. when i right click on the file and use the option 'Extract here', i get the message 'command line error'. likewise, even when i use the command 'ln -s' for creating symbolic links to files i get the message 'Operation not permitted'.
so i suppose there is a basic problem in some of the commands. please suggest a solution.

Try this:

Log in as a different user

$ mkdir a b
$ cd a
$ touch testfile
$ cd ../b
$ ln -s ../a/testfile ./
$ ls

You should see the linked file in b. Let me know the outcome.

---

### Post by erginemr on 2008-03-11
> **Samrat Rao said:**
> yes the source and target is on the same pc, same partition.

i just figured that the problem is deeper. when i try to untar a file say 'foo.tar.gz' using: tar -xvvzf foo.tar.gz , it untars the file but i get the message: 'Cannot untime: Operation not permitted'. when i right click on the file and use the option 'Extract here', i get the message 'command line error'. likewise, even when i use the command 'ln -s' for creating symbolic links to files i get the message 'Operation not permitted'.
so i suppose there is a basic problem in some of the commands. please suggest a solution.

You said you logged in as root, but in Ubuntu the root account is disabled. Have you explicitly enabled the root account? What is the out come of "whoami" in the terminal? If it says something other than "root", then it means you are not logged in as root.

In such a case, you need to prefix your commands with "sudo" , such as "sudo ln -s ...." when working in directories and with files that you do not own. Please try the same with the "sudo" command.

---

### Post by frankos44 on 2008-03-11
> **erginemr said:**
> You said you logged in as root, but in Ubuntu the root account is disabled. Have you explicitly enabled the root account? What is the out come of "whoami" in the terminal? If it says something other than "root", then it means you are not logged in as root.

In such a case, you need to prefix your commands with "sudo" , such as "sudo ln -s ...." when working in directories and with files that you do not own. Please try the same with the "sudo" command.

No, no need to log in as root. I am just trying to find out if you are actually able to link files or not or if the problem is unique to your account alone. 

Just cerate a new user and then log into that account.

---

### Post by erginemr on 2008-03-11
> **frankos44 said:**
> No, no need to log in as root. I am just trying to find out if you are actually able to link files or not or if the problem is unique to your account alone. 

Just cerate a new user and then log into that account.

I am also against logging in as root. But he said before that he logged in as root, and is still getting "operation not permitted" errors, which doesn't make sense...

---

### Post by frankos44 on 2008-03-11
> **erginemr said:**
> I am also against logging in as root. But he said before that he logged in as root, and is still getting "operation not permitted" errors, which doesn't make sense...

I still very interested to know what happens if you log in as a different user all the same, create the 2 folders as mentioned earlier and let me know the exact message, if any.

---

### Post by Samrat Rao on 2008-03-11
i created a user account and tried the same operation, viz:
$ mkdir a b
$ cd a
$ touch testfile
$ cd ../b
$ ln -s ../a/testfile ./
      and then i get the message (same as usual)
ln: creating symbolic link `./touchfile.' to `../a/touchfile' : Operation not permitted

and yes erginemr was right, i typed whoami and it gives my name, not 'root'. but i have used sudo quite a few times it works ie it asks for my password.
just in case...my hard disk has about 2mb bad sectors, but before installing ubuntu 7.10 i formatted the whole hard disc, installed windows xp first and then ubuntu. when i start ubuntu it gives the message: there are differences between boot sector and its backup. does this info help?

---

### Post by frankos44 on 2008-03-11
> **Samrat Rao said:**
> i created a user account and tried the same operation, viz:
$ mkdir a b
$ cd a
$ touch testfile
$ cd ../b
$ ln -s ../a/testfile ./
      and then i get the message (same as usual)
ln: creating symbolic link `./touchfile.' to `../a/touchfile' : Operation not permitted

and yes erginemr was right, i typed whoami and it gives my name, not 'root'. but i have used sudo quite a few times it works ie it asks for my password.
just in case...my hard disk has about 2mb bad sectors, but before installing ubuntu 7.10 i formatted the whole hard disc, installed windows xp first and then ubuntu. when i start ubuntu it gives the message: there are differences between boot sector and its backup. does this info help?

I dont think boot sector or bad sectors are related to this problem because you successfully created   a new account on a different area of the disk. 

As far as I know you cant create links over FAT32,  FAT16 partitions or SMB shares. Take a look at the type of partition the home folder resides in, this might show some light on the matter.

---

### Post by Samrat Rao on 2008-03-11
oh my god!!! fat32 not allowed!! you mean that i cannot allow windows to access ubuntu partitions in which i will have to creart symbolic links? but i have no option i guess, as i need to know linux and am interested in learning too.
i searched in ubuntu forum and found that both fat32 and ntfs do nor allow creation of symbolic links. but i installed ubuntu 7.10 in my friend's desktop and i used ntfs filesystem for windows and it allows creation of symbolic links. i could not use ntfs for my system, as windows cannot format my hard disk using ntfs, no idea why, cos of bad sectors i guess...
so what do i do?

---

### Post by frankos44 on 2008-03-11
> **Samrat Rao said:**
> oh my god!!! fat32 not allowed!! you mean that i cannot allow windows to access ubuntu partitions in which i will have to creart symbolic links? but i have no option i guess, as i need to know linux and am interested in learning too.
i searched in ubuntu forum and found that both fat32 and ntfs do nor allow creation of symbolic links. but i installed ubuntu 7.10 in my friend's desktop and i used ntfs filesystem for windows and it allows creation of symbolic links. i could not use ntfs for my system, as windows cannot format my hard disk using ntfs, no idea why, cos of bad sectors i guess...
so what do i do?

Perhaps you need a different approach. The last thing I would entertain is allowing windows to access a Linux partition directly even it was possible. I suggest that you look into Samba first. This way you can set up a share and have control over your system without external threat. 

Personally I have never shared files with windows because I am totally Linux here but I have often accessed windows partitions from Linux directly as windows is so open and vulnerable you can do that with incredible ease.  SAMBA is the answer for you.

---

### Post by Samrat Rao on 2008-03-11
ok, but first i have to know what Samba is. i'll try to find out and then see what to do. thanks for the help. i'll get back once my problem is solved...

---

### Post by Spenzer4Hire on 2008-03-11
Wow, I would never knowingly run on a hard drive with bad sectors, not to mention 2 MB worth.  Of course individual sectors go bad from time to time, but that many?  I would consider pretty much every bit of data that you touch should be corruptable, you should be able to live without it.  Also, even if the system was used for completely unimportant tasks, I still wouldn't put up with it.  You will never know if a problem you have is related to the bad hard drive, or an actual bug or whatever.

Anyways, just my 2 cents.  Good Luck!

---

### Post by frankos44 on 2008-03-11
> **Spenzer4Hire said:**
> Wow, I would never knowingly run on a hard drive with bad sectors, not to mention 2 MB worth.  Of course individual sectors go bad from time to time, but that many?  I would consider pretty much every bit of data that you touch should be corruptable, you should be able to live without it.  Also, even if the system was used for completely unimportant tasks, I still wouldn't put up with it.  You will never know if a problem you have is related to the bad hard drive, or an actual bug or whatever.

Anyways, just my 2 cents.  Good Luck!

I agree it is a bit risky. I know in the early days when drives were less than perfect Unix would mark any bad blocks it found during formatting and prevent them from being used. I believe windows does a similar thing.

Drives are always low-level formatted by the manufacturer and any defects mapped out from existence giving the OS a perfect media.

My approach is if you start getting new bad blocks appearing throw it away.

---

