---
title: "How to delete a link"
date: 2007-03-31
forum: General Help
---

### Post by rahulthewall3000 on 2007-03-31
Hi, 
I created a link to my windows hard drive and now I want to delete that link. But when I try to move the link to the trash I see no response. Can anyone out there tell me how to do so. 

Thanks 
Rahul

---

### Post by taurus on 2007-03-31
Applications -> Accessories -> Terminal
```
rm **filename**
-or-
rmdir **directory**
```

---

### Post by rahulthewall3000 on 2007-03-31
Thanks a lot for that, though I did it in a different way. As I had ntfs-3g installed I moved the link from my Linux hard drive to the windows hard drive and then deleted it from linux. Strangely enough, rm/rmdir  didn't work. 

Cheers
Rahul

---

### Post by ssakgul on 2007-09-01
And the extended question is that: What can I do if the link refers to a directory which contains important data and I want to erase only the link, not the data? If they are in separate file systems it is a big problem.

I did it:

[LIST=1]
[*]Rename the real directory
[*]Remove the link
[*]Re-rename the real directory if you want
[/LIST]

---

