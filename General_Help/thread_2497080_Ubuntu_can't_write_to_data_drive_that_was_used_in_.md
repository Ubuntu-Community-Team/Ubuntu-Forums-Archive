---
title: "Ubuntu can't write to data drive that was used in Windows 10"
date: 2024-04-22
forum: General Help
---

### Post by dorasmith24 on 2024-04-22
This solution exists in scattered and not very clear format on this forum, typically partially there and incomplete, and scattered in among completely different discussion and argument.   I asked how to solve this problem here maybe a year ago, and got crossly yelled at for using Windows and Ubuntu with teh same drives and some files both operating systems need to be able to access, and never given the solution.  It literally took me years to find and understand the solution.  I literally have two or three years of files in Documents on my Ubuntu drive that belong in My documents on my data drive, that I wasn't able to store there - like my tax returns and W2 forms, that I now have to move.  People need to have ready access to the solution to this problem in clear straightforward English.

The problem is that if you have dual boot with Ubuntu and Windows 10, probably with Windows 11 as well and almost certainly with other versions of Linux, and you have a data drive that both operating systems can access, Windows somehow makes it impossible for Ubuntu to write to the drive.  You can't save anything to the drive, or edit anything on that drive, and software like your email client that needs to write to the drive claims your mail store folders aren't legal.

   Sometimes the problem seems to extend to the ability to even boot the Ubuntu system drive.  It may only pertain to drives that were formatted in certain ways, one of which is NTFS.  If you want to be able to put Windows files on a drive, which some of us do, you can't format it for only Linux file systems.   I've never had Windows disable my ability to boot into Ubuntu, as my drive, sometimes drives, that do that, are formatted in I think ext4.  

Far more forum discussions, here and elsewhere, go into long convoluted and very unclear discussions on how to change drive permissions that only occasionally ever works; there seems to be some convoluted work around that can let Linux use a drive it doesn't have access to, that I can't even understand, because the instructions on how to do it are never written fully and clearly in simple English.  In any case this isn't how to solve the problem.

The cause of this problem is that you have to MAKE, Windows 10 unmount the drive, because, Windows 10 is Microsoft and everything has to be stupid.  (Might be more cause to yell at people for using Windows, but some of us have to use it for work or to use certain software.) 

  If the drive isn't unmounted, than some switch on the drive stays set so that nothing else has full use of that drive.  It's the same problem that used to be common on flash drives.  Windows 10 has this default quick restart process where instead of fully shutting down, the system goes into some kind of sleep or hibernation, I don't fully have the details down and it doesn't matter, where some things are never fully unloaded or released, so when you boot back up everything is in some sense there.   Not that your screen is there with everything you were running, though.   It makes Windows 10, which will never load not stupidly in any way that makes sense, load stupidly faster. 

To solve this you have to turn off fast start in Windows 10, then disable hibernation.   Possibly you don't actually have to do both, but the people who succeeded best at solving the problem seem to do both, as I did.  It certainly is not harmful to do both.  

To turn off fast start, 
Right click on Start/ the Windows icon in the lower left corner of teh screen.
Choose power options.
Choose additional power settings.  
Choose "what the power buttons do"
Click on change settings currently unavailable
Uncheck Fast start.   
Save changes.
Reboot - but not yet.

To disable hibernation,
Run the command window as administrator.  
Type in:
     powercfg.exe/hibernate off
return.
Now reboot the computer.   

Then shut down teh computer and boot into Ubuntu, and I had full access to my data drive and everything on it.

---

