---
title: "Adventure with user administration (Solved)"
date: 2006-11-14
forum: General Help
---

### Post by bobromeo on 2006-11-14
The adventure started with my wife (linda) complaining that she couldn't log in anymore. 
Used the administration tool. No linda. Added linda. Login, nothing. 
Used the administration tool (UAT) several times and after exiting and starting the tool again, no linda !
Noticed that there still was a home dir for linda, removed it {thought that was the problem, shouldn't have done that, read it in the manual}
Editted passwd with vi, saw no linda, added line with yy (surprised myself remembering that, afer 10 years unix inactivity)
Remembered that her uid was 1004.
Used UAT and there she was again, changed the password, but no luck no login !
Copied a home dir and chown-ed it
Linda was still  a group, but still no login.
Did a passwd -d linda and after that a passwd linda.
Now she can login again ;) 

(Use ubuntu 6.10 now but the original account for linda was before this upgrade.)

---

