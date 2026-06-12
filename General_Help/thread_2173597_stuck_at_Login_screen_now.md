---
title: "stuck at Login screen now"
date: 2013-09-10
forum: General Help
---

### Post by BlauFusion on 2013-09-10
I am using Xubuntu 13.04 and I am stuck on the login screen.
I am not sure if this is a GRUB window?
I am past the choice of which operating system to choose, and I have the options of my main account or guest or other, and the choice of Xfce session or Xubuntu session.

I think that I must have messed up my /etc/lightdm/lightdm.conf file by trying to autostart my main account adding my username and timeout to the file.

Now, when I press Login for my main account, the screen goes black for a moment and returns me to the same login screen. It does not matter if I choose the Xfce session or the Xubuntu session.
The guest login seems to work normally, but I don't think I can edit that file as guest.

If anyone could help that would really save my bacon. The stuff on this computer is too valuable to me for me to lose it.

Thanks very much...

---

### Post by grahammechanical on 2013-09-10
What you are seeing is not Grub. I am not sure if Xubuntu uses the Lightdm display manager but it is the log in window. There is a simplier way of making Xubuntu auto login than editing that file. This is what I suggest. I do not know if it will work. Revert the changes you made to that file.

At the Grub boot menu select Recovery Mode. At the Recovery Menu select Network. That will set up a connection to the router and will also put the file system in read/write mode which you will need next.

When back at the Recovery Menu select Root. You will now be at a Root command prompt. Type
```
 nano /etc/lightdm/lightdm.conf
```

that should open the Nano text editor with lightdm.conf ready to be edited. Revert the changes. Press Ctrl+W to write-out or save. You may need to give the correct file name and path. Then press Cntrl+X to Exit.

At the Root prompt type

```
exit
```

to get back to the Recovery Menu and select Resume. Fingers crossed you get to a desktop. 

Regards.

---

### Post by BlauFusion on 2013-09-10
Ah, that was a lifesaver, thanks. 
I had tried "dropping into root" but of course it was not r/w until starting the network. 
I didn't try that since I didn't **need **the network.

If anybody cares, it was my .profile that was actually messed up. :P

Thanks a billion!

---

