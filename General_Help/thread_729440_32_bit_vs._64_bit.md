---
title: "32 bit vs. 64 bit"
date: 2008-03-19
forum: General Help
---

### Post by mattack on 2008-03-19
I'm getting a new computer in a few days... It's a Dell XPS 420 Mini-Tower: Intel Core 2 Q6600 Quad-Core (8MB L2 cache,2.4GHz,1066FSB), 3 GB DDR2 SDRAM 667MHz
I mostly use my computer for email, web surfing, minor photo editing, and listening to music, though I plan to start watching movies, and maybe even ripping a few DVDs. I regularly rip CDs that I own. I'm also learning Perl and plan to do a little bit of programming. I'm not a hardcore gamer, I don't do 3D modeling, etc...
I've done a little reading about 64 bit and it's lack of some key plug-ins for the web (Flash and Java). It seems there are ways to get them working, though some have varying results, especially with sound.
I really like my computer to "just work" without a lot of hassle, one of the reasons I like Ubuntu so much.
What I'm wondering is, are there any advantages to installing 64 bit Ubuntu? Will there be any performance hit by going with 32 bit vs. 64 bit? Is there anything else I should know?

---

### Post by logos34 on 2008-03-19
Head over to the 64-bit forum...

[http://ubuntuforums.org/showthread.php?t=368607](http://ubuntuforums.org/showthread.php?t=368607)

---

### Post by Pres-Gas on 2008-03-19
I would say the biggest advantage to using 64 bit is that you would be able to use more than 4 gigs of ram.  Since you only have 3, that is not an issue for you.  If you plan in the near future to get 4 gigs or more, you should consider 64 bit.

I recently tested the alpha 6 of Hardy, though, and found that I was able to get both Flash and Java working on it.  I will take a guess and say that it was using the 32 bit version of Firefox, but am not sure.  Can anyone confirm that?  In any case, your basic browsing should be fine as far as Flash and Java.  Since Hardy is using Firefox 3 by default, the addons are not all there, but I did see Firefox 2 in the repos...so you can still install that for that addon that you MUST have or you would die.

---

### Post by Victormd on 2008-03-19
I've had both systems installed on the same machine and 64bits makes a difference (that I noticed) when working with graphics (I had Photoshop installed through WINE and used Blender) and noticed a difference between both platforms. Also, it's been reported that 64bits is better for (CD/DVD) ripping than 32 bits.  However, I must point out that with your hardware configuration, you won't have any problems with speed no matter how you go.

I was able to get flash and java working on my 64bit system with no problem whatsoever... but my experience with 32bits was much simpler.

MHO, based on your hardware and your desire to "simply work" is to stick to the 32bit version...

---

### Post by Victormd on 2008-03-19
> **Pres-Gas said:**
> I recently tested the alpha 6 of Gusy, though, and found that I was able to get both Flash and Java working on it.  I will take a guess and say that it was using the 32 bit version of Firefox, but am not sure.  Can anyone confirm that?

I got it to work using the 32bit version of Firefox (the first time I installed 64bits) and with another script that I found on the forum... kind of a black-box to me so can't say if it was using 32bit firefox or not. Either way, both worked fine.

---

### Post by NightwishFan on 2008-03-19
<-- 64-bit user

It is fast. Flash and etc works on 64-bit firefox/konqueror now.

---

### Post by sdennie on 2008-03-19
I would recommend the 32bit version.  I have a machine with 4G of RAM and went with the AMD64 version of Ubuntu for a while.  It sounds silly but, there is security in numbers in this case.  The 32bit version of Ubuntu is more widely used and, as such, better supported.  People will argue with me on this and that's fine but, I noticed no real speedup from using a 64bit OS and have found fundamental (unfortunately fundamental to be sure) things like Flash are much more reliable on a 32bit system.

I actually run a custom 32bit kernel with PAE enabled (which, surprisingly, gives me more available RAM of my 4G than the 64bit kernel did) and have found the whole experience much more pleasant than using the AMD64 distribution.

---

### Post by NightwishFan on 2008-03-19
I do not use it for the ram. I only have 895mb. When it takes me 22 seconds rather than 1m12s to encode audio then something is done right. I also like that my processor is always stepped to 1ghz a core since it takes very little of my cpu to do most things.

---

### Post by Rome.konig on 2008-03-19
i would say go with 64 bit, 32 bit systems are a decade old and probably reached its old age ready to kick the bucket. you can't go wrong with 64, you can even install 32-bit platforms on 64-bit computers so why not go with the new.

---

### Post by PmDematagoda on 2008-03-19
> **Rome.konig said:**
> i would say go with 64 bit, 32 bit systems are a decade old and probably reached its old age ready to kick the bucket. you can't go wrong with 64, **you can even install 32-bit platforms on 64-bit computers so why not go with the new**.

Sorry, did you say can or can't?

---

