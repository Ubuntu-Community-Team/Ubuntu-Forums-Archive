---
title: "[SOLVED] After update install Grub shows 2 Ubuntu generics and 2 ubuntu generic recov"
date: 2008-07-09
forum: General Help
---

### Post by Universal344 on 2008-07-09
Please go here for thread: [http://ubuntuforums.org/showthread.php?t=854743]("http://ubuntuforums.org/showthread.php?t=854743")
I posted here because because no one responded in updates & installation section.

---

### Post by drs305 on 2008-07-09
Each time a new kernel is introduced it is added to the grub menu (the kernel and its associated recovery mode). 

The number of kernels displayed is editable in menu.lst. By far the safest method to edit this display is through StartUp-Manager. 

I don't know if SUM is available for Gutsy, but I would expect so. Try to install it with:

```
sudo aptitude install startupmanager
```

Whether or not it is available (via System, Admin, Startup-Manager), there is information on using it or editing your /boot/grub/menu.lst file in the Tutorial forum:

[HOWTO: Grub Menu Kernel Display Options & StartUp-Manager]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by rraj.be on 2008-07-09
If your kernal is updated in your latest update you will be having  two kernals or more.

To remove them you can comment corresponding lines in
```

sudo gedit /boot/grub/menu.lst
```

Else you can use startupmanager to limit the number of kernals displayed.

To install startup manager type this in terminal

```
sudo apt-get install startupmanager
```

You can also do the following with StartUpManager

1) Password protect your GRUB
2) Select the default OS to boot
3) Customize the look of your GRUB
4) Set the timeout's.

---

### Post by Universal344 on 2008-07-10
I took a look at the menu file and the top two listings (the top one didn't work, screen went black) were Ubuntu kernel 2.6.22-15-generic
and the bottom two were Ubuntu kernel 2.6.22-14-generic

I think I will install the start up manager in a few minutes, but does it matter that I have an extra kernal that doesn't boot?

UPDATE: I just installed startup manager.  If I limit the kernals to 1 how do I know which one it will take away.  And if it takes away 2.6.22-14-generic than am I screwed because 2.6.22-15-generic doesn't boot?

---

### Post by drs305 on 2008-07-10
> **Universal344 said:**
> I took a look at the menu file and the top two listings (the top one didn't work, screen went black) were Ubuntu kernel 2.6.22-15-generic
and the bottom two were Ubuntu kernel 2.6.22-14-generic

I think I will install the start up manager in a few minutes, but does it matter that I have an extra kernal that doesn't boot?

UPDATE: I just installed startup manager.  If I limit the kernals to 1 how do I know which one it will take away.  And if it takes away 2.6.22-14-generic than am I screwed because 2.6.22-15-generic doesn't boot?

In this case I would uninstall the bad kernels via synaptic. When the kernel is removed via synaptic the menu.lst is also updated. What you are looking for in synaptic starts with "linux-image-2.6.24....."

Are you sure the kernel is bad - have you investigated why it's not working?

---

### Post by zvacet on 2008-07-10
> But, after it finished loading my screen went black and my monitor indicated it was not receiving a signal. 

This is just a guess but it look like it is related with your video card.After every kernel upgrade you need to install video card driver for that kernel.Maybe you should look in that direction and solve that problem.Like I said it is just a guess.

---

### Post by Universal344 on 2008-07-10
> **drs305 said:**
> In this case I would uninstall the bad kernels via synaptic. When the kernel is removed via synaptic the menu.lst is also updated. What you are looking for in synaptic starts with "linux-image-2.6.24....."

OK, I think I will try that and reply with my results.

I am doubtful it is because of drivers because when Ubuntu first installed it didn't need me to do that.  Now I have ati drivers configured on it for compiz and desktop effects to work (now I've uninstalled compiz because it sometimes made my screen do odd things)

---

### Post by Universal344 on 2008-07-10
I found the kernal in synaptic. It read Linux-image-2.6.22-15-generic.
This is one that doesn't boot in the Grub menu.  Should I tell it to remove or completely remove it.

---

### Post by drs305 on 2008-07-10
> **Universal344 said:**
> I found the kernal in synaptic. It read Linux-image-2.6.22-15-generic.
This is one that doesn't boot in the Grub menu.  Should I tell it to remove or completely remove it.

Just as a check, run this to confirm you are not using the 15 kernel:
```
uname -r
```

You can then mark it for complete removal - it will be available for download and reinstall in the future should you want to try it again.

---

### Post by Universal344 on 2008-07-10
Its not that I don't trust you its just that I'm not that experienced in unix and I want to be safe.  But what exactly will this command do.  I ask because in the malicious commands warning al lot of them had the -r switch.  Could I also get confirmation from someone else that this is safe.

Thanks

---

### Post by drs305 on 2008-07-10
> **Universal344 said:**
> Its not that I don't trust you its just that I'm not that experienced in unix and I want to be safe.  But what exactly will this command do.  I ask because in the malicious commands warning al lot of them had the -r switch.  Could I also get confirmation from someone else that this is safe.

Thanks

That's okay. You can learn what most commands do by typing "man *commandname*" in terminal. It will explain what the command does as well as the available switches (options).

This command will produce the kernel you are currently running. On my machine, running "uname -r" produces:
```
~/Desktop: uname -r
2.6.24-19-generic

```

---

### Post by Universal344 on 2008-07-10
Thanks.

Running the command produced the following output for me:

```
*username*@*computername*:~$ uname -r
2.6.22-14-generic

```

So can I tell synaptic to completely remove linux-image-2.6.22-15-generic?

---

### Post by drs305 on 2008-07-10
> **Universal344 said:**
> Thanks.

Running the command produced the following output for me:

```
*username*@*computername*:~$ uname -r
2.6.22-14-generic

```

So can I tell synaptic to completely remove linux-image-2.6.22-15-generic?

Yes. It's best to keep at least 2 kernels on your machine and available via grub. In this case, if the kernel isn't working there isn't much point in keeping the kernel even if it only leaves you one. I would suggest you try to install a newer kernel if you can. You don't have to use it but it would be good to get that second option on your machine should you run into problems later.  You can select which kernel to use via StartUp-Manager if you end up with more than one kernel on your machine.

Don't forget to mark this thread solved via the 'Thread Tools' if you get things to your liking.

---

### Post by Universal344 on 2008-07-10
When I say remove completely it says it also must remove:
[CENTER]linux-generic
linux-image-generic
linux-restricted-modules-2.6.22-15-generic
Linux-restricted-modules-generic
Linux-Ubuntu-modules-2.6.22-15-generic[/CENTER]

Can I give it the go ahead to proceed?

---

### Post by drs305 on 2008-07-10
> **Universal344 said:**
> When I say remove completely it says it also must remove:
[CENTER]linux-generic
linux-image-generic
linux-restricted-modules-2.6.22-15-generic
Linux-restricted-modules-generic
Linux-Ubuntu-modules-2.6.22-15-generic[/CENTER]

Can I give it the go ahead to proceed?

Yes you can, and here's why. Although it appears that these should be retained, the linux-generic and linux-image-generic represent the latest kernels, whatever the version. So if you ever want to install the latest kernel, you don't have to know the number. (You would have a choice of linux-image or linux-image-generic). So since you are uninstalling the most recent version it includes these package names as well. 

In any case, to confirm this, I just uninstalled the most recent kernel (in use) on my machine and got the same list of files as you did. I rebooted to the older kernel and everything went as expected.

---

### Post by Universal344 on 2008-07-10
IT WORKED!!!!!

Thank you so much.  I do have one more question to ask though.  Later today I'm going to upgrade to Hardy Heron.  Should I wait to install more kernels until I have it upgraded or should I do that first?  

Thanks again!

---

### Post by drs305 on 2008-07-10
> **Universal344 said:**
> IT WORKED!!!!!

Thank you so much.  I do have one more question to ask though.  Later today I'm going to upgrade to Hardy Heron.  Should I wait to install more kernels until I have it upgraded or should I do that first?  

Thanks again!

They will be new kernels so there really isn't much point to installing gutsy ones now. The current kernel in synaptic for Hardy is 2.6.24-19. There are later kernels available from outside synaptic but 19 is probaby what you will get (and want).

Don't forget to backup any data before upgrading. I am very happy with Hardy and hope you will be too. 

Best of luck with the upgrade.

---

