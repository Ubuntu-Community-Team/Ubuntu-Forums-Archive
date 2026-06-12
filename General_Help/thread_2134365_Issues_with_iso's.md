---
title: "Issues with iso's"
date: 2013-04-11
forum: General Help
---

### Post by jbullis on 2013-04-11
Hey guys, sorry to probably post a very generic question here but the forum i found about this stuff was like 5 years old so i didn't really think they'd be getting back to me.

Heres where im at...

Trying to download and install a program called iraf, and found a thread that gave me the following code:

sudo apt-get install libc6-dev
wget [http://www.astro.uson.mx/~favilac/do...RAF_Ubuntu.iso]("http://www.astro.uson.mx/~favilac/downloads/ubuntu-iraf/iso/IRAF_Ubuntu.iso")
mount -o loop -t iso9660 'Where is your iso?' 'Where to mount'
sh install.sh
cd ~
mkiraf
type: xgterm

everything works fine up to the mount, where i get the following message

mount -o loop -t iso9660 ~/Downloads/IRAF_Ubuntu.iso ~/IRAF
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
missing codepage or helper program, or other error
(could this be the IDE device where you in fact use
ide-scsi so that sr0 or sda or so is needed?)
In some cases useful info is found in syslog - try
dmesg | tail or so

i should also mention that i am currently using Ubuntu 12.04 LTS

any help or suggestions you guys can give me would be GREATLY appreciated

---

### Post by pinballwizard on 2013-04-11
Don't know exactly why you downloaded an image to install iraf.
Go here:
[http://iraf.noao.edu/](http://iraf.noao.edu/)
or here:
[http://iraf.net/downloads/](http://iraf.net/downloads/)

Get the correct .tar file for your architecture and install from there.

---

### Post by jbullis on 2013-04-11
Well thats where I started too, and have run into many other problems doing things that way. From the thread I was reading through this sounded like it would be a bit easier...[http://ubuntuforums.org/showthread.php?t=912583](http://ubuntuforums.org/showthread.php?t=912583)

but i guess ill go back to the other way. Maybe you can answer me this, during the install they want me to use the setenv command. where I then get this message: "No command 'setenv' found, did you mean: Command 'netenv' from package 'netenv' (universe)
setenv: command not found"

---

### Post by pinballwizard on 2013-04-11
> **jbullis said:**
> Well thats where I started too, and have run into many other problems doing things that way. From the thread I was reading through this sounded like it would be a bit easier...[http://ubuntuforums.org/showthread.php?t=912583](http://ubuntuforums.org/showthread.php?t=912583)

but i guess ill go back to the other way. Maybe you can answer me this, during the install they want me to use the setenv command. where I then get this message: "No command 'setenv' found, did you mean: Command 'netenv' from package 'netenv' (universe)
setenv: command not found"

setenv is because the program needs you to **set** an **env**ironment...
Which is a C command, not a Bash command. You need to install tcsh

```
sudo apt-get install tcsh
```

From here:
[http://askubuntu.com/questions/152705/command-setenv-not-found-upon-installation-of-crystal09-program](http://askubuntu.com/questions/152705/command-setenv-not-found-upon-installation-of-crystal09-program)

You will need an export command. I would imagine something similar to:
```

export IRAF_HOME="/usr/local/iraf"
```

From this thread: [http://ubuntuforums.org/showthread.php?t=143962](http://ubuntuforums.org/showthread.php?t=143962)

---

### Post by jbullis on 2013-04-17
Ok, so this is my 4th or 5th time trying to get this thing to work and i am very very close. Here is the thread i have been using to go thru the steps just so you guys will have an idea of what ive been doing. 

[http://ubuntuforums.org/showthread.php?t=912583](http://ubuntuforums.org/showthread.php?t=912583)

I have made it all the way down to the end where it is telling me to make the login script with the following commands:

cd ~/iraf
mkiraf
irafshell

but when i type the last line "irafshell" this is what I get in response:

root@jbullis08-NB:~/iraf# irafshell
bash: /usr/local/bin/irafshell: Permission denied

any suggestions?

---

