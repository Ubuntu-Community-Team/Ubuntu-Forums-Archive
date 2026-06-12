---
title: "sudo and temperory root"
date: 2007-01-17
forum: General Help
---

### Post by neoflight on 2007-01-17
I would like to know the differences between using

1. sudo and
2.  using root temporarily 

what's the difference if the time logged as a sudo or root from a terminal to install apps or edit some config fies is the same! 

why is sudo preferred to  root ...

i got stumped when talking to a fedora guy! ](*,) 

thank you

---

### Post by taurus on 2007-01-17
Because sudo applies only for that command and while you log in as root, it lasts for the whole session.  And if you forget that you are still root and run something that you're not supposed to, then you are in deep water.  But if you try that command from your regular account without the sudo, then you just get an error message about permission problem.

---

