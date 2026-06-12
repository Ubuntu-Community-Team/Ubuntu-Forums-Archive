---
title: "sudo limitations?"
date: 2005-10-26
forum: General Help
---

### Post by Randy Sparks on 2005-10-26
I wanted to copy across my Windows fonts from my NTFS Windows partition. So I used the disk tool under the System menu to mount the NTFS partition and then then issued the following console command:
```

sudo cp /mnt/Windows/fonts/*.ttf /usr/system/fonts
```

I had to sudo it because the mount only had root permissoins. But I got an error message saying "cannot stat". 

Everything is correct, including the path. The problem appears to be that sudo doesn't give the cp command the required permissions to enter the directory. IN other words, on the console at least, it appears sudo isn't a direct swap-in for switching to the root account (ie su), as with other Linux dustros.

If I type "sudo nautilus /mnt/Windows/fonts", I see the contents of the directory just fine in a file browser window.

Is this a limitation of sudo or is there another way of crafting the command to make this work? I realise that enabling the root account will also do the trick but I'm curious to know if it can be done via sudo. :confused: 

ps. PLEASE don't reply telling me to apt-get install the MS Core Fonts. This question isn't about installing fonts. It's about making proper use of the sudo command.

---

### Post by PriceChild on 2005-10-26
Try using "sudo su -", then enter your password, and finally try the command without the sudo.

Not used to linux at all, so please don't flame me if it's a silly idea and won't change a thing, but it's helped me!

((P.S. that last comment has filled you with confidece hasn't it ;) ))

---

### Post by sanjose on 2005-10-26
how about this

**sudo cp /mnt/Windows/fonts/*.ttf /usr/share/fonts**

---

