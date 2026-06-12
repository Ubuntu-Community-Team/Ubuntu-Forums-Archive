---
title: "VMWare / iTunes release NTFS drive now!!!"
date: 2007-04-04
forum: General Help
---

### Post by signul9 on 2007-04-04
FIXED.    

Kept trying to run a chkdsk through VMWARE to get past the 'boot twice' message.  That never really worked...  

Ended up taking the external drive to work, and run chkdsk via XP on my work machine...  Fixed it right up, all is well!!!! 



I have an external usb NTFS drive that holds all my music.  After exploring my iTunes options in Edgy, I decided I'd try to be slick - VM install of XP, with iTunes, attach my external drive & iPod to the VM session and let iTunes do it's magic.  

All was going well - and then my VM session bluescreened.  Tried process again - bluescreened.  Each time it bluescreens it corrupts NTFS and I have to do the whole ntfsfix /dev/sda.  

I'm close to admitting defeat and just moving forward with Songbird under Edgy, however now I can't seem to eject my NTFS external from the VM Server?  Even the standard XP 'safely remove hardware' process.  The VM session ejects the drive fine but anytime Edgy tries to mount it, it gives me the 'drive scheduled for check, boot into windows twice etc.' message?  (Which I've done a few times now.)  FYI - When mounted in the XP VM, the drives works just as it should.  

I just want my NTFS to once again be mountable/accessible through Edgy and not the VM server!!!

---

