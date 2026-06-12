---
title: "Need help fixing an apparently broken file"
date: 2007-09-22
forum: General Help
---

### Post by randomlogic on 2007-09-22
Hello all.

I've been using VMWare to run Windows inside Ubuntu.  A couple of days ago, it simply stopped working.  Whenever I would try to start the virtual machine, it would get so far and simply hang.  (Great!  And me without a backup of an important data file inside that virtual machine!)

Wanting to save the file .vmdk file to another machine so that I could test an older copy, I attempted to ftp it over.  The ftp failed partway thru the transfer.

Thinking that perhaps the file was corrupted, I ran fsck, but it reported no errors.

Then I tried the following:
[FONT="Courier New"]
mark@marvin:~/vmware/Broken$ ls -l
total 4185352
-rw------- 1 mark mark       8664 2007-09-21 05:54 WindowsXP.nvram
-rw------- 1 mark mark 4281597952 2007-09-21 05:54 WindowsXP.vmdk
-rw------- 1 mark mark          0 2006-11-06 08:51 WindowsXP.vmsd
-rwxr-xr-x 1 mark mark       1298 2007-09-20 21:35 WindowsXP.vmx
mark@marvin:~/vmware/Broken$ cp WindowsXP.vmdk broken.vmdk
cp: reading `WindowsXP.vmdk': Input/output error
mark@marvin:~/vmware/Broken$ ls -l
total 4285696
-rw------- 1 mark mark  102645760 2007-09-22 09:48 broken.vmdk
-rw------- 1 mark mark       8664 2007-09-21 05:54 WindowsXP.nvram
-rw------- 1 mark mark 4281597952 2007-09-21 05:54 WindowsXP.vmdk
-rw------- 1 mark mark          0 2006-11-06 08:51 WindowsXP.vmsd
-rwxr-xr-x 1 mark mark       1298 2007-09-20 21:35 WindowsXP.vmx
mark@marvin:~/vmware/Broken$
[/FONT]
This puzzles me since I would have expected fsck to report a problem.

Does anyone know how I can go about repairing this file?

Thanks in advance for any ideas.

Mark
<<Suffering from fits of Random Logic>>

---

### Post by ryanVickers on 2007-09-22
My theory is that there's nothing wrong with the file, but rather that VMware just died randomly as it tends to do.  Try VirtualBox - It's a thousand times faster and this doesn't happen! :)

---

### Post by randomlogic on 2007-09-26
It turns out that the file was still readable.  I restored a copy of the VMDK file from another machine and loaded THAT one into VMWare.  Then, on a whim, I tried adding the broken VMDK file as a 2nd hard drive.

IT WORKED!

My Windows session saw the extra drive and allowed me to extract my data.  This is a useful trick for anyone else who runs into the problem of having an unbootable VMWare image file.

---

### Post by ryanVickers on 2007-09-26
I knew it! :p

---

