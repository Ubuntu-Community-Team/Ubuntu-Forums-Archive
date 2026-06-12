---
title: "Cant Write or Navigate to Windows Partitions"
date: 2008-03-04
forum: General Help
---

### Post by rphil2008 on 2008-03-04
I have two hard disks which I dual boot Windows and Ubuntu. My problem is I cant see nor write to my Windows partition. How can I do that?

Given:

Hard disk 1- Windows XP, NTFS, single partition

Hard disk 2- partition 1- Ubuntu 7.1
__________partition 2- Swap for Ubuntu
__________partition 3- NTFS "Data Volume" made with Windows XP

I have no problem booting, detecting flash drives and removable media. But I cannot write to my "Data Volume" from within Ubuntu. Also when I try to navigate to my Windows partition, I dont see anything at all.

I saw a link on ntfs-3g but the problem is that it assumes you can connect to the internet and download the necessary files needed for its installation. My pc has not internet connection. The long list of commands to go through seem too complicated for me.

Is there another way? Thanks!

---

### Post by twin_57103 on 2008-03-04
Will this help?  [http://monkeyblog.org/ubuntu/installing/#add_cd]("http://monkeyblog.org/ubuntu/installing/#add_cd")

What version of Ubuntu are you using?  I believe I read that NTFS write support is automatically implemented in 7.10.

---

### Post by rphil2008 on 2008-03-05
Thanks for the link. You are right about the read/write builtin support for NTFS in Ubuntu 7.1 except that this only works on the Ubuntu 7.1 Live CD. 

I am looking at my office laptop now with a Live CD. Writing and reading at the Windows NTFS volume is a piece of cake... no permissions and all that hurdles. I simply right-click on the Windows volume and create a directory or file without a hitch. I can totally wreck my Windows partition using the Live CD if that was my intention. While Knoppix Live CD will give you a warning dialog when you change the NTFS volume to read and write, the Ubuntu Live CD has no warnings about it whatsoever.

Strangely when Ubuntu 7.1 is installed on the hard drive (at my home pc) the security measures become a formidable brick wall. a newbie like me cannot write on my Windows partition for file sharing purposes. I cannot even see what's inside the Windows hard disk! I will try the Live CD on my home pc later and see if the behavior is the same.

---

### Post by tact on 2008-03-05
How exactly are you accessing the NTFS partition now?  Pls describe in detail so we can determine whats happening.

Can you cut and paste the contents of your /etc/fstab file here so we can see if thats set up, and if so if its set to mount read only.

Thanks

---

### Post by rphil2008 on 2008-03-05
<edited bellow>

---

### Post by rphil2008 on 2008-03-05
Hi guys, I have finally found a solution to the problem. Apparently in my inexperience with command line, I managed to screw up the permissions and ownership.

To answer your questions:

I initially tried to access the partitions using the command line since I was working with the book Linux toolbox focused on command line. I remembered practicing the commands chmod and chown to take control of files, dir, those partitions. I also practiced the touch command. I either messed up the results or messed up the commands... my fault. 

Thanks for juggling my mind with your comments and questions. I did all over again, properly this time and I can now write to the NTFS partitions with both the command line and GUI interface.

1. Using GUI- I simply treated the desktop like my WinXP and got the result I wanted. Click Places, Computer, right-click and New Folder or New File. It worked.
2. Using the command line- without any other preamble I simply changed to /media/disk and used touch and mkdir. It worked too!

I am mortified to admit being a real noob... complicating a simple matter.. heheh=) Ubuntu developers appeared to have anticipated the needs of new users like myself and have put measures in place to make using Ubuntu as comfortable as possible. I got engrossed by the command line facility that I forgot I can actually use the mouse!

---

### Post by tact on 2008-03-05
Glad its all sorted and you are able to work in ways you would expect.  As you learn and as your needs become clearer (to you) you may discover that there other ways to easily get to data on partitions not native to your linux installation.    Learning - the beauty of being a noob huh. :)

---

### Post by rphil2008 on 2008-03-05
thanks tact. you're right about NTFS file support on Ubuntu 7.1 too. It's all there in Ubuntu by default (at least on the Gutsy Gibbon version). I am just happy I need not go through the installation on the ntfs-3g facility.

meanwhile, pressing on to other learning topics...=)

---

