---
title: "How to mount lvm volumes with luks"
date: 2024-08-22
forum: General Help
---

### Post by kurtoro12 on 2024-08-22
Hi, my partner and I have been trying to fix our ubuntu laptop for almost a week as It's been showing errors whenever it boots (we've already tried recovery mode, no results). 

We have gotten support from someone and have made progress until we've reached a standstill when the person helping said he couldn't find a documentation on mounting lvm volumes with luks. 
We're posting here to see if there could be any help for doing this.

Here's the archived support thread (as an HTML) for further context of the issues with images included. I'll still try to answer questions.

[ATTACH]294114[/ATTACH]

[SIZE=3][/SIZE]

---

### Post by TheFu on 2024-08-22
Remove the image!  Some people pay for internet by the byte.

So, LVM objects are inside the LUKS encrypted container. That means you need to "open" the LUKS before any LVM stuff can even be seen.  Let me find some notes.
```
# How-to mount my old C720 Luks encrypted storage
# Assume: sdf5 is the partition to be opened (usually logical partition)
# Assume: LVM is used
# sdf                               8:80   0 119.2G  0 disk  
# &#9500;&#9472;sdf1                            8:81   0   243M  0 part  
# &#9500;&#9472;sdf2                            8:82   0     1K  0 part  
# &#9492;&#9472;sdf5                            8:85   0   119G  0 part  
#   &#9492;&#9472;c720 (dm-4)                 252:4    0   119G  0 crypt 
#     &#9500;&#9472;c720--vg-root (dm-5)      252:5    0  51.9G  0 lvm   /mnt/root
#     &#9500;&#9472;c720--vg-lv--swap (dm-6)  252:6    0   4.1G  0 lvm   
#     &#9492;&#9472;c720--vg-lv--Stuff (dm-7) 252:7    0    50G  0 lvm   /mnt/Stuff
# 
# sudo cryptsetup luksOpen /dev/sdf5 c720
# sudo vgchange --activate y
# sudo mkdir    /mnt/root    /mnt/Stuff
# sudo mount    /dev/mapper/c720--vg-lv--Stuff    /mnt/Stuff
# sudo mount    /dev/mapper/c720--vg-root    /mnt/root
```

You need to know the exact, correct, name of the LUKS container.  My example above is "c720". Yours will be different.
I think the "luksOpen" command has been replace with just "open". Check the **cryptsetup** manpage for details.

I should say that I've used Ubuntu-Mate with whatever file manager it came with to open LUKS encrypted containers, then access LVM LVs all using point-n-click.  I don't know if other file mangers do this or not.  Above, I show the CLI way.

You can run **fsck** pointing at the LVs BEFORE mounting anything.
Don't forget to umount the file systems and close the LUKS container when you are done.

I can post a 24.04 LUKS encrypted system tomorrow, if you ask. That machine is shutdown for the day now.

---

### Post by bagelbagel on 2024-08-23
hiii
im the girlfriend with the broken laptop!
so i dont really know ubuntu that well and i certainly dont know much beyond the attached thread
can we clarify some things because im very confused
my ultimate goal is to restore my system and, as far as i know, i need to mount my root partition so i can retrieve logs from the day my computer first wouldnt boot
is this correct?
i dont know what lvm volumes are, but thats where my previous support thread got stuck, and its been several days since then because ive been dealing with personal health struggles
where should i be at this point?
should i use system rescue or recovery mode? 
what commands should i use and what should i be looking for?
sorry for my ignorance as i just began linux thiss year, but i dont really know most of what youre talking about although i am willing to learn
thank you for your time

---

### Post by TheFu on 2024-08-23
Will looking at logs actually help you?  Rescue or recovery mode?  I don't care.  Whatever works.  I'd use an ISO in **Try Ubuntu** mode.
I posted commands already.  They need to be modified for your needs/names/system. Only you can do that.

If you don't know what LVM is, this will be very difficult.  It is an administrator-type way to manage storage. Generally noobs don't touch it.  Enterprise servers use LVM .... and storage nerds like me.  I cannot train you on general LVM skills.  Use the internet for that.  It isn't THAT hard, but it is a different way of thinking about storage.  The LUKS+LVM setup that Ubuntu uses is pretty bonehead/simple. That's a good thing.

If what I've already posted isn't sufficient, then I doubt I can be any further help until you get some basic knowledge and skills.  If you do want to keep going, a Beginning Linux Book: [https://www.linuxcommand.org/tlcl.php](https://www.linuxcommand.org/tlcl.php) to ensure your basic skills are sufficient (about the first 250 pages) and then learn LVM using any 3-part online tutorial that you like.  LVM is LVM, regardless of the Linux distro, so don't worry that the tutorial is for some other distro.  They all use CLI. There isn't any GUI for LVM, sorry.  When you understand the relationship between LVs, VGs and PVs, that should be sufficient. Expert level isn't necessary.

If this sounds too hard, perhaps the "right answer" for you is to use the backups you've been making.  Wipe the system completely and restore all the precious data into a newly installed Ubuntu on the system.  
No backups?  I'll wish you good luck.   Anytime encryption is used, excellent backups are mandatory, not optional.

---

### Post by bagelbagel on 2024-08-23
with all due respect
i dont need to learn lvm and i dont need to dedicate my life to linux in order to be worthy of your help
i just need someone to step down from their high horse for 10 seconds to point me in the right direction
no one *needs* to read 250 pages in order to use a computer 
and this is a support forum
im doing my research right here and now from the source
and clearly, you didnt read more than two sentences from my last support thread
i get that im not entitled to help but you also dont have to reply

---

### Post by oldfred on 2024-08-23
You have one set of instructions, did you try those?
You have not posted any detail, to give more specific instructions.

Please copy & paste the pastebin link to the BootInfo summary report ( do not post report), do not run the auto fix till reviewed. Use often updated ppa version with your USB installer or any working install over somewhat older ISO. 
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

With encryption, you probably have to decrypt your install for Boot-Repair to work.

Another set of chroot instructions:
 chroot with UEFI, LVM, encryption on NVMe drive
[https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088](https://ubuntuforums.org/showthread.php?t=2349833&p=13602088#post13602088)
To chroot, you need the same 32bit or 64 bit kernel. Best to use same version.

Mount LVM - duckhook
[https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372](https://ubuntuforums.org/showthread.php?t=2383017&p=13733372#post13733372)
[https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621](https://unix.stackexchange.com/questions/339011/how-do-i-mount-an-lvm-partition/339621#339621)
For mounting encrypted see first few lines:
[https://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu](https://askubuntu.com/questions/262211/how-do-i-resize-an-encrypted-lvm-to-install-another-copy-of-ubuntu)

---

### Post by currentshaft on 2024-08-23
do it

---

### Post by TheFu on 2024-08-24
> **currentshaft said:**
> Lol, the drama.

Why don't you just ask an LLM? It literally took less than a minute to solve with ChatGPT:

lsblk
sudo cryptsetup open /dev/sdXn mycryptname
sudo vgscan
sudo vgchange -ay
sudo lvdisplay
sudo mkdir /mnt/myvolume
sudo mount /dev/your_vg/your_lv /mnt/myvolume

That should let you back up your files so you can reinstall the system.

And that is in post #2 above.  Seems like an answer to me, but what do I know?

If people could ask good questions of an AI tool, then they'd get somewhere between great and terrible answers. The problem is that all the answers seem reasonable until you actually try to use them and find out.  AI isn't the answer to all problems and is very hard to ask good questions for many people.  Even 1 word in the question can make a huge difference in the provided "answer" making it useless.   

After all, normal people struggle to even use web search tools.  I know that I struggle with some searches outside my areas of expertise.  AI is the same.

Good day everyone.

---

