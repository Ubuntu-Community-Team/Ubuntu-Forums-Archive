---
title: "dual linux boot"
date: 2006-12-08
forum: General Help
---

### Post by tommy1987 on 2006-12-08
I have installed slackware and installed lilo to the MBR. This has not picked up Ubuntu, however I can mount the partition in slackware.

I want to dual boot them so they both appear in lilo. I have tried editing lilo.conf and added the following to the file:

#Ubuntu entry
root=/dev/hda1
image=/boot/vmlinuzetcetcetc
label=Ubuntu
read-only
#End of Ubuntu

But when typing lilo into the terminal to apply the change I get the following:

Fatal: First sector of /dev/hda1 doesnt have a valid boot signature.


Is this becuase lilo cannot see it because it is not mounted at this point?

For a resolution I either need Ubuntu to appear in lilo, alternatively I could go back to Grub as long as i can add slackware. How do I reinstall Grub to the MBR and then add slackware?

---

### Post by lucky_chouhan on 2006-12-09
1. when you installed ubuntu after slackware then lilo is 
automatically configure to use slackware as well as ubuntu.

2. 2nd option is use any boot manager 

SMB (Smart Boot Manager) is very small utility that is stored in MBR and easily supported many OS and its size is 40KB.

---

### Post by bodhi.zazen on 2006-12-09
To install grub:

boot the live Ubuntu CD

Open a terminal, type:```
sudo grub
```

This will bring up the grub prompt, enter the following:
```
root (hd0,0)
setup (hd0)
quit
```

Reboot. You should see enteries for Ubuntu and Slackware. if not, boot to Ubuntu and enter:```
sudo update-grub
```

---

### Post by tommy1987 on 2006-12-09
Thanks very much, just the useful information I have come to expect from this community!

Nice one!!

---

