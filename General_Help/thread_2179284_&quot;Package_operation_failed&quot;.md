---
title: "&quot;Package operation failed&quot;"
date: 2013-10-07
forum: General Help
---

### Post by PaulBx on 2013-10-07
In the software updater I got "Package operation failed" and "The installation or removal of a software package failed."

I think I am running 13.04 although I am not sure if the updater could boost me up to 13.10 on its own? Anyway how to tell what revision I'm on? "uname -a" doesn't do it. (first couple of dumb questions... )

Well I finally figured out what it was by searching the forum: /boot ran out of room.

However I'd like to suggest that the updater error message be a bit more edifying (there is no "details" button). Surely the updater knows what is wrong; why doesn't it tell me? Then I wouldn't have to go searching through the forum and bothering people with dumb questions. :smile:

This cannot be an infrequent error, what with a limited size of /boot and the updater keeping all the old kernels around...

---

### Post by ian-weisser on 2013-10-07
Developers generally won't see a message in this forum.

Instead, consider filing a bug report "The error message is not helpful," and do suggest a better way to handle the problem.

---

### Post by ajgreeny on 2013-10-07
> **PaulBx said:**
> In the software updater I got "Package operation failed" and "The installation or removal of a software package failed."

I think I am running 13.04 although I am not sure if the updater could boost me up to 13.10 on its own? Anyway how to tell what revision I'm on? "uname -a" doesn't do it. (first couple of dumb questions... )

Well I finally figured out what it was by searching the forum: /boot ran out of room.

However I'd like to suggest that the updater error message be a bit more edifying (there is no "details" button). Surely the updater knows what is wrong; why doesn't it tell me? Then I wouldn't have to go searching through the forum and bothering people with dumb questions. :smile:

This cannot be an infrequent error, what with a limited size of /boot and the updater keeping all the old kernels around...
This is not actually a very common problem, as most users do not have a limited sized /boot as it is just a folder in their root partition.  Do you have a good reason for having a separate /boot partition?

---

