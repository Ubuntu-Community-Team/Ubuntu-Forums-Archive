---
title: "Ubuntu stuck on greeter loading"
date: 2017-05-28
forum: General Help
---

### Post by liberator48 on 2017-05-28
So i was stupid and forced edited the /etc/lightdm/lightdm.conf because i wanted to frickin enable password to be required to login on my own account.
What happened was that the text in the .conf file got erased and I opened the file with admin rights in Plume and to the best of my knowledge put back the text that was there before.

So once i restart now it gets stuck on the Ubuntu MATE logo with the 5 dots under it that change color when it loads the desktop/login screen.

My question is, how do i fix the lightdm.conf file, so that it can log me in again?
I assume i need to fix it with command line somehow as it won't load me in to desktop :(
Help please!

---

### Post by liberator48 on 2017-05-28
Solved it by opening command line when it got stuck and concatenating the string [SeatDefault] at the beginning of the lightdm.conf file... That was easy.

---

