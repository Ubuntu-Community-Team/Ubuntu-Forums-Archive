---
title: "Command not found while trying to install a .run file"
date: 2013-01-07
forum: General Help
---

### Post by Acadani on 2013-01-07
I've tried googling and searching in the forums, but I couldn't find the solution. It's been a while since I used Ubuntu, and I forgot everything =D

I tried to install a game called Savage 2... the first time I downloaded the game, the setup ran without issues and I got to install it. But the game wouldn't run. I installed it on a Windows partition, because I didn't have enough space on Ubuntu's partition, don't know if this might be the issue. 

I deleted everything and tried reinstalling the game, but this time the setup wouldn't run (I redownloaded the setup file like 10 times). 

I tried everything, still didn't work =D Please help me out.

acadani@acadani-N68S3:~$ cd /media/acadani/3EA8E7B2A8E7673D/Downloads
acadani@acadani-N68S3:/media/acadani/3EA8E7B2A8E7673D/Downloads$ chmod +x s2.runacadani@acadani-N68S3:/media/acadani/3EA8E7B2A8E7673D/Downloads$ sudo sh ./s2.run
[sudo] password for acadani: 
./s2.run: 1: ./s2.run: Syntax error: Unterminated quoted string
acadani@acadani-N68S3:/media/acadani/3EA8E7B2A8E7673D/Downloads$ sudo ./s2.run
sudo: ./s2.run: command not found
acadani@acadani-N68S3:/media/acadani/3EA8E7B2A8E7673D/Downloads$ s2.run
s2.run: command not found
acadani@acadani-N68S3:/media/acadani/3EA8E7B2A8E7673D/Downloads$ sh s2.run
s2.run: 1: s2.run: Syntax error: Unterminated quoted string
acadani@acadani-N68S3:/media/acadani/3EA8E7B2A8E7673D/Downloads$ ./s2.run
bash: ./s2.run: Permission denied
acadani@acadani-N68S3:/media/acadani/3EA8E7B2A8E7673D/Downloads$ cd /home/acadani/Downloads
acadani@acadani-N68S3:~/Downloads$ 
acadani@acadani-N68S3:~/Downloads$ ./s2.run
bash: ./s2.run: Permission denied
acadani@acadani-N68S3:~/Downloads$ sudo ./s2.run
sudo: ./s2.run: command not found
acadani@acadani-N68S3:~/Downloads$ sudo sh ./s2.run
./s2.run: 1: ./s2.run: Syntax error: Unterminated quoted string

---

### Post by Acadani on 2013-01-07
bump

---

### Post by BlinkinCat on 2013-01-07
> **Acadani said:**
> bump

Hi and welcome,

It is considered reasonable to bump your thread after 24 hours - unless someone replies in the meantime of course.

Cheers - :)

---

### Post by efflandt on 2013-01-08
"I installed it on a Windows partition..." says it all.

Windows filesystems have no concept of execute permission.  You can fake it with a mount option like **umask=000** (which gives anyone permission to read/write/execute anything), however, then you have to be careful about accidentally executing something that should not be executed.  By doing that I was able to run quake3 from a FAT32 USB memory stick on a Raspberry Pi (which runs an arm version of Debian wheezy Linux).

Another thing that can trip you up is that DOS/Windows uses different line endings (carriage return, linefeed) than *nix systems like Linux (linefeed only, also called newline).  So if you edit a script in Windows, or something like ftp automatically switches line endings in text files, scripts may not execute, but the error can be confusing.

For example if attempting to run a script tries to print an error about "/bin/sh^M" not found, the Ctrl+M in Linux returns to the start of the line and the rest of the error message overwrites that (ie, you only see part of the error).

I am guessing that the reason for the unterminated quoted string error when trying to use sh to run it is that something uses back slashes to continue lines, but instead of escaping the newlines, it escapes the invisible carriage returns, and the line ends with an actual newline before a closing quote.  Either that or something word wrapped during editing.

So it is usually best to stick to Linux file systems for running Linux scripts, tools for editing them, or running Linux binaries.

---

### Post by Acadani on 2013-01-08
Thanks for the reply! Now I know what to do =)

---

