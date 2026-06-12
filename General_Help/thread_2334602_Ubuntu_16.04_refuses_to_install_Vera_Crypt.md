---
title: "Ubuntu 16.04 refuses to install Vera Crypt"
date: 2016-08-21
forum: General Help
---

### Post by spiritglove on 2016-08-21
I have used the sudo apt-get install command and the Sudo bash command with no luck.
After downloading through the terminal, installation commands give's the following error message"

 sudo apt-get install veracrypt-1.17
[sudo] password for el: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package veracrypt-1.17
E: Couldn't find any package by glob 'veracrypt-1.17'
E: Couldn't find any package by regex 'veracrypt-1.17'
el@el-HP-G60-Notebook-PC:~$ 



I tried both vera crypt 1.18 and 1.17 with the same result 

I am a newb to this, what is going on here?

---

### Post by deadflowr on 2016-08-21
There is no veracrypt software within Ubuntu repositories.
So you need to add a repository in order to get it.
From here: [https://launchpad.net/~unit193/+archive/ubuntu/encryption]("https://launchpad.net/~unit193/+archive/ubuntu/encryption")
```
sudo add-apt-repository ppa:unit193/encryption
```
hit enter to accept the new keys,
then run
```
sudo apt-get update
```
If no errors, then install veracrypt:
```
sudo apt install veracrypt
```
then all should be good to go.

Hope it helps.

---

### Post by speartip on 2016-08-21
Assuming you have downloaded the linux package from here:
[https://veracrypt.codeplex.com/releases/view/625477](https://veracrypt.codeplex.com/releases/view/625477)
The 1st thing you need to do is right click the tar.bz2 package & extract the folder.
Then enter the folder which should have 4 files inside. Right click & "open in terminal".
Then enter the command: (if 64bit computer)
```
./veracrypt-1.18-setup-gui-x64
```
if 32 bit:
```
./veracrypt-1.18-setup-gui-x86
```
Then follow the instructions to install.

---

### Post by spiritglove on 2016-08-22
Thanks spearbit, that was the same instruction I found every where that was no help.

Adding the repositories was what did the trick, thanks Deadflowr, you got it

---

