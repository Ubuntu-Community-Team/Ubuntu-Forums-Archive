---
title: "How do I copy the download from Windows 10 to Ubuntu Root?"
date: 2021-07-20
forum: General Help
---

### Post by tangara on 2021-07-20
Hi experts,

I am learning how to do CI Jenkins with Ubuntu.  Unfortunately I am on Windows 10 and I have a Ubuntu 20.04 LTS with WSL2.

Now, I got a pem key from AWS but it will only download to Window 10 and not Ubuntu.

So, how do I copy the pem key that is in Windows 10 and make it go to Ubuntu root?  since I need it to work together with Jenkins and Nginx which I have installed in Ubuntu root.

Hope that it can be done.

Tks.

---

### Post by mastablasta on 2021-07-21
why would you install something in root?

anyway you use sudo command to elevate you privilege to admin. more here: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by yancek on 2021-07-21
> So, how do I copy the pem key that is in Windows 10 and make it go to Ubuntu root?    

It's a simple process of mounting the partition, accessing it and doing the copy on an actual install of Ubuntu.  In some cases, as suggested above you may need root (sudo) privileges.  Ubuntu on WSL doesn't work the same way.  I'm sure microsoft has a site somewhere describing and documenting WSL and that would likely be a better place to go for information.

[https://docs.microsoft.com/en-us/windows/wsl/about](https://docs.microsoft.com/en-us/windows/wsl/about)

When you say root, are you referring to the /, root of the filesystem as I can't imagine any reason to copy to the root user directory.

---

### Post by grahammechanical on 2021-07-21
I offer these links as evidence that the answers to questions about Windows Subsystem for Linux are on the internet. I can in no way validate the correctness of the commands offered in these links

[https://ridicurious.com/2018/10/18/2-ways-to-copy-files-from-windows-10-to-windows-sub-system-for-linux/](https://ridicurious.com/2018/10/18/2-ways-to-copy-files-from-windows-10-to-windows-sub-system-for-linux/)

[https://stackoverflow.com/questions/42586120/copy-files-from-windows-to-windows-subsystem-for-linux-wsl](https://stackoverflow.com/questions/42586120/copy-files-from-windows-to-windows-subsystem-for-linux-wsl)

Regards

---

### Post by tangara on 2021-07-22
Am I right to say that using UBUNTU WSL2 in Windows 10 is like having a crippled leg?

---

### Post by yancek on 2021-07-22
>  Am I right to say that using UBUNTU WSL2 in Windows 10 is like having a crippled leg? 

Never used it myself but most of what I have read about it has been negative.  Questions about it are better posted at a windows forum as it is microsoft software, a modification of Ubuntu to (supposedly) run on windows.  Only microsoft knows what modifications they have made.

---

