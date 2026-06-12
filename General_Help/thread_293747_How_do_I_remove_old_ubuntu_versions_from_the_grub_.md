---
title: "How do I remove old ubuntu versions from the grub menu?"
date: 2006-11-05
forum: General Help
---

### Post by Jasper Houtman on 2006-11-05
I started using ubuntu breezy and I'm now using edgy. In the time I've used ubuntu the boot list in grub has been growing slowly. 

How do I reduce it back to a few options? Can I safely remove these old kernel versions? And is there a way to stop grub from making such a long list?

Thanks in advance for your help.

---

### Post by bulldog on 2006-11-05
Yes you can remove those lines or comment them out.

You can also uninstall the kernels you don't use anymore with synaptic.
Search for linux-image and remove the obsolete ones.

Then sudo update-grub and they should be delete from menu.lst.

---

### Post by pdub on 2006-11-05
Make a backup first,

**sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak**

Then

**sudo gedit /boot/grub/menu.lst**

Remove any of the items that you no longer want in the menu, then save and exit.

---

### Post by testube_babies on 2006-11-05
> **pdub said:**
> Make a backup first,

**sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak**

Then

**sudo gedit /boot/grub/menu.lst**

Remove any of the items that you no longer want in the menu, then save and exit.


It usually won't make a difference with gedit, but since it is a graphical program it would be safer to use **gksudo** instead of sudo.  That is, ```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak
gksudo gedit /boot/grub/menu.lst
```

---

### Post by scooper on 2006-11-05
Be careful with simply editing /boot/grub/menu.lst, it's automatically generated based on the kernels found in /boot.  To really get rid of them you need to get rid of the kernels from /boot.  The "right" way is to uninstall the obsolete kernels with apt or synaptic.  The sleazy way is to simply move or remove the kernels you don't need from /boot and then run "sudo update-grub".  Sometimes I get confused trying to find the kernels in synaptic and resort to the sleazy method by moving what I am sure I don't need to a trash bin.

Remember, if you do it manually you have to run update-grub to see the change.

---

### Post by Tomosaur on 2006-11-06
This isn't correct. The 'proper' way to stop grub showing your old kernels is to tell it to only show 1, or 2, or whatever amount you want it to show. There is a line in /boot/grub/menu.lst which will allow you to change this. It says '#howmany=all'. Don't uncomment it, just alter the 'all' to an integer. You should then run 'sudo update-grub' at the command line to get your grub menu trimmed. Restart, and it should be fine.

You **can** just remove the old kernels from your machine altogether, but having just the one kernel is probably a bad idea if anything fucks up.

---

### Post by Jasper Houtman on 2006-11-06
Thanks for all the replies!

I've decided to just limit the number off entries in the grub list for now, then when I have more time this weekend I'll check out removing some off the older  ones in Synaptic.

---

