---
title: "Mega file storage app can't see anything under &quot;computer&quot; directory"
date: 2017-05-01
forum: General Help
---

### Post by juntjoo2 on 2017-05-01
...and the folders I want to sync are on a particular partition that would be accessible directly from the "computer" directory.  Anyone have any idea why this is and what I can do to access this partition?  Thanks

---

### Post by Autodave on 2017-05-01
I am totally lost: you need to give a lot more info. For instance, is this all on one HD or on different HDs?  Did you make a special partition for these files? How was the partition formatted? 

What exactly are you calling the "computer" directory? Is this a directory that you created with that name?

---

### Post by juntjoo2 on 2017-05-01
> **Autodave said:**
> I am totally lost: you need to give a lot more info. For instance, is this all on one HD or on different HDs?  Did you make a special partition for these files? How was the partition formatted? 

What exactly are you calling the "computer" directory? Is this a directory that you created with that name?

this is one HD and I created the partition formatted for my Windows system to also be able to read, so it's whatever that is.  Can't think of it off the top of my head but it's the main one format Windows uses. And I can access it through Linux too, but this particular app isn't seeing it I guess, well, it's just not seeing anything under "computer", which is like the main directory for this system. I didn't create it. It's got all the system folders like "bin", "boot", "dev", "etc", "home" and the partition I created "SharedFiles". Thanks

---

### Post by howefield on 2017-05-02
So, it's a shared partition that both Ubuntu and Windows use to access files, is it mounted in fstab ?

---

### Post by juntjoo2 on 2017-05-02
> **howefield said:**
> So, it's a shared partition that both Ubuntu and Windows use to access files, is it mounted in fstab ?

yes and yes, but never mind anymore.  Thank you for helping out.  There was nothing wrong.  I just needed to double click on the folder in the window to open up what's inside(the "computer" folder).  I was just a step away and didn't realize it.  Thanks

---

