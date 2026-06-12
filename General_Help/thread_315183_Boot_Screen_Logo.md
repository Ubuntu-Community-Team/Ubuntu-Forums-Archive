---
title: "Boot Screen Logo"
date: 2006-12-08
forum: General Help
---

### Post by antisho on 2006-12-08
OK, well, no one seems to want to help me with anything, so I'll try an easy one.

The Ubuntu boot screen (that is, after grub and before login) shows a Kubuntu logo. How can I change it back to the Ubuntu logo?

Incidentally, apparently in Edgy all the text in the boot screen went away. Any way to get it back?

---

### Post by Dr. Nick on 2006-12-08
Try the link I posted [here]("http://ubuntuforums.org/showthread.php?t=220132"), Yes the text did dissapear, I am not sure how to get it back, but IIRC it has been scheduled to reappear when Fiesty comes out( but dont quote me on that)

---

### Post by strabes on 2006-12-08
Yeah you should just have to issue:
```
sudo update-alternatives --config usplash-artwork.so
sudo dpkg-reconfigure linux-image-`uname -r`
```

They removed the text on the bootsplash image to make it less scary for new users. If you don't want to see any bootsplash you could do ```
sudo apt-get remove usplash
```

That would be really ugly though. I suppose if there was some way you could get the old .so file from 6.06 you could just put it in /usr/lib/usplash and then select it with the 1st command I pasted above.

---

### Post by Ramses de Norre on 2006-12-08
```
sudo update-alternatives --config usplash-artwork.so
sudo dpkg-reconfigure linux-image-`uname -r`
sudo gedit /boot/grub/menu.lst
```

For the first command: choose the ubuntu one (I think it's called default).
Third: this will give you a file to edit, look in the "commented" part of the file for a line starting with ```
#defoptions
``` this line probably contains the word "quiet", remove that to get text in usplash.
If it's not on the defoptions line it will be somewhere in the neighborhood (I'm not sure, I removed it a wile ago..).
Then to reflect the change you made run this:
```
sudo update-grub
```

---

### Post by antisho on 2006-12-09
Thanks for the help! It should work now, I'll reboot soon to check. :)

---

