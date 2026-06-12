---
title: "[SOLVED] Usplash issues screen goes blank or w. no bootscript, logo is bleeding off s"
date: 2008-02-03
forum: General Help
---

### Post by streamsanddragonflies on 2008-02-03
Hi!  I was trying to figure out what I uninstalled by error since I am having a messed up Usplash until login.  If I disable the bootscript via Startup-Manager, I get a Ubuntu-studio logo stretched out to the right of the screen and bleeding off the screen and nothing on the left.  Also the progress bar is gone!  If I checkmark the 'enable bootscript" in St.up Manager, I get the logo minus the progress bar on upper portion of screen with ok ok ok ok loading on the right bottom and no scripts on the left.  Then after a few minutes the screen goes blank until login!

Now I thought that following instructions in a related report ( Wed Oct 10 06:57:37 BST 2007, maf at appgate.com) for the live CD version would help;  which includes installing:  

Versions of packages usplash depends on:
ii  debconf [debconf-2.0]     1.5.14         Debian configuration management sy
ii  initramfs-tools           0.85eubuntu19  tools for generating an initramfs
ii  libc6                     2.6.1-1ubuntu9 GNU C Library: Shared libraries
ii  libusplash0               0.5.6          userspace bootsplash library

but one related package won't install:  sysv-rc-bootsplash in the synaptic repositories, and I can't resolved the needed dependancies!  Though I have enabled all repositories in the multiverse!  I installed 'splashy', thinking that this will help- being part of the virtual pre-dependancy. 
 
He also talks copying casper-scripts but I don't have a casper-bottom folder, only a casper pre-mount!  
Quote:
"The usplash splash-screen disappears half-way through the boot process
when booting a gutsy live-CD. After some debugging I found that this
happens when the casper-scripts figure out the x-configuration
(/usr/share/initramfs-tools/scripts/casper-bottom/20xconfig).

I worked around it by basically copying
/usr/share/initramfs-tools/scripts/init-top/usplash to 
/usr/share/initramfs-tools/scripts/casper-bottom/21usplash. This has the
effect of restarting usplash after X has been configured. It is not the
most elegant solution but at least it improves the situation for me."
 End Quote.

I also changed the boot options display resolution in  Startup-Manager from 640x480 to 1024x728, since that was mentionned in another Usplash thread, but it's confusing me with the bootsplash image where you select your OS-which is supposed to be at the lower resolution. 

I even changed quiet splash to splash in the grub/menu.lst.
Even though, I am following varying instructions, I am afraid that I will break my bootup and not be able to login anymore!  No one answered me in the IRCs, though I am new to them.  I feel a bit down about this.

I get the nice simple Usplash in Xubuntu (my older computer) - progress bar and bootsrcipts and all, and I all I had done was to check 'enable boot scripts' in startup-manager- note, it was relatively easy to choose my own bootsplash image via Startup-M. for both systems!
I am hoping to find someone to just compare packages with me to see what I have wrong or missing.  I don't need a custom Usplash just wish fort the default one back, with bootscripts enabled!

:(

---

### Post by streamsanddragonflies on 2008-02-08
After worrying, the bootsplash finally works fine!  Even though there is a short version of the bootscript (root, init. bottom, top) that scrolls down below the nicely sized & centered logo along with  the progress bar!  Even though I couldn't manage to install sysv-rc-bootsplash in deb.pkgs or synaptic, it seems that the changes I made and installing all the other required pre-dependancies resolved the issue!

I have to learn backing up next to relieve the worrying though...as the first update that required a reboot in gutsy occured, and I want any change I do to my system or that is done, to be able to be  reverted back just in case...

---

