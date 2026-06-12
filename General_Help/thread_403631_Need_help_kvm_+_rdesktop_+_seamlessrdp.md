---
title: "Need help kvm + rdesktop + seamlessrdp"
date: 2007-04-07
forum: General Help
---

### Post by rufius on 2007-04-07
Hi: 

     I've got Feisty Fawn installed on my laptop and I have kvm working flawlessly with Windows XP Pro. I've followed these tutorials: 

[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)
[https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo](https://help.ubuntu.com/community/WindowsXPUnderQemuHowTo)
[https://help.ubuntu.com/community/KVM](https://help.ubuntu.com/community/KVM)

I got to the point where I've downloaded seamlessrdp and extracted it into C:\. I run the following command: 

```
rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe notepad.exe" localhost:3389 -u username -p password
```

It provides a large window, logging into my virtual machine, and then it just goes to the windows desktop. I've been puzzling over this for a while now because I tried it as well on a different operating system and got the same results. Can anyone give me a hint as to where I've gone wrong? Thanks a lot!

---

### Post by rufius on 2007-04-09
bump?

---

