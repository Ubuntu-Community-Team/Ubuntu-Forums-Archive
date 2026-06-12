---
title: "Loading https"
date: 2008-02-13
forum: General Help
---

### Post by talkingtree on 2008-02-13
I tried searching for previous posts but it seems like no one else got this problem except me!!

I freshly installed Ubuntu linux on my comp and opened up firefox. The site that has http works but sites like gmail with "https" does not load. How do I solve this?

---

### Post by nemilar on 2008-02-13
Does it give you an error message?  Can you describe in more detail what happens when you say that it doesn't load?

---

### Post by talkingtree on 2008-02-13
oh it doesnt load as in firefox displays connection has timed out

it's not the server's problem because i tried gmail on another computer and it works fine

---

### Post by nemilar on 2008-02-13
[http://ubuntuforums.org/archive/index.php/t-279191.html](http://ubuntuforums.org/archive/index.php/t-279191.html)  seems to have some ideas on the issue:

1)  Check that SSL is working in your browser by testing it here:
[http://weblogin.bu.edu/troubleshooting?cmd=ssl](http://weblogin.bu.edu/troubleshooting?cmd=ssl)

 My gut feeling is that SSL is working fine and you'll pass the test..  If you scroll all the way down in that post, you'll find that the solution that eventually worked in that case was disabling IPv6.  *My gut* tells me that it will work for you, too, so give that a shot.

[http://ubuntuforums.org/showthread.php?t=6841](http://ubuntuforums.org/showthread.php?t=6841)
Has information about how to disable IPv6.  Try giving the second post a try first; disable IPv6 in Firefox and restart your browser, and see if that works.  If so, then you should probably disable it system-wide.

I hope this fixed your problem, 'cause that's about all I've got.

---

### Post by talkingtree on 2008-02-13
ok cool it works now ^^

i really appreciate ur help, thank you

---

