---
title: "TRUECRYPT   really really need help"
date: 2012-12-26
forum: General Help
---

### Post by DD4lifeusmc on 2012-12-26
Forced to buy new computer. Samsung  series 3. I now have Ubuntu 12.10  64 bit on it, no windows.
In 11.04 and 11.10 we had to edit the whitelist for truecrypt to work properly.
I downloaded newest version of truecrypt. Installed it. the window opens.
But can't find the whitelist file like before.
Tried to open an encrypted volume copied from old computer.
Refuses to open, get this error message.
Truecrypt  device-manager: resume ioctl on truecrypt1_0 failed!
invalid argument command failed.

Ok is the truecrypt installation bad
Is the encrypted volume bad or non usable on the this new computer
Is it 12.10 causing the problem
is it the computer and this new screwed up UEFI secure boot causing the problem

So do we still have to edit the whitelist and if so where is it now?
Anybody know how to get truecrypt running correctly.
I got business data I need to retrieve!
Thanks

---

### Post by rnerwein on 2012-12-27
> **DD4lifeusmc said:**
> Forced to buy new computer. Samsung  series 3. I now have Ubuntu 12.10  64 bit on it, no windows.
In 11.04 and 11.10 we had to edit the whitelist for truecrypt to work properly.
I downloaded newest version of truecrypt. Installed it. the window opens.
But can't find the whitelist file like before.
Tried to open an encrypted volume copied from old computer.
Refuses to open, get this error message.
Truecrypt  device-manager: resume ioctl on truecrypt1_0 failed!
invalid argument command failed.

Ok is the truecrypt installation bad
Is the encrypted volume bad or non usable on the this new computer
Is it 12.10 causing the problem
is it the computer and this new screwed up UEFI secure boot causing the problem

So do we still have to edit the whitelist and if so where is it now?
Anybody know how to get truecrypt running correctly.
I got business data I need to retrieve!
Thanks
hi
1. i don't think so
2. i don't think so
3. yes - your message told me that the "ioctl" request for the device is not defined in the 
    system or have changed ( i don't think so).
    if you are confirmed with the bash you can try to trace the process wich want's to 
    open the volume with: strace -f  -o blablu -e trace=ioctl -p PID of the process
   to see the argument what is
    given to the call (did your software comes with some own header files) . post the blablu file it's an text file. i'll have a look at it.
    there are no secure data inside because only the ioctl calls are traced.
cheers

---

### Post by DD4lifeusmc on 2012-12-28
> **rnerwein said:**
> hi
1. i don't think so
2. i don't think so
3. yes - your message told me that the "ioctl" request for the device is not defined in the 
    system or have changed ( i don't think so).
    if you are confirmed with the bash you can try to trace the process wich want's to 
    open the volume with: strace -f  -o blablu -e trace=ioctl -p PID of the process
   to see the argument what is
    given to the call (did your software comes with some own header files) . post the blablu file it's an text file. i'll have a look at it.
    there are no secure data inside because only the ioctl calls are traced.
cheers
I think I know why the IOCTL error. The old hard drive was NTFS this new one was only fat32. The truecrypt vol is 5.4 gig. fat32 can not handle a file bigger than 4gig.
However. my main problem is where is the whitelist file at in  12.10. As Truecrypt icon is not automatically in the system tray.
So need to edite the whitelist config. But can't find it with dconfg  editor.

---

### Post by DD4lifeusmc on 2013-01-19
turns out had a bad disk copy of the true crypt files because of the other computer I copied them from.
As far as truecrypt goes.
Ubuntu or truecrypt made another change in how they communicate.
No longer have to edit the whitelist.
Open true crypt mount your container.
Then either click exit the window, or just click a different window.
Come back as needed or click the main truecrypt icon to bring up the T.C window again.
You can close the main T.C. in launcher and leave containers open.
Reopen the main T.C. in the dash and any container left open is still mounted.

---

