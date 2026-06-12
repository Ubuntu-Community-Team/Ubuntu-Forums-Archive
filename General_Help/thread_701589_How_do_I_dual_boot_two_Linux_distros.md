---
title: "How do I dual boot two Linux distros?"
date: 2008-02-19
forum: General Help
---

### Post by c/Kr3t on 2008-02-19
I want to put both Fedora 8 and Ubuntu Ultimate 1.7 onto one harddrive. I've been surfing the net looking for tuts and I found an easy one to do but I want to ask anyone that knows more than I to see if this will work or not.

This is the tut that I found to dual boot a linux with winblows (linux installed first).

[http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp](http://apcmag.com/5459/dualboot_ubuntu_and_windows_xp)

Would this same method work for two linux distros but instead of booting with a winblows cd, just use a linux one?

Any help or tips on how to succesfully set up a dual boot would be awesome. I just want to use two.


p.s. can you do like 4 or 5 if the computer can handle it?

---

### Post by orlox on 2008-02-19
usually, linux OSs use grub and try to configure it appropiately so it works well with preexisting linux OSs (generally the issue it's more complicated to set a windows-linux boot).

Even though, I once had trouble in setting a dual boot with fedora (i installed fedora core 4 after ubuntu and it spoiled the startup of ubuntu). I had to manually fix the file /boot/grub/menu.lst cause it had some problems with the routes of some files (this, cause the partition where I had the original OS, ubuntu, used to be mounted at / and then passed to /media/sda4 or smething like that after installing fedora). After correcting the routes on the file everything turned out neat...

Even though, I still think that altering the things on GRUB are a little complicated cause it could leave you with a system that can't startup (this actually happened to me when I was playing with this things...) and I don't remember how I fixed it....Well, but probably someone here has a more recent experience or a clearer knowledge on how to do this...

---

