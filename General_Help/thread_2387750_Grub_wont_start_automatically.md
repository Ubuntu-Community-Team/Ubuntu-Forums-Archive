---
title: "Grub wont start automatically"
date: 2018-03-23
forum: General Help
---

### Post by usera. on 2018-03-23
Hey, 

I have Ubuntu running alongside Windows and I never had too many problems... few days ago I started my computer and instead of grub, windows is immediately running as the computer turns on. I didn't do any updates, it just suddenly happened. 
I can still run Ubuntu if I go to the Windows boot manager but that is very unpractical since I never really use Windows.
any Ideas why it happened and how I can solve it? 

Thanks!

---

### Post by ajgreeny on 2018-03-23
A similar sounding problem was posted a few days ago at [https://ubuntuforums.org/showthread.php?t=2387230&p=13748842&viewfull=1#post13748842](https://ubuntuforums.org/showthread.php?t=2387230&p=13748842&viewfull=1#post13748842)

You do not really give us enough info to know if the problem really is the same but have a look through the information there and see if anything rings bells.

Come back again if your problem is totally different (or appears to be) and we'll try to help further.

---

### Post by yancek on 2018-03-23
Apparently, you have an EFI install.  Can you verify that?  Which version of windows are you using?  Which version of Ubuntu?  If no changes of any kind were made or no major windows updates, something like that would not be expected with the possible exception of hardware problems.  If you do have an EFI install, boot Ubuntu and run the following command which will show the boot order for EFI:

```
sudo efibootmgr
```

---

