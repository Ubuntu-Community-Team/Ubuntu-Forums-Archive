---
title: "fsck runned but not visible"
date: 2007-11-10
forum: General Help
---

### Post by colascorp on 2007-11-10
Hello!
I've a strange problem with Gusty on a notebook...
When fsck is run at startup i can't see anything.. just black screen and the HD led blinking.
I didn't have this issue with Feisty and Edgy.

Many thanks!

Kind Regards,
Guglielmo

---

### Post by mgaskell on 2008-02-12
I have the exact same problem but it just started. Where is the file that sets the parameters for the automatic fsck every 30 boots?

---

### Post by colascorp on 2008-02-12
It happened with the ATI card on my old latpop. Now I have a Dell with Nvidia and everything is fine. I don't know where the file to set fsck is. I only know that if you want fsck in the next boot you can:
[LIST]
[*]open gnome-terminal
[*]go to your home directory
[*]type "sudo touch /forcefsck"
[*]reboot your computer
[/LIST]

I hope this is useful

Regards,
Guglielmo

---

### Post by mgaskell on 2008-02-12
Thanks

Yea, I know how to force it. I looked all through the Boot folder for a file that would control whether or not the fsck was visible with no success. I'm sure it's a setting that got changed. Just need to find it.

---

### Post by Herman on 2008-02-13
[Temporarily Edit the GRUB Menu]("http://users.bigpond.net.au/hermanzone/p15.htm#Temporarily_Edit_the_GRUB_Menu") - Would that link be any help? Or is it a different problem? 

Your ext3 file system superblock sets the number of boots before the file system should be checked agian, [How to take a look at your ext3 superblock]("http://users.bigpond.net.au/hermanzone/p10.htm#take_a_look_at_your_ext3_superblock")

You can use the           tune2fs command to make changes to it if you want,
```
man tune2fs
```Personally I would  rather leave mine alone.

It's better to run an extra file system check of your own when you have time than to reduce the frequency of file system checks.
It's easy to run your own file system check from a [GParted -- LiveCD]("http://gparted.sourceforge.net/")
 or GParted in the Ubuntu Gutsy Live CD, [                         Running a filesystem check with GParted]("http://users.bigpond.net.au/hermanzone/p10.htm#Running_a_filesystem_check_with_GParted_")**. **Or you can [                      Run a filesystem check on an ext3  filesystem]("http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem") - from a Live CD - command line. Either of those will reset your mount count for you. It's better to do too many file system checks than not enough. 

Regards, Herman :)

---

