---
title: "Trying to run an executable that exists but Ubuntu says doesn't!"
date: 2006-10-28
forum: General Help
---

### Post by mwob on 2006-10-28
Hi,

I am following instructions to install my USB modem. I have an executable file called "firmware-extractor" that I need to execute against a file that I have. The executable file exists in my home folder and when I "ls" it appears green (not sure what that means). 

Anyway, when I try to run it I get told that there is no such "file or directory". The instructions do specify that I should enter "./" before "firmware-extractor" ( not sure what the ./ means), but it still falls over with the same "firmware-extractor: No such file or directory" error... Am I missing something obvious here, is this something related to permissions in linux?

I'm totally perplexed because the error is telling me that my file does not exist, when it obviously does! 

Thanks

Matt

---

### Post by meng on 2006-10-28
make sure it has execute permissions:
chmod a+x firmware-extractor

Now:
./firmware-extractor

---

### Post by mitch.c on 2006-10-28
> **mwob said:**
> Hi,

I am following instructions to install my USB modem. I have an executable file called "firmware-extractor" that I need to execute against a file that I have. The executable file exists in my home folder and when I "ls" it appears green (not sure what that means). 

Anyway, when I try to run it I get told that there is no such "file or directory". The instructions do specify that I should enter "./" before "firmware-extractor" ( not sure what the ./ means), but it still falls over with the same "firmware-extractor: No such file or directory" error... Am I missing something obvious here, is this something related to permissions in linux?

It sounds like the file is executable based on the LS_COLOR, but if you want to be sure, type:
```
user@ubuntu:~$ chmod 755 ~/firmware-extractor
```
To run the command from inside your home folder, type:
```
user@ubuntu:~$ ./firmware-extractor
```
The "./" is a "shortcut" for this directory, so if you are currently in your home directory, "." is the same as "/home/yourusername", or "~". The reason for this syntax is that executing a command or script from inside the current directory is considered a security risk.

To run from somewhere else, use the absolute path (or ~ for your home directory):
```
user@ubuntu:~$ ~/firmware-extractor
```

---

### Post by absurdhero on 2007-11-05
I ran into this problem today in a similar situation. Despite this threads age, I am replying to that fellow googlers can get an answer. The cause of this bizare error is that I am running a 64-bit operating system and the binary I was trying to execute is 32-bit. The system looks for a 32-bit dynamic loader and cannot find it. So, bash correctly reports that the file cannot be found.

If you install the ia32-libs package, the problem will be corrected.

I should also point out that it is not possible for the problem to be related to setting the binary as executable. If any of you who proposed that solution have ever tried executing something for which you didn't have executable permission, you would get a permission denied error NOT "no such file."

---

