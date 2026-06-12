---
title: "Asus N550JV won't boot 13.10 from DVD"
date: 2014-03-15
forum: General Help
---

### Post by eline.wiel on 2014-03-15
I recently bought an Asus N550JV laptop and my plan is to replace the HDD with an SSD and install Ubuntu on that. The purpose for which I have bought it does not allow me to use windows. Before I open it and replace the HDD I first wanted to make sure that it can boot Ubuntu from a DVD, and there the trouble starts.

First I get:
Could not open EFI\boot\fallback.efl : 14 Error: variable root isn't set

And then I see Grub, when I then try to boot from the DVD half of the time I get the same thing as in this Ask Ubuntu tread.
[http://askubuntu.com/questions/377903/errors-during-ubuntu-13-10-installation](http://askubuntu.com/questions/377903/errors-during-ubuntu-13-10-installation)
I think this is some random DVD error and not related to my further problems (because in those cases I don't hear the DVD drive spinning up). The interesting things happen when it gets past that part.

At first I just got the purple screen with the logo and the white blobs that get colored, the DVD drive spins and they the row of dots gets colored a few times and then they all turn red and the system hangs. One time I pulled out the DVD, and I got presented with some errors which I can not type, so I took some pictures of the screen, they can be seen in 1 to 3 in this [http://imgur.com/a/5pm0p](http://imgur.com/a/5pm0p) imgur album.

After this I searched around a little and decided to try nomodeset as an option. This appears to get me a little further, I now get text after the logo which can be seen in the last picture. It also reacts to the shutdown button when it is stuck at "Stopping System V runlevel compatibility.

What is going on here, and more important, how do I solve it?

If I can not solve this I am basically stuck with an almost 1000 euro brick, windows 8 is useless to me.

Edit: I rememberd I have mint 16 on an USB stick laying around, that one gives a blank screen.
Edit2: Disabeling secure boot resulted in some half mint boot, it only gives a dekstop with 3 icons now.

---

