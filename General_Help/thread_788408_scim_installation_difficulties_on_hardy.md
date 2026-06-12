---
title: "scim installation difficulties on hardy"
date: 2008-05-09
forum: General Help
---

### Post by onlainari on 2008-05-09
Hey.

Running a fresh Hardy(xubuntu) and following the guide at [https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM) does not get me done. Well to be precise, my problem seems to be getting the "Enable support to enter complex charachters" box getting tagged. 

quote from the SCIM page:
> under Hardy, Gutsy or Feisty, you will have to check the box at the bottom (Input Method) to activate complex characters input. You will have to uncheck it, click Apply, then check it again and click Apply.

Check- uncheck - apply - check -apply - (gets unchecked automatically) ok - reboot -> box is being unchecked.


I have recently installed xubuntu three times, and each time the problem has occured. At first install, I don't know how exactly i got scim working, but i didn't pay so much attention to that tag thing that time. I didn't get it done, so I think i used some other tip described to some other done hardy system. 2nd time i noticed the tag problem. I check-uncheck-check-uncheck-check numerous times with boot or log out and in different occasions(next day) and then finally I got it, and scim also started to work. Now it's the third time, and I would rather learn how exactly I can get this work, and not just by a "lucky" tag. Any help appreciated thx..

---

### Post by onlainari on 2008-05-10
I got a satisfactory solution by installing scim-bridge-client-gt.

> Under Ubuntu 8.04 Hardy Heron

Nothing more to do since the ubuntu-desktop package already brings scim-bridge-client-gtk and language-selector setup the use of scim-bridge by default. 

Because of the above statement in [https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM) with no further notes for xubuntu users i thought these packages were installed and i didn't need to do anything as it says.

 I ran across a topic about virtualbox keyboard problem with scim users(as i have had the same problem before) i noticed someone mentioning to install scim-bridge-client-gt. For that matter i installed that one, because i knew i would try the virtualbox later. Out of curiosity I went to check if the "enable support to enter complex charachters" box stays checked and it did. I booted and scim is fine now. So, then I went to check whether xubuntu 8.04 has  those packages installed that above quote mentions to be installed by default, and actually only language-selector is. 

So I was a bit ignorant to not verify whether the quote statement was true, but [https://help.ubuntu.com/community/SCIM](https://help.ubuntu.com/community/SCIM) there could be a mention fox at least xubuntu users to install scim-bridge-client-qt and/or scim-bridge-client-gtk(?) to make it easier for xubuntu users.

---

### Post by Zorael on 2008-05-10
It's a wiki, go ahead and add your piece. :>

---

