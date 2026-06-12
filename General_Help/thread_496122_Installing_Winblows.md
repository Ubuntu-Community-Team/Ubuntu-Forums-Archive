---
title: "Installing Winblows"
date: 2007-07-08
forum: General Help
---

### Post by freexzai on 2007-07-08
Okay. I have been using Ubuntu since I quit playing Ultima Online. Well I really want to play again. My Computer isn't quite that great and Wine isn't an option(except after 8pm). 

250 gig HD that is my main HD partitioned 4 times. 50gig "/" 100 gig "/home" 100gig "/media" and 10gig swap

I have a second 40 gig HD that I used for a test space when I was trying out hardware configurations with Ubuntu that I now wish to use for a Faildows XP install(Oh UO how I can never quit you).

When I try and install Windows it wants to rewrite the boot tables I guess so it can try and take over my computer. DO NOT WANT! 

Anyways my question is will it be safe to delete my swap so it can write its bullcrap?

My second question is why is this such a pain in the ***?

Are there any other options I am not thinking of? 

And lastly did I miss the howto on this and should be modded down redundant?

---

### Post by AndyCooll on 2007-07-08
The bootom line is Winderz doesn't make it easy to dual-boot. 

You are always best installing Winderz first. See the link in my signature for an excellent dual-boot tutorial.


:cool:

---

### Post by Vajra Vrtti on 2007-07-08
> When I try and install Windows it wants to rewrite the boot tables I guess so it can try and take over my computer. DO NOT WANT!There is no way to keep the Windows installation from doing that. What you have to do is to install Windows (in the second HD, I guess)  and then [restore grub]("http://ubuntuforums.org/showthread.php?t=224351").

---

### Post by freexzai on 2007-07-08
Okay. Well I got clever. That was stupid. I pull out the 250. Make the 40 Primary. Install Windows. Make the 40 Secondary. Put the 250 back in. Explode my computer.

If I put the 40 as primary agian it works fine. If I use the 250 by it self or with the 40 as secondary I get a disk check error after I get past grub. It give me some error fixing terminal. If I "shutdown -r now" it goes to gbm. When I try and log in it says home cant be found. and logs me back out.

---

### Post by Vajra Vrtti on 2007-07-08
That's strange. I would expect some problems accessing 40 after it was changed to secondary but, if 250 wasn't changed in the installation, why isn't it working anymore?

---

### Post by freexzai on 2007-07-08
Everything is better and now working.

I got windows installed. I got Ubuntu installed and I got much less of a headache. 

Just gotta deal with my GF and life will be great.

I had a Error 8 in case anyone is wondering. To fix it I just reinstalled Ubuntu. 

That is why I keep my /home on a different partition.

---

