---
title: "how do you reinstall windows, error unknown filesystem grub error"
date: 2013-08-18
forum: General Help
---

### Post by FenrirXIII on 2013-08-18
Hello,

We have a Dell XPS ONE (A2010) at home and my parents main computer. It was pre-installed with Windows Vista and for a while it works... but the HDD bloats up and never deletes any file (even if its permanent delete). It came to a point that the HDD said it was too full and we weren't able to save or open anything.

So, I install Ubuntu 12.04LTS 32-bit.

For a while it works like a charm but as months went on it had a hard time trying to boot:

Sometimes it boot for 10 minutes, sometimes an hour
Sometimes it boots and then ask to press a certain key to repair or skip
Sometimes it boots then says hd0 not found grub rescue

For a while they kinda tolerated it, but they ask me if they can revert back to Windows... i mean, it's their right, that's their computer.

So i put in my Window 7 disc.

I deleted the partition and format to NTSC i tried installing it.

thing is, I didnt know that I first have to Click on Repair Windows.
After I click it, and it tried to install, Windows says I cant because there some error so i have to restart the computer

then after that: it gave me a new error:

error: unknown filesystem
grub rescue>

now it wont let me boot via Windows 7 CD

what do i need to do?

---

### Post by VMC on 2013-08-18
Change your BIOS so the booting order is CD/DVD first, then hard drive.

edit: when it boots, push F2, F10 or F12. It should show the correct key to use.

---

### Post by FenrirXIII on 2013-08-19
did what you told me and it work... thing is, i figured the HDD fried because of the heat... 80~100 degree Fahrenheit around my area... and to top it of the said computer as an all-in-one computer from ages ago... i was able to fix it by replacing the HDD and well fresh install,.. so far so good. and my dad, told me he rather keep the Ubuntu instead of Window 7. I put it in 2D mode so it doesnt use much resources... now the only thing that im worried about that this thing could happen again... anyway to prevent this without damaging my wallet? psensor says that the computer temp reached 58 degree Celsius (thats pretty damn hot) but otherwise when touched it seem colder than it used to be? i've heard that the psensor is buggy and sometimes increases the temperature... so im going to delete that on the morrow. any other reliable app to measure temperature? or any other tips to keep the computer cool? DELL XPS ONE A2010

otherwise ill mark this as solve! thanks community!

---

### Post by VMC on 2013-08-19
After looking at some pictures of the motherboard, there are a couple of small fans inside. #1, make sure their running, and too clean out any air ducts that you can access.

In the past, my Dell's access to the motherboard was easy, so I used compressed air to blow out all dust and cleaned the fan blades for good measure. It appears you pc may be harder to access.

---

