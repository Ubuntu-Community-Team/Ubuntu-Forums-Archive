---
title: "Slow/Stall at  Startup"
date: 2007-01-24
forum: General Help
---

### Post by asnd16 on 2007-01-24
I did an automatic update yesterday and ever since Not sure if it was the update but something happened. 

Its as if Ubuntu stalls in the startup/boot  it takes almost five minutes to fully boot.  Anyway to check to see what its stalling on?  Or does anyone else have any issues in the past days with updates?

It stalls first at where the splash screen would be, then it takes forever to load my clear menu bar and the background. :guitar:

Another thing I did was add a network connection then I had issues getting the Networking app opened and was unable to open it all together. But for some reason today its fine, I back tracked and deleted the network connection and restarted and it still has issues.

---

### Post by gaebriel on 2007-01-24
Have you tried booting in recovery mode and noticed a difference. To see where it's hanging up at, edit your /boot/grub/menu.lst file. Remove the words "quiet" and "splash" from the kernel you want to boot from - typically the first in the list - and then you'll be able to see what happens on the screen as the system is booting up. 

I always remove these anyway since I prefer watching the system scroll through what it's doing. Also, if you have a 1024x768 monitor, you can add "vga=773" (1280x1024 - vga=775) to the end of the line you removed "quiet" and "splash" from and then it should be easier to watch the screen because the data won't fly by so quickly.

---

### Post by asnd16 on 2007-01-24
splashimage=(hd0,0)/boot/grub/splash.xpm.gz

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash rootflags=data=writeback
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single rootflags=data=writeback
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST



Anything look out of the ord?

---

### Post by gaebriel on 2007-01-25
Those lines look fine to me. But if you want to see where the system is hanging up, you'll want to edit the line that says "kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash rootflags=data=writeback" to "kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro rootflags=data=writeback". You can do it during bootup mode as well if you don't want to make the change permanent - just press Escape to load the menu, then follow the on-screen instructions to edit a line ... 

Wait a second. I just reread your original post and I may have misunderstood where it was failing before. Clarification: Does it load up to the login screen just fine and then only go extremely slow when it's loading the first splash screen after login? or does the system boot fine until just after the option to press 'Esc' and then go slowly when it loads the Ubuntu splash page immediately following that option?

---

### Post by Bagster on 2007-01-25
I have the same problem.....

My pc was working fine until i turned it on this morning, having installed updates yesterday.  Until then my system was running perfectly fine, booting quickly and generally behaving itself. Now it takes an age to fully start, with gaim only booting a good minute or so after when it used to. It is also generally unresponsive, with the terminal alone taking over 10 seconds to start. 
There are no rogue processes apparently running, no obvious cause on the problem.
If anyone could help, that would be brilliant - just let me know what info you need!

---

### Post by Bagster on 2007-01-25
Well the problems seems to have vanished.....
It all starts fine and now is totally responsive - and without a single software change. Very very odd........

---

### Post by asnd16 on 2007-01-25
> **gaebriel said:**
> Those lines look fine to me. But if you want to see where the system is hanging up, you'll want to edit the line that says "kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash rootflags=data=writeback" to "kernel /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro rootflags=data=writeback". You can do it during bootup mode as well if you don't want to make the change permanent - just press Escape to load the menu, then follow the on-screen instructions to edit a line ... 

Wait a second. I just reread your original post and I may have misunderstood where it was failing before. Clarification: Does it load up to the login screen just fine and then only go extremely slow when it's loading the first splash screen after login? or does the system boot fine until just after the option to press 'Esc' and then go slowly when it loads the Ubuntu splash page immediately following that option?

I still have the issue, I can get to the login screen fine but right after the login screen it still takes forever.  Its really getting on my nerves.    I want to veiw AFTER I log in.

---

### Post by asnd16 on 2007-01-27
ok how about this, How do I go about re-installing ubuntu? Do I just put in the install cd?

---

