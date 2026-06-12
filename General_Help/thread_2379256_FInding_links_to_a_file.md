---
title: "FInding links to a file"
date: 2017-12-03
forum: General Help
---

### Post by eraserpencil on 2017-12-03
How do I check what links are attached to a file? I am unfamiliar with how the `find -L` command works. I always get too much info or get pointed back to the original file.

My /home/user directory is messy. I have folder like `rambox`, `snap` for example, and tonnes of .something files like `.cert`, `.compiz` etc. I'd like to do some tidying up by bunching similar file types like keys together. Hence I'm needing some help on what I can delete and what I can't, which config files to edit. Also, my /opt folder is bare empty, so I could bring some application in my /home/user directory over.

---

### Post by Frogs Hair on 2017-12-03
Are you referring to attempting combine hidden folders such as .compiz,.gnome, and so on ? If so I would not recommend it because applications and other parts of the OS use those files to run and changing their  locations could cause problems. if you don't want to see hidden folders remove the check from the show hidden option or use Ctrl + H.

---

### Post by Holger_Gehrke on 2017-12-03
```
find ~ -type l -lname <pattern> -printf '%p %l\n'
```
finds symbolic links to files fitting <pattern> in your home directory and it's subdirectories, prints their names and the names of the files they point to.

I don't know about the 'rambox' directory, but 'snap' is needed for programs installed from snap-packages to work.

All the files and directories whose names begin with a '.' are configuration files. They are 'hidden' in the sense that file managers usually don't show files with a '.' as first character of their names unless told to do so. You can usually tell from their name what program they belong to. They have to be exactly where they are, otherwise the programs won't find them and will start with the system wide default configuration which is either stored in files in /etc or built into the program.

And why do you have applications installed into your home directory ? Unless you compiled them yourself from source, this should not happen. Even then, there is usually a 'sudo make install' as the final step of installation, which normally moves the executable, its libraries and shared  data into the appropriate subdirectories of /usr/local. The '/opt' hierarchy is meant for programs that for some reason do not follow the standard way of installing programs on unix-like operating systems. They are either commercial or are cross-platform apps whose development was mainly not done on Linux.

Holger

---

### Post by eraserpencil on 2017-12-03
> **Frogs Hair said:**
> Are you referring to attempting combine  hidden folders such as .compiz,.gnome, and so on ? If so I would not  recommend it because applications and other parts of the OS use those  files to run and changing their  locations could cause problems. if you  don't want to see hidden folders remove the check from the show hidden  option or use Ctrl + H.

I'm not using the GUI. It's just everytime I do ls -al I get a very elongated list of file that makes it hard to find anything. Very soon, I might need to ls -al | grep stuff on my home directory just to find specific .files.

> **Holger_Gehrke said:**
> ```
find ~ -type l -lname <pattern> -printf '%p %l\n'
```
finds  symbolic links to files fitting <pattern> in your home directory  and it's subdirectories, prints their names and the names of the files  they point to.

I don't know about the 'rambox' directory, but 'snap' is needed for programs installed from snap-packages to work.

All  the files and directories whose names begin with a '.' are  configuration files. They are 'hidden' in the sense that file managers  usually don't show files with a '.' as first character of their names  unless told to do so. You can usually tell from their name what program  they belong to. They have to be exactly where they are, otherwise the  programs won't find them and will start with the system wide default  configuration which is either stored in files in /etc or built into the  program.

And why do you have applications installed into your  home directory ? Unless you compiled them yourself from source, this  should not happen. Even then, there is usually a 'sudo make install' as  the final step of installation, which normally moves the executable, its  libraries and shared data into the appropriate subdirectories of  /usr/local. The '/opt' hierarchy is meant for programs that for some  reason do not follow the standard way of installing programs on  unix-like operating systems. They are either commercial or are  cross-platform apps whose development was mainly not done on Linux.

Holger

So  it's not possible to ever shift them? I have never run the command  'sudo make install' I usually chmod +x and they work. I guess I'll  delete and reinstall them the proper way. What about the key files  that's created on my home directory? How do I know if I still have the  app that uses them? I vim-ed them and they have very vague information. 

I'm not using the GUI. It's just everytime I do ls -al I get a very   elongated list of file that makes it hard to find anything. Very soon, I   might need to ls -al | grep stuff on my home directory just to find   specific .files.

---

### Post by vasa1 on 2017-12-03
> **eraserpencil said:**
> ... What about the key files  that's created on my home directory? How do I know if I still have the  app that uses them? I vim-ed them and they have very vague information. 
...
What are key files? Post the names and contents of one or two of them if they're text files.

---

### Post by eraserpencil on 2017-12-03
> **vasa1 said:**
> What are key files? Post the names and contents of one or two of them if they're text files.

Example: Release.key

It's in readable text and all I got is that it's a PGP Public Key Block.

---

### Post by vasa1 on 2017-12-03
Is this your own computer? Or has someone been using it before? All I could find when searching for "release.key" was reference to developing Android apps.

---

### Post by eraserpencil on 2017-12-03
> **vasa1 said:**
> Is this your own computer? Or has someone been using it before? All I could find when searching for "release.key" was reference to developing Android apps.

It is mine. And I have tried googling, but I couldn't find any information what might be using it.

---

### Post by HermanAB on 2017-12-04
Hmm, soft links are not reverse traceable.  That is why hard links generally work better.

---

