---
title: "rdiff-backup files from Mac to Ubuntu - zsh:1: command not found: rdiff-backup"
date: 2022-12-25
forum: General Help
---

### Post by freeflyjohn on 2022-12-25
I had rdiff-backup working sucessfully, until I replaced my Mac Book Pro 2011 (running High Sierra OS) with a Mac Book Pro M1 (running Ventura OS).

When I run my backup script, I now get the error "zsh:1: command not found: rdiff-backup'

```

2022-12-25 12:12:23.980941 +0000  <CLIENT-231430>  Using rdiff-backup version 2.0.0
2022-12-25 12:12:23.981045 +0000  <CLIENT-231430>      with cpython /usr/bin/python3 version 3.8.10
2022-12-25 12:12:23.990444 +0000  <CLIENT-231430>      on Linux-5.4.0-135-generic-x86_64-with-glibc2.29, fs encoding utf-8
2022-12-25 12:12:23.991124 +0000  <CLIENT-231430>  Executing ssh -C myname@johns-mbp.fritz.box rdiff-backup --server
2022-12-25 12:12:23.992744 +0000  <CLIENT-231430>  Client sending (0): ConnectionRequest: Globals.get with 1 arguments
2022-12-25 12:12:23.993041 +0000  <CLIENT-231430>  Client sending (0): version
[COLOR=#ff0000]zsh:1: command not found: rdiff-backup[/COLOR]
2022-12-25 12:12:24.198357 +0000  <CLIENT-231430>  Fatal Error: Truncated header string (problem probably originated remotely)

Couldn't start up the remote connection by executing

    ssh -C myname@johns-mbp.fritz.box rdiff-backup --server

Remember that, under the default settings, rdiff-backup must be
installed in the PATH on the remote system.  See the man page for more
information on this.  This message may also be displayed if the remote
version of rdiff-backup is quite different from the local version (2.0.0).

```

I use rdiff-backup to backup files onthe Mac to the Ububtu server, using SSH to pull data from the Mac to the server...

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291448&stc=1[/IMG]

I run the following script from the Ubuntu server...

```

#!/bin/bash

# Use this script to perform a backup of Mac user to the server via SSH 
# Source:     /Users/myname
# Destination:    /media/storage/Backup/Mac/myname

rdiff-backup -v9 --print-statistics \
    --exclude-special-files \
    --exclude ignorecase:'**.ini' \
    --exclude ignorecase:'**.DS_Store' \
    --exclude ignorecase:'**\$RECYCLE.BIN' \
    --exclude ignorecase:'**.AppleDouble' \
    --exclude ignorecase:'**.localized' \
        --exclude /Users/myname/Documents/Microsoft\ User\ Data \
    --exclude /Users/myname/Documents/Parallels \
        --exclude /Users/myname/Downloads/svn \
        --include /Users/myname/Desktop \
    --include /Users/myname/Documents \
    --include /Users/myname/Downloads \
    --include /Users/myname/Movies \
    --include /Users/myname/Music \
        --include /Users/myname/Pictures \
    --exclude '**' myname@macbookpro.fritz.box::/Users/myname \
    /media/storage/Backup/Mac/myname

```

The Mac has rdiff-backup version 2.0.5 which I installed using Mac ports, the Ubuntu server has rdiff-backup version 2.0.0.

I can SSH from the Ubutnu server to the Mac using SSH keys (I disabled password login) and vice versa.

When I manually connect from Ubuntu to the Mac using SSH and run the rdiff-backup command it works, but for some reason rdiff-backup does not work when I run the script.

On the older Mac Book Pro 2011, I had to add the following line to ~/.bashrc...

```

PATH=/usr/local/bin:$PATH

```

It seems the new Mac M1 uses zsh now instead of bash and I am not sure whether I need to do something similar ?

Its as if when Ubuntu connects to the Mac via SSH, it tries to run rdiff-backup (on the Mac) but the command cannot be found ?

But if this were the case then I would expect to get the same error when I manually SSH from Ubutnu to the Mac and run the rdiff-backup command, which does in fact work correctly.

---

### Post by Tadaen_Sylvermane on 2022-12-25
Rdiff-backup needs to be installed on both the source and the target for it to work. It's not a singular thing. Check if it's installed on the new mac and reinstall as needed if possible. If not then you would need to move to something other than rdiff-backup.

---

### Post by freeflyjohn on 2022-12-25
> **Tadaen_Sylvermane said:**
> Rdiff-backup needs to be installed on both the source and the target for it to work. It's not a singular thing. Check if it's installed on the new mac and reinstall as needed if possible. If not then you would need to move to something other than rdiff-backup.

Thanks Tadaen_Sylvermane, rdiiff-backup is installed on both the source and the target, I had to do the same with the old Mac.

When I originally got rdiff-backup working on the old Mac, the version of rdiff-backup that came with the Mac OS was too old and the only way to install a newer version was to use this command...

```
pip install rdiff-backup==2.0.0
```

The new Mac didn't seem to have rdiff-backup installed, I had to use Mac Ports to install it.

When I check the version of rdiff-backup on the Mac (using rdiff-backup -V) it reports the version as 2.0.5

When I check the version of rdiff-backup on Ubuntu (using rdiff-backup -V) it reports the version as 2.0.0

So both machines do have rdiff-backup installed and both versions are almost the same.

---

### Post by Tadaen_Sylvermane on 2022-12-25
Is rdiff-backup in the default $PATH on the mac?

---

### Post by freeflyjohn on 2022-12-25
> **Tadaen_Sylvermane said:**
> Is rdiff-backup in the default $PATH on the mac?

Im not too sure, on the older Mac Book Pro 2011 I had to add the following line to ~/.bashrc... 

```

PATH=/usr/local/bin:$PATH

```

But it seems the new Mac M1 uses zsh now instead of bash (so I dont think it uses the .bashrc file), therefore I am not sure whether I need to do something similar for zsh ?

Then again, if the path was wrong then I would expect to get the same error when  I manually SSH from Ubutnu to the Mac and run the rdiff-backup command.

When I manually SSH from Ubutnu to the Mac the rdiff-backup command works (it shows the version as 2.0.5).

---

### Post by Tadaen_Sylvermane on 2022-12-25
Found this. Maybe try it with a .profile or .bashrc to see if it will import the $PATH. Just an idea. I don't know enough about a Mac to go further personally.

[https://stackoverflow.com/questions/764600/how-can-you-export-your-bashrc-to-zshrc](https://stackoverflow.com/questions/764600/how-can-you-export-your-bashrc-to-zshrc)

---

### Post by freeflyjohn on 2022-12-26
> **Tadaen_Sylvermane said:**
> Found this. Maybe try it with a .profile or .bashrc to see if it will import the $PATH. Just an idea. I don't know enough about a Mac to go further personally.

[https://stackoverflow.com/questions/764600/how-can-you-export-your-bashrc-to-zshrc](https://stackoverflow.com/questions/764600/how-can-you-export-your-bashrc-to-zshrc)

Thanks Tadaen_Sylvermane, I have been playing around with these profiles but they havent worked and to be fair I dont really know what Im doing.

It seems to be more difficult and confusing now that the Mac uses zsh instead of bash ?

What I cant understand is when I SSH from the server to the Mac, the rdiff-backup command is found (here it reports the version as 2.0.5)...

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291455&stc=1[/IMG]

Yet when I run the script (which I assume effectively does the same thing) the rdiff-backup command cannot be found...

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291456&stc=1[/IMG]

Just for reference, the rdiff-backup version on Ubuntu is 2.0.0...

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291457&stc=1[/IMG]

And from the Mac terminal (zsh) the rdiff-backup version is 2.0.5...

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291458&stc=1[/IMG]

---

### Post by freeflyjohn on 2022-12-27
At last I got it working !

I created the profile .zshenv with the following path...

```
PATH=/opt/local/bin:$PATH     
```
 
 Then refreshed the profile using...

```
source ~/.zshenv     
```
 
and now the rdiff-backup command works.

What a palava !

Thanks all for taking the time to help :)

---

### Post by Tadaen_Sylvermane on 2022-12-27
Awesome. Make sure and mark the thread solved. Glad you got it.

---

