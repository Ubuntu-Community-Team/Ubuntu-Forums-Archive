---
title: "Error when restarting virtual machine"
date: 2007-10-10
forum: General Help
---

### Post by hilfer on 2007-10-10
Hi all:

I have a virtual machine where I installed ubuntu 7.04.

Everything was working till this morning.

When I try to enter the virtual machine I get the following error:


Unknown error creating VM (VERR_INVALID_PARAMETER).
VBox status code: -2 (VERR_INVALID_PARAMETER).

 RESULT CODE: E_FAIL (0x8004005)
COMPONENT: CONSOLE
{1dea5c4b-0753-4193-b909-22330{64ec45}

What does it means ??

---

### Post by dabl on 2007-10-10
Did you install a kernel upgrade?  That will break your VMWare configuration.  Fix it by running ```
sudo /usr/bin/vmware-config.pl
```

HTH!  :)

---

### Post by hilfer on 2007-10-10
Hi DABL:

How can I run the code if I cannot enter at the virtual machine ??
This code can only be runned from inside ubuntu, Right ??

---

### Post by dabl on 2007-10-10
Ahhhh -- my misunderstanding -- sorry.  I thought your VM was "in" Ubuntu (like mine).  I guess your VM is "in" Windows or some other OS?  So Ubuntu is the "guest", right?

Well, then I think the configuration must be fixed in the "host" OS.  I don't think this problem is with Ubuntu -- it is with the VM configuration in the host.  :(

---

### Post by hilfer on 2007-10-10
Yes ubuntu is the guest.

So the problem is on windows, something is preventing VM to open.

Which means that the answer should come from experts on virtualBox.

I have a post in virtualBox forum.Maybe someone has answers.

Thank you anyway.

---

### Post by bodhi.zazen on 2007-10-10
Well , can you provide more information please .

What is your host OS ? 

I assume Ubuntu is your guest.

And, from the error message, it looks like you are using virtual box (not VMWare).

dabl's command is for VMWare ;)

Can you start a new guest (boot the ubuntu iso on a new machine)?

---

### Post by hilfer on 2007-10-10
Yes I'm using virtualBox.

My host OS is win XP PRO sp2.

I didnt try to start a new guest as it takes too long to install ubuntu again.

I will try another day , as I think I dont have any other solution.

Tks.

---

### Post by bodhi.zazen on 2007-10-10
LOL

You do not need to install Ubuntu, I am just curious as to if you can boot the iso.

That will tell us if the problem is with the host of guest.

You might have better luck posting on the Virtual Box forums ;)

---

### Post by hilfer on 2007-10-11
I have posted at virtualbox forum yesterday at 2 pm but so far I have no replies.

---

### Post by Arghesis on 2007-10-11
I'm having the same error on my Virtual Box. But I'm using it the other way. I have Kubuntu 7.04 installed and did a winxp pro sp2 install on virtual box.

i followed the howto from the ubuntuforums, and did there some file changes in order to set up my network and bla bla, but it didn't work. Unfortunately, my ez-ipupdate program didn't work either, so i went back and undo the networking changes and now it works fine, except with the virtual box.

if you know any solution to the problem, please let us know.
i'll try to make another machine to boot from it.

cheers


I was able to create a new machine. i'm hoping to be able to fix the old one so i don't have to do the reinstall all over again...

---

### Post by hilfer on 2007-10-14
I installed Ubuntu  7.04 again in a new VM and its working great.
Now I have one question.How can I share files from one OS to another ???
Is it possible? ?

If so please let me know how.

rgds.hilario.

---

### Post by bodhi.zazen on 2007-10-14
> **hilfer said:**
> I installed Ubuntu  7.04 again in a new VM and its working great.
Now I have one question.How can I share files from one OS to another ???
Is it possible? ?

If so please let me know how.

rgds.hilario.

I was afraid of that :(

There are several ways to share. You can share with USB devices, share a partition, or via any network protocol (ssh, scp, sshfs, nfs, samba, ftp, http).

I personally nfs (you can mount a nfs on Windows) and sshfs

---

