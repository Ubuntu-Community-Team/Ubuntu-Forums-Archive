---
title: "Help mounting an image.dd file for use with photorec"
date: 2018-11-16
forum: General Help
---

### Post by michko2 on 2018-11-16
I'm looking for some help, obviously, lol.

I had a hard drive that crashed.  I imaged it to an external drive in an image.dd file.  The external drive is 1GB, the image.dd file is 619.2GB of that space.  There are other folders and files on the external drive.

When I run photorec, I can't get it to select just the image.dd file.  I seem to be locked into scanning the entire external drive, which is not what I want.

I did some research before coming here.  Here is where I get stuck:

I ran    	 	 	 	   sudo mkdir /mnt/disk_image
which took me back to a prompt, which is what it is supposed to do.

I *think* this command should mount the image.dd file:
  	 	 	 	   
sudo mount -o loop -t auto /media/mich/My\ Passport\ Ultra/image.dd /mnt/disk_image
  
  
Unfortunately, that command returns the following:
  	 	 	 	   unknown filesystem type 'LVM2_member'.
  

Not sure where that is coming from or what to do from here.  Any help would be appreciated.

Thank you in advance.

---

### Post by michko2 on 2018-11-17
Forgot to add:

If I do not use mkdir to create the mount point first, or simply change the name of the target to one that has not yet been created, then I get a mount point does not exist error.

I.E.:

use:
  	 	 	 	   sudo mount -o loop -t auto /media/mich/My\ Passport\ Ultra/image.dd /mnt/disk_image3

This returns:
  	 	 	 	   
mount: /mnt/disk_image3: mount point does not exist.
  

So, if i create the mount point first, I get the unknown file system type error.  If I don't create the mount point first, I get a mount point does not exist error.

thank again.

---

### Post by michko2 on 2018-11-24
No one?  Is the question so simple that I should figure it out myself, or is it hard enough that no one has any input?  Or am I not polite enough?  So I'm going to say "please"

---

### Post by dragonfly41 on 2018-11-24
I will try .. but I have no personal experience in LVM (logical volume management).
The clue is the string you reported ...

[COLOR=#000000]unknown filesystem type 'LVM2_member'

Try google search .. Ubuntu NEAR [/COLOR][COLOR=#000000]unknown filesystem type 'LVM2_member'

and you will find more informed help than I can offer.[/COLOR]

---

