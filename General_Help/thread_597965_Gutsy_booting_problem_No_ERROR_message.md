---
title: "Gutsy booting problem: No ERROR message???"
date: 2007-10-30
forum: General Help
---

### Post by mike_302 on 2007-10-30
When I get to the Grub, I select the gutsy OS, it qucikly does its little line at the bottom (the one about keymapping or something???) no errors, and then the screen goes black... No boot screen. The loading light appears to be flashing fairly rapidly after 5 seconds, as if it were loading something, but nothing will happen... period. You could wait 5 minutes it wouldnt change. HERE'S THE CATCH!
If i wait about 30 seocnds, then hit ctrl+alt+f1 (and only f1, not f7) it brigns up a few lines of command, all beginning with "kinit" but the only one I could read and remember was "kinit: no resume image, doing normal boot" then gutsy loads... and everything is fine and dandy from there on out. But CLEARLY you guys can see that this is not what it should be doing. Can anyone troubleshoot this (assume I'm a linux newb cuase in reality that s what I am... although I know my way around Windows pretty well, but thats not going to do much here)

PLEASE, if you are going to suggest adding lines to anything, give me atleast FAIRLY detailed instructions on how to do it.

Thanks in advance!

---

### Post by thelocust on 2007-10-30
What happens when you boot in "recovery mode"?

---

### Post by mike_302 on 2007-10-30
It loads the command line i guess? I never booted into it before this problem, so I don't know wht it SHOULD be doing. ALTHOUGH! please note, it loaded that command line when I forgot I had only hibernate my windows session so it gave an error saying i still had Windows hibernated in the RAM. I have not tried since.

---

### Post by mike_302 on 2007-10-31
OK. now this is getting silly. I'm very sorry if I sound annoyed but I am... I've asked MANY questions on here, several of which I'v had to just ignore because I was not getting anoter answer. Now, on this one, I REALLY need to resolve this and: I DID get help in a previous thread, but when I simply asked how to go about doing the thing you said, that was it... No more replies.

All I am asking for here is a little help to get Ubuntu working properly. Some of you already had answers in a previous thread, but as I said, I am not a Linux pro so I wasn't totally sure how to go about doing that. Can SOMEONE please explain ?

---

### Post by mrojas73 on 2007-10-31
can you press ESC right after the bios screen goes away and then hit "e" on the generic kernel and on the second line hit "e" again.  At the end of the line right next to splash type noapic.  Hit enter and "b" without the quotes on all of them.

If that allows you to boot you need to modify your /boot/grub/menu.lst.

I don't know if your problem is related to this but it sounds like it could be.

Good luck.

---

### Post by mike_302 on 2007-11-03
It still isn't booting. I did exactly as you said.

but as I said, pressing ctrl+alt+f1 still makes it boot, albeit after a bunch of lines saying "no resume image", booting normal ...

Anyone else? This is gutsy64

---

