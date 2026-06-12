---
title: "Major problem with Integrated NVIDIA GeForce 7025 graphics card ."
date: 2013-03-04
forum: General Help
---

### Post by Jamstercool on 2013-03-04
Hi,

I've recently installed Ubuntu 12.10.Coming from win7, which luckily I decided to keep on the partition, just in case the ubuntu installation wasn't quite as solid as I'd hoped .

I'd been having a few problems since install.One major issue being when I resumed my pc, Once I'd logged in all I saw was a black screen with a mouse pointer.Only I complete restart got the screen back. .So I searched the ubuntu software installer and their was a current X.org or similar NVIDIA driver ( the one believe I had installed ) and another X.org or similar driver . So I decided to try and install the other driver . When I restarted my machine I was presented with a window saying that my screen was currently in a low resolution and gave several options ,non of which has got me back onto the unbuntu desktop,so I could re-install the less buggy driver again . 

The little reasearch I've done,  seems to show there is a  common problem with NVIDIA GeForce graphics cards on ubuntu . 

Please can I have the straight facts! I need a stable computer for my study!.Is their a definite work around?.Or because of my integrated graphics card should I stay with win7?.All I want is a screen that comes on when it should :-) .

Ubuntu 12.10 64bit
NVIDIA[SUP]®[/SUP] GeForce 7025 graphics (integrated)

---

### Post by ManamiVixen on 2013-03-04
You need to "sudo apt-get install nvidia-current" on you PC. As of late though, any card older than the GeForce 8000 series dosen't work well on Ubuntu 12.10. You can try 12.04 if you cant get the card working.

---

### Post by Jamstercool on 2013-03-04
Ok thanks for the help it helped me get back to the ubuntu desktop .Though intillially all I could see was the desktop with no taskbar .I right clicked to get to screen settings, the graphics driver had set my 21" desktop screen for a laptop screen, there was no alternative setting . 
I installed The 'X.org X server driver' works ok . ( The one with the blank screen on resume bug ) .Though the way I work the suspend feature is a good power saving feature that I'd really like to use .
Can anyone recoomendend me a unbuntu friendly graphics card .Some graphics card that is relatively in the Budget range and has at least enough power as the Geforce GeForce 7025 .Alternatively is their a linux distribution that will include drivers that work for this card ? .

Thanks for the help :-)

---

