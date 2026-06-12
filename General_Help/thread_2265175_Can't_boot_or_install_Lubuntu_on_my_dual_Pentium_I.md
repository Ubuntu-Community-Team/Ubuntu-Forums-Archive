---
title: "Can't boot or install Lubuntu on my dual Pentium III computer"
date: 2015-02-13
forum: General Help
---

### Post by cody16 on 2015-02-13
I can't install or boot a live session of lubuntu 14.10 from my usb flash drive due to a panic.
 I know next to nothing about these things.
 It's a dual Pentium III desktop with two 1.4 ghz CPUs.
It has 3.5 gigs of RAM
 My Graphics card is a Geforce 7600GS.
I tried to burn Lubuntu to a DVD but it gives the same panic.
I used the latest version of universal usb installer to write Lubuntu to the flash drive.
I tried to install ubuntu, but apparently it doesn't support i686 anymore.

I just want to install a lightweight linux distro to play Frets On Fire which is a python based guitar hero clone. 

Heres a picture of the panic. [URL="https://www.dropbox.com/s/g4k9cafiwpmubdm/DSCN0007.JPG?dl=0"]
[/URL][https://www.dropbox.com/s/g4k9cafiwpmubdm/DSCN0007.JPG?dl=0](https://www.dropbox.com/s/g4k9cafiwpmubdm/DSCN0007.JPG?dl=0)

---

### Post by Bucky Ball on 2015-02-13
When at the screen with the options 'Try Lubuntu' and 'Install Lubuntu', could you hit F6 and choose 'nomodeset' then proceed? Any difference? Could be a graphics issue.

---

### Post by sudodus on 2015-02-13
I would suggest that you try an older and more polished version of Lubuntu, that is still supported, ***Lubuntu 14.04.1 LTS***. If you have problems, try some [boot options]("https://help.ubuntu.com/community/BootOptions"), for example **nomodeset** and a proprietary driver.

Maybe you need an even older version. In that case I suggest a community re-spin based on Ubuntu 12.04 LTS, for example ***Bodhi*** or ***LXLE***, or [Precise Gnome Classic Tweak]("https://help.ubuntu.com/community/PreciseGnomeClassicTweaks").

If still no luck, try an ultra light linux distro, for example ***Tiny Core***, ***Wary Puppy*** or ***TahrPup***.

---

### Post by cody16 on 2015-02-13
Pressing f6 just refreshes the options. It doesn't do anything. The options are press enter to select or press tab for advanced options. I pressed tab and I added "nomodeset" to the end, but I'm not sure if I was supposed to add a space first, so the syntax might be wrong. Now this is all that I see.

[https://www.dropbox.com/s/jwl3ghothbv8c84/DSCN0008.JPG?dl=0](https://www.dropbox.com/s/jwl3ghothbv8c84/DSCN0008.JPG?dl=0)

---

### Post by cody16 on 2015-02-13
I require hardware rendering and the ability to easily install all of the dependencies for the game. I want a software manager that is up to date. I installed the same version of lubuntu on a 700 mhz Pentium III laptop with 512mb of ram just the other day and it worked fine.

---

### Post by sudodus on 2015-02-13
I suggest that you try something older, that is more likely to work with your old hardware.

But you might as well try some more with boot options, one or more at the same time. Please read more about the details at the following link

[Boot options]("https://help.ubuntu.com/community/BootOptions")

---

### Post by Bucky Ball on 2015-02-13
No space before nomodeset, but I guess we could call it progress, of a sort. That appears to be a totally different error you're getting now.

---

### Post by cody16 on 2015-02-13
But, I can run the same version of lubuntu on a 700mhz laptop with an 8mb integrated video card and 512mb of ram. Surely I should be able to boot just fine. I don't understand?

---

### Post by Bucky Ball on 2015-02-13
Different hardware one would think. That changes things. It's obviously not liking something about the hardware. Did you install from the same install media on the other machine?

---

### Post by cody16 on 2015-02-13
Actually I figured it out. I needed a space and I needed quotation marks like this "nomodeset". But now it seems to be stuck on the the lubuntu loading screen with no flash drive activity.

---

### Post by sudodus on 2015-02-13
You should ***not*** use quotation marks like this "nomodeset".

---

### Post by Bucky Ball on 2015-02-13
> **sudodus said:**
> You should ***not*** use quotation marks like this "nomodeset".

Good pick up. Just this:

nomodeset

;)

---

### Post by mörgæs on 2015-02-13
Dual Pentium 3, that's some interesting hardware. 

Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags. Can be done from a live boot using any kind of Buntu.

---

### Post by cody16 on 2015-02-13
I pressed the escape key while it was locked in the loading screen and it revealed an input output error. 

[https://www.dropbox.com/s/7181h5bm5vxjqi8/DSCN0010.MOV?dl=0](https://www.dropbox.com/s/7181h5bm5vxjqi8/DSCN0010.MOV?dl=0)

---

### Post by cody16 on 2015-02-13
Not using quotation marks gives the same result as not typing nomodeset at all.

---

### Post by Bucky Ball on 2015-02-13
Watched the vid up until you said you typed in a quotation mark. NO quotation mark around 'nomodeset'. Just type in:

nodmodeset

Ah, you ninja-ed me with your last post. I see. Quotations or not makes no diff. I'll keep watching and see if I get any clues. ;)

Have you tried just booting from a DVD as the install media? No idea about the boot manager you're using to force a boot from USB, but maybe that's playing a part in the lack of success.

---

### Post by cody16 on 2015-02-13
Well It finally works, but it wasn't easy. I used Universal Usb Installer along with a usb to ide adaptor to install the lubuntu installer to a separate hard drive. Then I installed that hard drive inside of the Pentium III and I booted from it. Finally I was able to begin the installation of lubuntu onto my intended hard drive without any issue. I still have no idea why I couldn't install from the flash drive or a dvd.

Sometimes life is hard.

How do I mark this as solved?

---

### Post by mörgæs on 2015-02-13
Did you read Bucky's signature?

---

### Post by Bucky Ball on 2015-02-13
Good news. Yea, bit of a mystery as to why you couldn't get Lubuntu installed in the regular fashion via USB, but good thinking. Got there in the end. Enjoy and good luck. ;)

---

### Post by sudodus on 2015-02-13
> **Bucky Ball said:**
> Good news. Yea, bit of a mystery as to why you couldn't get Lubuntu installed in the regular fashion via USB, but good thinking. Got there in the end. Enjoy and good luck. ;)

+1

Congratulations, and welcome back with a new thread, if you need help with something else :KS

---

