---
title: "StarOffice7"
date: 2006-10-28
forum: General Help
---

### Post by joegumbo on 2006-10-28
Hi,
     I just installed "Edgy Eft"...   very impressive!!  The only other Linux I could get to work on this eMachine W3503 was Slackware 10.2.  I was hoping the an easier to use Linux would become available.  Ubuntu runs on this like it was meant to.

     I'm only having one serious issue...

     I tried to install my old copy of StarOffice7 Update1 on this.  I was informed that when running ./setup, Permission Denied.  
I then tried using sudo chmod +x after cd-ing to the cdrom, and I was informed: " chmod: changing permissions of `./setup': Read-only file system"

     I'm not sure what my next step should be.

Thanks,
-Joe G.

---

### Post by chavo on 2006-10-28
You can't change permissions on a cd filesystem, it's not writable. Just run sudo sh /path/to/setup. If that doesn't work maybe you can copy the cd to your hard drive first? 
I'm not sure I've never installed SO this way.

---

### Post by taurus on 2006-10-28
Instead of trying to install your old version of StarOffice, why not use OpenOffice!!!  Otherwise, you need to copy the setup program from your CD to somewhere on your harddrive, change permissions, and run from it.

---

### Post by joegumbo on 2006-10-29
I copied the "linux" folder to /home/user.  Then I cd'ed to the directory /home/joegum/linux/office7.  Then I ./setup.  The only thing to watch out for is if you need to install Sun's j2re included with SO.  I will refuse to install because of permission issues. In the little console that opens during installation, chmod +x to the j2re directory.  Close the directory, attempt to install again from  the GUI and it will go on fine.

Thank you,
-Joe

---

