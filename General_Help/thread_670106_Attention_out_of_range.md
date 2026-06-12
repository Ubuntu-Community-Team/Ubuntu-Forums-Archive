---
title: "Attention: out of range"
date: 2008-01-17
forum: General Help
---

### Post by CharliueScott on 2008-01-17
Hi, I have just installed Xubuntu Dapper Drake LTS. I have no prior experince of using any Linux system, but i decided that I wanted to give it a go on my old workstation, (which was previously running Win98 ). 
 It is an old Computer. I installed the X86 Alternate CD, as the computer only has 128Mb of Ram.
  Everything was going fine, untill the installation finished, and it came to booting into the new system. The Xubuntu logo loaded, and everything listed loaded or mounted "ok", but after the logo screen, a dashed line on the top left of the screen appeared, (sort of like windows CMD Prompt), and the screen suddenly went black, and then flashy lines appeard on the screen. 
  shortly after that, a message appeared in a box in the center of the screen saying
 
  [B]Attention
Out of Range
H:   .1khz    L: ......HTZ[/B]  (not certain of the L: value, but i can post it later when i get home and check)
 
  From that i could not access anything. I have seen a couple of posts on here that saying to access the console and change values etc, but as i have no prior experience using Linux systems, i dont know how they work so i was wondering if anyone could post a simplified solution to this problem.

 I am using an old CRT monitor.. could that be it?

 Many Thanks 
Charlie Scott

---

### Post by svasanth on 2008-01-17
I'm afraid there is no simple soltion.Try this,

1.Press Alt+Ctl+F2,
2.login using user name password,
3.follow the steps in [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973).

The problem seems to that the refresh  range given in the graphical interface configuration file(/etc/X11/xorg.conf) does not fall into ur monitor settings. Try to increase the refresh range(this 'out of range' problem is common for old monitors).

---

### Post by CharliueScott on 2008-01-17
Thanks for the advice, just one problem, when it comes to entering the username and password, i cannot enter aany characters (numbers nor letters) in the password prompt. It just dashes (on the spot) quickly whenever i try and enter anything and then after trying for a while it says "timed out after 60seconds". 

 Do you think that a new monitor would solve the problem outright? Im thinking of taking the computer to my sisters place and try it out there, but if this problem is universal (on any monitor), i wont bother, and will just revert to windows.

Many thanks 
Charlie

---

### Post by ugm6hr on 2008-01-17
> **CharliueScott said:**
> Thanks for the advice, just one problem, when it comes to entering the username and password, i cannot enter aany characters (numbers nor letters) in the password prompt. It just dashes (on the spot) quickly whenever i try and enter anything and then after trying for a while it says "timed out after 60seconds". 

Have you tried just entering the password and pressing Enter (before it times out)?

It is not supposed to show the characters as you enter the password.

---

### Post by CharliueScott on 2008-01-17
I did, but i may have misstyped, i assumed that it would appear as ** or something to that effect. I'l give it another go, thnx

---

