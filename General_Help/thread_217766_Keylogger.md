---
title: "Keylogger?"
date: 2006-07-17
forum: General Help
---

### Post by digimars on 2006-07-17
I have a friend who thinks his wife has installed a keylogger program on his Windows xp computer.  I mostly use Linux, so is there a linux tool that I could use (LiveCD style) that could help me find one, if there is one?  Where would I look to see if he does have a keylogger proggy running in the background?

---

### Post by T700 on 2006-07-17
Most, common Windows keyloggers can be detected by commercial software such as Pest Patrol, Symantic Anti-Virus, or the like.  I think I'd go that route first.  If she is sophisticated enough to circumvent detection from ordinary scanners, you are unlikely to be able to locate it, Linux or not.

As a sidenote, if the situation is really that bad, I'd worry more about gasoline in the bed or a knife to the back, but that's just me!

Paul

---

### Post by jordilin on 2006-07-17
I don't know, but you could run any spyware removal tool directly in the windows machine. I don't see the point of running a Linux Live Cd to detect a keylogger.

---

### Post by glinsvad on 2006-07-17
First of all, I'd do a very simple test:
- search for files (all hidden and system included) containing a very unique text string such as ifafilecontainsthistextthensomeoneisbuggingme
- repeat the search a few hours later

This will reveal if logfiles are being generated in plain text because your keystrokes will be saved somewhere in your filesystem. However, if the keylogger encrypts your keystrokes, it will not show up.

Primarily you could then rely on simple anti-virus scans (assuming your wife isn't an expert programmer with the ability to write her own keylogger).

That being said, a keylogger is really quite similar to a trojan horse, primarily because it needs to run every time the computer starts up WinXP. This is a major tell-tale, since there are only so many ways a program can be loaded at startup (again assuming the keylogger isn't able to infect files like a virus can).

You should concentrate on regedit, which has a list of programs to run on login - be suspecious of any non-windows exe/dll-file you can't track back to something you installed yourself. Just follow step 4 in this guide (do the rest also just in case).
[http://www.symantec.com/security_response/writeup.jsp?docid=2004-021914-2822-99&tabid=3]("http://www.symantec.com/security_response/writeup.jsp?docid=2004-021914-2822-99&tabid=3")

---

### Post by digimars on 2006-07-17
I'm pretty sure that he has anti-virus running, and I know that he has Windows firewall.  I'll check with him to make sure that his stuff is up to date.  He may not have any anti-spyware stuff, so I'll load some up on my USB key when I head over there.  Thanks for the tips everyone!!

---

