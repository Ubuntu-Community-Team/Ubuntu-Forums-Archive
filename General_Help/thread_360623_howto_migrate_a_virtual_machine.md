---
title: "howto migrate a virtual machine?"
date: 2007-02-13
forum: General Help
---

### Post by madcow72 on 2007-02-13
Hey,

I am planning on re-installing my operating system, but have a Windows virtual machine that I would like to keep.  From experience, just copying the vm to another hard drive and then placing it back after install doesn't seem to work.  I always get an error of something like: "Unable to remove lock on file ...."  and can never get it to open.  The same thing after changing permissions on all files and higher folders so that I explicitly have all permissions enabled.  

So my question is:  is there any tried and true method for copying and pasting a vm so that it can still be used?  Thanks in advance!

---

### Post by beerorkid on 2007-02-13
I have been successful moving a VM's around with no problems.  i even put them in different named folders on different PC's.

I guess it could possibly have something to do with stuff in the .vmx file

I created the VM with workstation but use it in player if that makes any difference.

---

### Post by madcow72 on 2007-02-13
When you copy a vm, do you drag and drop, or use a more sophisticated command line?  I've just been doing a simple:  cp -r /var/vm/Windows /media/usbdisk/

And after installing the new system, I reverse that command, reinstall vmware and point it to that virtual machine.  So far, I haven't been successful and always have to create the vm from scratch.

---

### Post by beerorkid on 2007-02-13
yeah drag and drop to or from an ubuntu samba share.  I now have a "golden image" so when XP gets all messed up I can start anew.

I will do a bit more research.

---

### Post by madcow72 on 2007-02-13
Hmmm... The "golden image" sounds interesting.  How are you doing that?  Are you creating an .iso of a working vm, do you mean?

---

### Post by beerorkid on 2007-02-13
well I created a VM in workstation which resides on my samba server and I just copy the whole folder over to a machine that I want it to run on and start it up in player.  I even copied it over to my laptop just so I could run windows if I need to.  So I can always just delete the whole folder and copy it from the samba server again.

We do that at work with our ESX servers.  We have golden images of windows server 2003, debian, and ubuntu server. Just makes it easier.

---

### Post by madcow72 on 2007-02-13
That sounds like a great idea!  I even have a local samba share that I can use to attempt the same thing.  I'll give that a shot.  I'm going down for a little bit now, gonna install Feisty.

---

### Post by beerorkid on 2007-02-13
nice.  My network admin said he zips up the folder and burns it to a DVD.

---

### Post by madcow72 on 2007-02-13
Well...Good news and bad!  Bad news is I could NOT get Feisty to install on my computer,:confused:  so I had to reinstall 6.10.  Good news is I was able to keep my vm!  In fact, I decided to just run it off my external drive where I backed it up and save the space on my / drive.  

What I did:
```
sudo cp -r /var/vm/WindowsXP/ /media/usbdisk/
``` and then after copying...
```
sudo chown -R user:user /media/usbdisk/WindowsXP
sudo chmod -R og=rwx /media/usbdisk/WindowsXP
``` (Where "user" is obviously my personal user name)

Then, on the new install, I pointed vmware server to the /media/usbdisk/ directory during setup.
Worked this time around.  Not sure why, but not gonna complain either!

---

