---
title: "[SOLVED] No Log Out Sound When I Log Out"
date: 2007-11-02
forum: General Help
---

### Post by adrian007 on 2007-11-02
Hello, I just upgraded to Ubuntu 7.10 and everything is great till i shutdown the computer. There was NO Logout Sound. I have checked the sound manager and the logout sound is enebled. All my other sounds work perfectly. It is not a big issue but i would like it to be solved.

P.S In Ubuntu 7.04 My Logout Sound Worked


Thank You In Advance:):):):):):)

---

### Post by nick_h on 2007-11-02
I have the same problem.  There are a few threads on the subject, for example, [here](http://ubuntuforums.org/showthread.php?t=600206) and [here](http://ubuntuforums.org/showthread.php?t=597058).

There is a more interesting one [here](http://ubuntuforums.org/showthread.php?t=565070).

There has also been a bug reported - [link](https://bugs.launchpad.net/ubuntu/+bug/157190)

---

### Post by adrian007 on 2007-11-03
Thank you as i thought only i had been having the problem

Thanks:)

---

### Post by imbjr on 2007-11-05
I can confirm on my Dell E520 that there's no logout sound. It can be played, but it does not trigger when it should. 

Tried changing it and re-enabling the system beep (which by the way seems to happen a little more often now - I've not yet paid enough attention to when, but one occasion was logging out and the login screen with faces being displayed).

---

### Post by dcstar on 2007-11-05
> **imbjr said:**
> I can confirm on my Dell E520 that there's no logout sound. It can be played, but it does not trigger when it should. 

Tried changing it and re-enabling the system beep (which by the way seems to happen a little more often now - I've not yet paid enough attention to when, but one occasion was logging out and the login screen with faces being displayed).

Install the **esound** package.

---

### Post by imbjr on 2007-11-06
> **dcstar said:**
> Install the **esound** package.

Worked a treat. Ta.

---

