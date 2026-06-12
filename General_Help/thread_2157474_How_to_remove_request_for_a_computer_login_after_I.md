---
title: "How to remove request for a computer login after I select Ubuntu from the grub menu?"
date: 2013-06-25
forum: General Help
---

### Post by A4Skyhawk on 2013-06-25
I have Ubuntu 12.10 (w/ GNU Grub v2.00-7ubuntu11) and Windows Vista.  There are no passwords in my BIOS.  In Ubuntu/System Settings/User Accounts, I  have it set up with a password, but with Automatic Login ON.  After  selecting Ubuntu in the Grub menu, I want Unity to boot-up without the  use of the password.  However, after selecting Ubuntu, the boot-up  SOMETIMES (not always) presents a black screen with the following display:
 

  Ubuntu 12.10 [my computer name] tty1
[my computer name] login:


  If I do nothing, it times out in ~45 secs and completes the boot-up  into Unity.  If I comply with the login request, it takes me to a root  command line, after which I do a CNTRL-ALT-DELETE and start over and let  it time out. 

How can I eliminate the request to login to my computer? 

TIA, A4Skyhawk

---

### Post by A4Skyhawk on 2013-06-29
Solved:  This problem has gone away ( I don't know how or why).  Now when I select Ubuntu in the Grub menu, the black scrren w/ the above message flashes very briefly and the boot up into Unity continues w/o having to enter a user name or password.
NOT solved:  The black login screen came back today (7/2/13).  See my response below

---

### Post by grahammechanical on 2013-06-29
What you have been seeing happens every time we boot but we do not usually see it because the process usually goes too fast to notice. If the loading process has difficulty doing what it is trying to do it will try again for several times and that produces a delay and we will see that login in screen. This is happening before Ubuntu is loaded. So, it is nothing to do with the automatic login setting.

If the boot process is badly broken you may get that login screen and it may not load any further. I have noticed that after two or three good, fast boots the system behaves better. It is as if it has a better writen scrpt to follow. 

To put it simply, first Linux is loaded (black screen with a login), then the Ubuntu platform loads on top of that (GUI login screen or GUI desktop)

Regards.

---

### Post by A4Skyhawk on 2013-07-02
Thanks for the explanation of the process sequence.  The black login screen appeared again today (7/2/13) after a few days of absence.  Is there something (file?) that I should check to see if it needs to be fixed?

---

