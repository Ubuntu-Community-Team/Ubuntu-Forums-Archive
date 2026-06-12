---
title: "how do I insert text from a file into bash command line?"
date: 2012-11-12
forum: General Help
---

### Post by gam01hr on 2012-11-12
hello,
I'm working in the terminal window. I have a long favorite command stored in text file. I'd like to insert content of the file to command line, then manually change some parameters and run it.

example:
```
$cat my_mount.txt
sudo mount -t vfat /dev/sdb1 /media/disk1 -o rw,... very long line here ...
```Sometimes  I want change /dev/sdb1 to /dev/sdc1 and so on.  I don't want to write script, I want just simply put the text to bash command line and rewrite the parameters. 

Of course I can do this with mouse "copy" & "paste". But I wonder if it would be possible only with the keyboard.

---

### Post by Lars Noodén on 2012-11-12
You can do it with [substitution](http://www.gnu.org/software/bash/manual/bashref.html#Command-Substitution) $()

```
$(cat my_mount.txt)

```

The $ is not the prompt in this case, it is part of what you type.

---

### Post by gam01hr on 2012-11-12
thank you, I tried you way. It seems that the command is executed immediately. I would like edit it on command line before it starts.

---

### Post by pkadeel on 2012-11-12
> **gam01hr said:**
> hello,
I'm working in the terminal window. I have a long favorite command stored in text file. I'd like to insert content of the file to command line, then manually change some parameters and run it.

example:
```
$cat my_mount.txt
sudo mount -t vfat /dev/sdb1 /media/disk1 -o rw,... very long line here ...
```Sometimes  I want change /dev/sdb1 to /dev/sdc1 and so on.  I don't want to write script, I want just simply put the text to bash command line and rewrite the parameters. 

Of course I can do this with mouse "copy" & "paste". But I wonder if it would be possible only with the keyboard.
If it is only the mouse which you don't want to use then use keyboard short cuts for copy paste.

Right now I don't have gedit & Kate installed but i remember I have seen such option in both or may be in one of these two softwares to send the text to terminal.

---

### Post by dannyboy79 on 2012-11-12
I am not certain on this but Y not enter the various strings you always use in /etc/fstab but have it "noauto", which means it doesn't auto mount it, but it only mounts it when you want and it would be as easy as sudo mount /dev/sdXx and I think it parses the fstab and mounts the partition with the options you want.

good luck.

PS (this seems weird to begin with and I see you have vfat which is fat32 and most likely an external drive, they should just be automounted when you plug it in.

---

### Post by Impavidus on 2012-11-12
I would use /etc/fstab, but if you want to use commands in this way (maybe something else in the future), you can edit the text file in a text editor in your terminal (vim, ed if you really want to make things complicated) and than execute it:```
vim my_command.txt
bash my_command.txt
```No mouse involved.

---

### Post by gam01hr on 2012-11-12
thank you, this way is suitable for me. It is easy to remember. The other commands, I don't remember, I just put into the text file :-)

---

### Post by gam01hr on 2012-11-12
have found some extra way:
**$ history -r my_command.txt**
"key arrow up" selects the command and I'm able to edit it

---

### Post by stinkeye on 2012-11-12
> **gam01hr said:**
> have found some extra way:
**$ history -r my_command.txt**
"key arrow up" selects the command and I'm able to edit it

You may find this way to search your bash history easier.
[**_[COLOR="DarkRed"]http://ubuntuforums.org/showpost.php?p=12339577&postcount=30[/COLOR]_**]("http://ubuntuforums.org/showpost.php?p=12339577&postcount=30")

---

