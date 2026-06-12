---
title: "[SOLVED] Boot Help"
date: 2008-05-29
forum: General Help
---

### Post by Wayne6890 on 2008-05-29
Hi, I have recently installed Ubuntu and having trouble with some boot options. When I turn my computer on in the boot menu Ubuntu appears twice. I was looking at the boot.ini in windows to see if i can remove the duplicate, but it does not even show that I have ubuntu on this machine. So my question is how do I remove the duplicate Ubuntu option in the boot menu?



Thanks



Wayne Brewster

---

### Post by drs305 on 2008-05-29
Please post the following. It will output the uncommented grub menu.lst items:
```
cat /boot/grub/menu.lst | grep -v "#"
```
What you are probably seeing is either 2 kernels, versions 16 and 17, or one version with both the normal and recovery options. Seeing the latter is probably a good thing. 

In either case, we can modify it to your liking.

PS. If you don't know how to do it, run the command, then highlight the text. In linux, you use CTRL-SHFT-C to copy and CTRL-SHFT-V to paste. When pasting into a thread, click on the # symbol at the top of the input box and put the input between the 'CODE' symbols.

---

### Post by Wayne6890 on 2008-05-29
> **drs305 said:**
> Please post:
```
cat /boot/grub/menu.lst
```
What you are probably seeing is either 2 kernels, versions 16 and 17, or one version with both the normal and recovery options. Seeing the latter is probably a good thing. 

In either case, we can modify it to your liking.

I try top edit this file but it  says permission denied. What must I do to get permission?

---

### Post by drs305 on 2008-05-29
> **Wayne6890 said:**
> I try top edit this file but it  says permission denied. What must I do to get permission?

I just wanted you to copy the result so I can see it. I've modified the command so the output is smaller. You should see something like this:

```

title           Ubuntu 8.04, kernel 2.6.24-17-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-17-generic root=UUID=cdfc1bc0-d14b-4b48-ad24-7bb40ec2ccde ro quiet
initrd          /boot/initrd.img-2.6.24-17-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-17-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-17-generic root=UUID=cdfc1bc0-d14b-4b48-ad24-7bb40ec2ccde ro single
initrd          /boot/initrd.img-2.6.24-17-generic

title           Ubuntu 8.04, kernel 2.6.24-16-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=cdfc1bc0-d14b-4b48-ad24-7bb40ec2ccde ro quiet
initrd          /boot/initrd.img-2.6.24-16-generic
quiet

title           Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.24-16-generic root=UUID=cdfc1bc0-d14b-4b48-ad24-7bb40ec2ccde ro single
initrd          /boot/initrd.img-2.6.24-16-generic

title           Ubuntu 8.04, memtest86+
root		(hd1,0)
kernel		/boot/memtest86+.bin
quiet

```

To answer your question, you must assume administrative powers to edit this system file. 
To do that, you would run the following. It will ask for your password. Type it in but you won't see it as you type, then hit enter after putting in your password.

```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
sudo gedit /boot/grub/menu.lst

```

---

### Post by Wayne6890 on 2008-05-29
This is what I have in the file



title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=671daf01-e6aa-4a88-a7c8-1a4cc42a2deb ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=671daf01-e6aa-4a88-a7c8-1a4cc42a2deb ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=671daf01-e6aa-4a88-a7c8-1a4cc42a2deb ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=671daf01-e6aa-4a88-a7c8-1a4cc42a2deb ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

---

### Post by drs305 on 2008-05-29
> **Wayne6890 said:**
> This is what I have in the file



title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=671daf01-e6aa-4a88-a7c8-1a4cc42a2deb ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-16-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=671daf01-e6aa-4a88-a7c8-1a4cc42a2deb ro single
initrd		/boot/initrd.img-2.6.20-16-generic

title		Ubuntu, kernel 2.6.20-15-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=671daf01-e6aa-4a88-a7c8-1a4cc42a2deb ro quiet splash
initrd		/boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title		Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-15-generic root=UUID=671daf01-e6aa-4a88-a7c8-1a4cc42a2deb ro single
initrd		/boot/initrd.img-2.6.20-15-generic

title		Ubuntu, memtest86+
root		(hd0,5)
kernel		/boot/memtest86+.bin
quiet

Good. You are running version 16 but also see the older kernel as well.

We can change what you see in one of four ways.

1. We can place comments in front of lines we don't want to see. They will still be in the file (and on the machine) but you won't see them.

2. We can delete these items from the menu. The system files are not erased, only the menu items.

3. We can remove the old kernels, which will automatically update the menu. This removes files from your computer.

4. We can make the changes via the System, Preferences menu. You don't modify the file yourself, ubuntu does.

Which would you like to do?

---

### Post by Wayne6890 on 2008-05-29
3. We can remove the old kernels, which will automatically update the menu.

---

### Post by drs305 on 2008-05-29
> **Wayne6890 said:**
> 3. We can remove the old kernels, which will automatically update the menu.

IMPORTANT: Before we continue, make sure you are using 16 and not 15.
Run this command. You should see **kernel 2.6.20-16-generic**  If you see 15, do not continue. If you have any questions, ask before proceeding.
```
uname -a
``` 

Generally you want to keep at least one previous kernel. However, assuming you have been using 16 for a while this is ok.

To remove the old kernel, open synaptic: System, Administration, Synaptic Package Manager. Hit the search button and enter "linux-image".

Find the listing for **linux-image-2.6.20-15-generic** and select it for removal. That will remove the old kernel and update the boot menu as well. 
IMPORTANT: Make sure this is not the kernel you are currently using.

---

### Post by Wayne6890 on 2008-05-29
Thank you very much, I followed what you said and it worked.

---

### Post by drs305 on 2008-05-29
Congratulations.

Here are some final thoughts. Each time a new kernel is added, your menu list will be expanded to include the new kernels. You can prevent the menu from expanding in the future by specifying how many to display on the menu. Right now you seem to want to see only one (many people choose to view the last two). To set this option for future kernel updates, you would change the "howmany" value in menu.lst  It would change to "howmany=1"  You can change this via menu items by installing startupmanager:
```
sudo aptitude install startupmanager
```

Then, go to System, Administraion, StarttUp-Manager, Advanced. There change the number of kernels to keep. In the Boot Options tab you can specify how many seconds you want the menu to be displayed and which kernel you want to start by default (if you have more than 1 installed).

Please mark this solved if you have no further questions. Top right of thread, Thread Tools link.

Welcome to the ubuntu forums :-)

---

