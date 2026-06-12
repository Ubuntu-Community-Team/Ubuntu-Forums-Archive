---
title: "Editting Grub Boot loader"
date: 2007-05-15
forum: General Help
---

### Post by Freaky_Llama on 2007-05-15
Its a little bit of a trick question, and don't know if it can be done.

On 7.04, or anything that uses Legacy grub, is there a way to kill the text at the bottom of the screen that's under the OS selection window (you know, where it tells you pretty much to "press enter to boot the selected OS".

It kinda defeats the use of pretty splash images to have it there, and I'd rather use a splashimage.


Thanks to all and sorry if I it's been answered. I tried to search, but for some reason, my companies internet blocks the search page, but the forums are ok.

---

### Post by ayenack on 2007-05-15
You can edit your grub by typing this in terminal

sudo gedit /boot/grub/menu.lst

Be careful with this it's easy to mess up your system so if you don't know what you're doing might not be a good idea to mess with it.

Best of luck. ayenack.

---

### Post by Freaky_Llama on 2007-05-16
Thanks for getting back to me. In menu.lst isn't where that text is held.

I'm talking about where it shows you what keys to press to edit the boot options etc. I want to remove those words because A) I know what to do there and B) It covers the 'pretty graphics' (?maybe?) on the bottom of the screen.

The only thing that I found thats any bit related in menu.lst is the hidden menu option.

---

### Post by mikewhatever on 2007-05-16
I think you'll find this page very useful [http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by ayenack on 2007-05-16
Not sure if this will work but have you tried hiding menu hidemenu it hides the menu by default you should still see the splash screen though I think. If you want to see the menu press esc.

Good luck ayenack.

---

### Post by Freaky_Llama on 2007-05-16
Thanks mikewhatever, that made for a good read, but the info I seek isn't in there. I went on to read the Grub manual, and couldn't find it. I'm fairly certain that what I'm looking to edit is in (in my case) the reiserfs_stage1_5 file. Oh well. I was hoping to at least personalize the Grub screen. 

I'll keep looking, but now for a way to edit that stage1_5 file.

ayenack - I tried hidden menu. All it does is hide the complete screen and just offer the countdown in simple white on black. Pressing ESC brings you to the splash screen. Its clean, and it works, just not fully what I'm looking for.

---

### Post by ayenack on 2007-05-16
Yes, just found that out for myself. I don't think you can do this without some serious hacking, beyond me I'm afraid. If you do work out how to do it post it here so I can have a go myself. Going to keep trying but not sure this is possible if I find a way I'll post back.

ayenack.

---

