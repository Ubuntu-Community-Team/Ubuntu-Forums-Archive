---
title: "WSL2 very slow download speed, not able to install any package"
date: 2023-12-14
forum: General Help
---

### Post by raymondraymond0517 on 2023-12-14
Hi,
currently, whenever I want to download any package, 
I would first downgrade from WSL2 to WSL1, 
then install any package I need, with normal download data connection speed.
If I tried to install directly from WSL2, it will not be successful, very slow download speed,
like 10k bits per second as compared to 6M bits per second.

Is there any way to resolve this?
I am using laptop running on Windows10 installed.
Thank you for the support.

---

### Post by yancek on 2023-12-14
This is a windows question as you are using WSL, windows software of a modified and limited Ubuntu.  Why you would need to change from WSL1 to WSL2 is something you would need to question at a windows forum or the microsoft support site.  Download speeds are generally limited by hardware and your ISP limitations so if you have better download speed when not using Ubuntu in WSL, it is likely a configuration problem within WSL.  Best go to a windows forum.

---

### Post by MAFoElffen on 2023-12-14
+1 -- As I use both Windows, Linux, & Others... My daily driver Is Ubuntu...

My recommendation would be to post at the [Microsoft Community Forum]("https://answers.microsoft.com/en-us"). That, to me would be a Microsoft Bug that needs to be reported. 

WSLx is an emulation that mimics a Linux-like environment, that resides within a very controlled sand-box, within the Windows OS. It is not real Linux. The Distribution layers within that, add the distribution-like layer within that to make that feel like that distribution. Beyond feeling like a distribution, it is limited in what it can do.

WSLx uses the Microsoft Windows host system's network drivers. Though there are some settings for that which you can tune and/or tweak:
[https://learn.microsoft.com/en-us/windows/wsl/wsl-config](https://learn.microsoft.com/en-us/windows/wsl/wsl-config)
[https://learn.microsoft.com/en-us/windows/wsl/networking](https://learn.microsoft.com/en-us/windows/wsl/networking)
[https://praveendavidmathew.medium.com/enabling-network-connectivity-in-wsl-2-windows-db2226bea92a](https://praveendavidmathew.medium.com/enabling-network-connectivity-in-wsl-2-windows-db2226bea92a)

I support many users of many things (besides just Ubuntu)... I do have an interesting question to you that I am very curious about. Please help me to understand, and for my own education with this... My question to you:

It takes Windows Pro Edition to turn on the WSL Feature. It takes the same edition level to turn on Hyper-V features. What are you doing in WSL, that could not be done (better) in a full-blown installation of that distribution in a Hyper-V VM Guest?

---

### Post by SeijiSensei on 2023-12-15
I recommend installing VirtualBox on your Windows machine and use that to create virtual machine into which you can install Ubuntu 22.04.

I would never choose WSL over VirtualBox because you're too closely tied to Microsoft. With VirtualBox you can install any OS you want. I've run Linux on Windows, Windows on Linux, and Linux on Linux.

---

