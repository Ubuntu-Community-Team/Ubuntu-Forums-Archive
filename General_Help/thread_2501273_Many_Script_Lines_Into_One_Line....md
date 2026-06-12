---
title: "Many Script Lines Into One Line..."
date: 2024-09-30
forum: General Help
---

### Post by wyattwhiteeagle on 2024-09-30
Using a small portion of a CLI-Only script.
Is it possible to make all of the below into only one line?
```
mkdir /home/wyatt/Desktop/Everything
mkdir /home/wyatt/Desktop/Everything/Image
mkdir /home/wyatt/Desktop/Everything/Text
mkdir /home/wyatt/Desktop/Everything/Document
mkdir /home/wyatt/Desktop/Everything/Application
mkdir /home/wyatt/Desktop/Everything/Wyatts-Scripts
mkdir /home/wyatt/Desktop/Everything/Compressed
mkdir /home/wyatt/Desktop/Everything/Unspecified
mkdir /home/wyatt/Desktop/Everything/Bkmk-Pswd
mkdir /home/wyatt/Desktop/Everything/Audio
mkdir /home/wyatt/Desktop/Everything/Bak-Files
```

---

### Post by Rubi1200 on 2024-09-30
Yes, it is possible.

```
mkdir -p /home/wyatt/Desktop/Everything/{Image,Text,Document,Application,Wyatts-Scripts,Compressed,Unspecified,Bkmk-Pswd,Audio,Bak-Files}

```

This will create the main directory /home/wyatt/Desktop/Everything and all the subdirectories listed inside the curly braces.

---

### Post by oldfred on 2024-09-30
Make a text file called mymkdir.sh
Make first line & I like to include name in bash files:
#! /bin/bash
# mymkdir.sh

Copy & paste all your commands into the file.
Change file to executable. 
sudo chmod +x mymkdir.sh

Then you can run file
sudo bash mymkdir.sh

---

### Post by ActionParsnip on 2024-09-30
> **oldfred said:**
> Make a text file called mymkdir.sh
Make first line & I like to include name in bash files:
#! /bin/bash
# mymkdir.sh

Copy & paste all your commands into the file.
Change file to executable. 
sudo chmod +x mymkdir.sh

Then you can run file
sudo bash mymkdir.sh

As you added the shebang you don't need "bash" when you run the script. Simply
```

sudo mymkdir.sh

```

Will do it

---

### Post by wyattwhiteeagle on 2024-11-04
> **Rubi1200 said:**
> Yes, it is possible.

```
mkdir -p /home/wyatt/Desktop/Everything/{Image,Text,Document,Application,Wyatts-Scripts,Compressed,Unspecified,Bkmk-Pswd,Audio,Bak-Files}

```

This will create the main directory /home/wyatt/Desktop/Everything and all the subdirectories listed inside the curly braces.

Where can I find info about those curly braces?
Sometimes running lines with the curly braces throw an error about those curly brackets.

---

### Post by TheFu on 2024-11-04
```
mkdir /home/wyatt/Desktop/Everything
mkdir /home/wyatt/Desktop/Everything/Image
mkdir /home/wyatt/Desktop/Everything/Text
mkdir /home/wyatt/Desktop/Everything/Document
mkdir /home/wyatt/Desktop/Everything/Application
mkdir /home/wyatt/Desktop/Everything/Wyatts-Scripts
mkdir /home/wyatt/Desktop/Everything/Compressed
mkdir /home/wyatt/Desktop/Everything/Unspecified
mkdir /home/wyatt/Desktop/Everything/Bkmk-Pswd
mkdir /home/wyatt/Desktop/Everything/Audio
mkdir /home/wyatt/Desktop/Everything/Bak-Files
```

I'd use an editor, like vim, to remove the mkdir from each line except the first and add a \ to the end of each line except the last.  That's 2 editor commands, less than 10 seconds and I'd be done.  Here's the result
```
mkdir /home/wyatt/Desktop/Everything \
  /home/wyatt/Desktop/Everything/Image \
  /home/wyatt/Desktop/Everything/Text \
  /home/wyatt/Desktop/Everything/Document \
  /home/wyatt/Desktop/Everything/Application \
  /home/wyatt/Desktop/Everything/Wyatts-Scripts \
  /home/wyatt/Desktop/Everything/Compressed \
  /home/wyatt/Desktop/Everything/Unspecified \
  /home/wyatt/Desktop/Everything/Bkmk-Pswd \
  /home/wyatt/Desktop/Everything/Audio \
  /home/wyatt/Desktop/Everything/Bak-Files
```

If it were me, I'd probably want these things on different storage, outside my HOME, so somewhere like /d/Everything/ is where I'd add all those directories. Then inside my HOME, I'd create a symbolic link pointing at the  /d/Everything location:
ln -s  /d/Everything ~/Everything.  I don't usually put things into the "Desktop" directory, but everyone has their own needs.

BTW, you can probably replace "/home/wyatt" with "~/" or $HOME, your choice.

---

### Post by Holger_Gehrke on 2024-11-04
> **wyattwhiteeagle said:**
> Where can I find info about those curly braces?
Sometimes running lines with the curly braces throw an error about those curly brackets.

```

man bash
```specifically the section "EXPANSION" subsection "Brace Expansion". The problem is that curly braces have a lot of uses. They can mark the beginning and end of the body of a function, they are used in parameter expansion ("${...}") and they can be use in brace expansion either with a list or a range.

Holger

---

### Post by TheFu on 2024-11-04
> **wyattwhiteeagle said:**
> Where can I find info about those curly braces?
Sometimes running lines with the curly braces throw an error about those curly brackets.

The internet is full of great information, especially about Linux topics.  [https://tldp.org/LDP/abs/html/index.html](https://tldp.org/LDP/abs/html/index.html) is there for all levels of Bash Scripting.  There are some really amazing things that Bash can do. 

For example, this link is about loops using variables: [https://tldp.org/LDP/abs/html/loops1.html](https://tldp.org/LDP/abs/html/loops1.html)  

Of course, with a loop, you don't have 1 command, you have N commands, but for something like the problem in this thread, it really doesn't matter if you run 10 or 1 command. The speed difference is completely unimportant in the real world for something done 1 time.  

If you needed to create 10,000 sub-directories, each limited to 200-500 sub-sub-directories then the processing time would matter.  I've learned over the decades that having a directory with even 500 items inside it drastically slows access.  I prefer to have deeper directories over flatter directories with more objects inside each individual directory.  

Plus, when a directory becomes corrupted, having fewer objects inside that directory means the corruption causes less data loss (if there aren't backups available).

There are lots of things that don't get put into manpages or guides that require experience to learn, I'm sad to say.  Plenty of experts here. When extra tidbits of experience are offered, best to try and understand those too.  Best to learn from mistakes made by others.

---

### Post by yancek on 2024-11-04
If you want this directory Everything in your Desktop directory, you can simply change to the Desktop directory then run:  mkdir Everything; cd Everything; mkdir Image Text Document  etc. just add all the other directories to that line.  You need the ; after the first 2 commands.  Works for me.

---

