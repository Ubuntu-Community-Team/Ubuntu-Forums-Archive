---
title: "can not run executables in terminal"
date: 2008-06-12
forum: General Help
---

### Post by fritzXIII on 2008-06-12
I have suddenly become unable to run executable files from within the terminal. I am running xubuntu 8.04 kernel version 2.6.24-18-generic.

I copy and paste this from the terminal:
```
fritz@basement:~$ dir
dell1300USBdriver		http+_www.apple.com_DTDs_PropertyList-1.0.dtd
Desktop				image
doom3-linux-1.3.1.1304.x86.run	programs
filesFromShare			songs
Fribdrox.bak			Untitled1.bak~
Fribdrox.pq			usefuldocuments
GNUstep
fritz@basement:~$ sudo doom3-linux-1.3.1.1304.x86.run
[sudo] password for fritz: 
sudo: doom3-linux-1.3.1.1304.x86.run: command not found
fritz@basement:~$ 

```

I am also trying to teach myself programing and created the following source file:
```
#include <iostream>
using namespace std;

int main(int argc, char *argv[])
{
	cout << "hello world";
}

```
and ran the following terminal session:
```
fritz@basement:~/programs/featuretest$ g++ -o testthing testthingy.cpp
fritz@basement:~/programs/featuretest$ testthing
bash: testthing: command not found
fritz@basement:~/programs/featuretest$ dir
testthing  testthingy.cpp

```
I tried using the gnome terminal emulator instead and still had the same problem. Does anyone know how I might go about fixing this or what I am doing wrong?

---

### Post by joselin on 2008-06-12
Try the following:

```
chmod 755 file_to_executed
./file_to_executed

```

Use "ls -l" instead of "dir". You will receive more info on any file.

Regards

---

### Post by JudgeFudge on 2008-06-12
Try ./testthing , i.e. with a ./ prefix. (unless your current directory is in the path the terminal can't find the program to execute).

---

### Post by fritzXIII on 2008-06-12
I had tried the "./" prefix on its own on the doom file to no avail.  the "chmod 755 filename" command followed by "./filename" worked perfectly.  I'll go off and research that chmod command.  many thanks.

---

### Post by bodhi.zazen on 2008-06-12
You might also want to look at setting your path.

---

