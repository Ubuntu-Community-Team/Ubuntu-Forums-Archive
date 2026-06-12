---
title: "OpenVPN does not give access to remote resources in VirtualBox"
date: 2015-03-27
forum: General Help
---

### Post by johnyjj2 on 2015-03-27
Hi,
I've installed OpenVPN on virtual machine in VirtualBox with Windows 7 x64 that is launched in my Ubuntu laptop. (Ubuntu is main system, Windows is hosted).
I can launch OpenVPN as administrator and connect to VPN correctly. Logs don't show errors. However, when I try to access local resources in company's LAN, I cannot. I don't see their network drives in My Computer. However, I can connect to remote desktop of my computer or see local intranet site in the web browser.
I've asked administrator and he said it works for everyone who uses Win 7. He just mentioned that it has to be launched as administrator (it runs like that). When I said to him that it's virtual machine on Linux, and not just ordinary Windows installation, he suggested that the way how Windows is virtualized under Ubuntu or maybe some Ubuntu firewall settings can be the issue. He also said it works for other Windows machine with ordinary installation, not virtualized.
What may be the reason that I cannot access intranet resources when I'm connected to VPN with OpenVPN in my virtualized Windows? Is it correct assumption of the administrator that it has something in common with virtualization in Ubuntu?
I've also tried to see "Network" section in left side of My Computer, but it only shows VSBOXSVR and the second item with name of my virtual machine account.
Thanks in advance for help!

---

### Post by nerdtron on 2015-03-28
What is the network setting of the windows VM? I think you should try to choose "Bridge' adapter here. reboot and see if it makes a difference.

---

### Post by SeijiSensei on 2015-03-28
Why are you connecting from the VM?  Have you tried connecting with OpenVPN from Ubuntu directly?  If you set up the tunnel on the host, the guest should be able to use it.  Nerdtron's suggestion of using bridge networking for the VM might help avoid the problem, so you should give that a try first.

---

