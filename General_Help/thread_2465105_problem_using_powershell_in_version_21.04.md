---
title: "problem using powershell in version 21.04"
date: 2021-07-22
forum: General Help
---

### Post by irv on 2021-07-22
I am using Ubuntu 21.04 with Gnome desktop. Today I tried to install Powershell from the snap store. I used the command in a terminal 
sudo snap install powershell --classic
and it installs without errors. But when I go to run it, it gives me this message
> Power shell
PowerShell 7.1.3
Copyright (c) Microsoft Corporation.
[https://aka.ms/powershell](https://aka.ms/powershell)
Type 'help' to get help.
No usable version of libssl was found
Aborted (core dumped)
If I try to install the package libssl it cannot find it. Has anyone else had this problem and is there a work-around.  I do have libssl-dev installed, but the problem is not being able to do a core dump because it can't find a usable version of libssl.

---

### Post by dragonfly41 on 2021-07-22
You might pick up tips from here (although it refers to 20.04).

[https://askubuntu.com/questions/1274028/how-to-install-powershell-7-on-ubuntu-20-04](https://askubuntu.com/questions/1274028/how-to-install-powershell-7-on-ubuntu-20-04)

---

### Post by irv on 2021-07-22
Thanks for the Link I tried all that was said. It isn't that I really use power shell that much, it was just a challenge to try and get it going.
Now I know why I dislike Microsoft so much. All the stupid things they try to do to keep us Linux users out of Windows. I guess I don't really want to be there anyway.

---

