---
title: "Netbeans 6.0 on Gutsy AMD64 uses too much RAM!"
date: 2008-02-01
forum: General Help
---

### Post by phibit on 2008-02-01
Hello,

 Let me first start off by saying that I am not generally an IDE user, but Netbeans seems like a nice option for someone who needs to make GUIs in swing.

  I recently installed netbeans 6.0 on my Gutsy AMD64 machine. I have 1 GB of RAM, which has been more than sufficient for anything I've had to do on Ubuntu.

  Then I opened Netbeans 6.0, and it occupies what I find to be an unbelievable 400+ MB of RAM! This is more than what Half-Life2 typically uses. Since Netbeans 6.0 was announced to have some major improvements over v5.0 in terms of memory management/usage, I suspect my configuration is somehow wrong.

  Also, I know some other people who have installed Netbeans 6.0 on Ubuntu computers, but with Gusty 32 bit. They do not have the same memory problems, and this leads me to suspect the problem is x86_64 specific.

  Has anybody else had this issue, and know how to resolve it?

  For the moment I have read that disabling some plugins (Tools | Plugins) helps with startup time and decreases the memory footprint, but I can't get Netbeans to use less than 300 MB! For me this is far too much RAM, as I like to have other programs running while I work.

:confused: I'm at a loss.

  Admittedly, I was shortsighted enough to not install a linux swap partition when I installed Ubuntu, but I refuse to believe this is the reason for my problem, and maintain that 1GB should be enough to support my minimal linux setup.

  I'd love to hear some suggestions. Thanks.

---

### Post by ~LoKe on 2008-02-01
Are you sure this isn't just how Linux/Ubuntu manage RAM?  From what I've seen, Ubuntu likes to eat as much ram as possible and store it away until it's needed.

---

### Post by phibit on 2008-02-01
I agree that Ubuntu's memory management is sometimes poor/different. Still, from what I've read about Netbeans, the linux release of v.6 has been optimized to use as little memory as possible (like.. below 150 MB).

Still, it is a possibility, but I'd like to think there's something I can do about it :P

Plus, I've seen it running on ubuntu (x86) with just a 195 MB footprint... Mine just won't do the same :(

---

