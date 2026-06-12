---
title: "creating SWAP space 12.10"
date: 2012-11-11
forum: General Help
---

### Post by feri_crosby on 2012-11-11
hello, so I cant hibernate my laptop because I dont have a swap space, I created 10GB partition(8GB RAM), swap-linux type and followed this steps [http://askubuntu.com/questions/33697/adding-swap-partition-after-system-installation]("http://askubuntu.com/questions/33697/adding-swap-partition-after-system-installation")

then i tried to hibernate my laptop and it worked normally, but after hibernating, when I turned PC back on, there is no SWAP space anymore - chcecked by command "free -m" 

any ideas how to fix it to stay forever?

thanks

---

### Post by mcduck on 2012-11-11
did you remember to add the swap into /etc/fstab and /etc/initramfs-tools/conf.d/resume ? 

And did you try restarting the PC after adding the swap and making those configurations?

---

### Post by feri_crosby on 2012-11-11
yop, i remember doing it but i didnt restart pc yet, im gonna try

---

### Post by arpanaut on 2012-11-11
Did you add the entry into /etc/fstab 
as was suggested in that link.

More info here: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by feri_crosby on 2012-11-11
yop, I did...and tried restart but didnt help...

just to make sure understanding steps from the link I posted,

the "/dev/sdx" is the partition of my swap area, right? so my swap area is "dev/sda4" ..and I used this instead of every "/dev/sdx" .. right?

---

### Post by mcduck on 2012-11-11
> **feri_crosby said:**
> yop, I did...and tried restart but didnt help...

just to make sure understanding steps from the link I posted,

the "/dev/sdx" is the partition of my swap area, right? so my swap area is "dev/sda4" ..and I used this instead of every "/dev/sdx" .. right?

yes, for the mkswap command. But keep in mind that you only need to run that command once, to create the swap partition, and also every time you run that command the UUID of the partition changes. (And both fstab and the resume file need to have the correct UUID to work). So if you have executed the mkswap command after you edited those files, you should run blkid again and re-edit the files again.

---

### Post by feri_crosby on 2012-11-11
and in this command

"sudo swapon -U UUID"

the UUID is something like that? "530bccfa-3517-4921-83f2-ab7702c727e5" or do I have to put the "/dev/sda4" ??

EDIT: ok, its working now, the main problem was that I copied the UUID but added a few numbers so it was wrong UUID...fixed

thanks :)

---

