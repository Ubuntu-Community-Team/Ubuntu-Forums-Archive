---
title: "how to share wine programs between users?"
date: 2008-05-18
forum: General Help
---

### Post by rkleemann on 2008-05-18
Hi,

I'm running Ubuntu Hardy, wine 0.9.59.

I went through a somewhat lengthy process in getting Office 2007 installed with Wine, and to my surprise it is actually working!!

But I hadn't realized that installing wine programs is good only for the user that installed it!

I installed it under my account, but really the main reason I installed it is for my wife!

Isn't there a way to install programs in a shared folder rather than ~/.wine?

It actually works with a symlink... I moved my ~/.wine to /home/.wine and symlinked to ~/. That actually works, but only because /home/.wine is owned by me. If I try the same for my wife, it won't work because it's not owned by her user.

I'm guessing I could copy the contents of .wine to her home, but then I'm wasting space.

It would be really nice to have a shared wine installation for some applications.

Is there any way that could be done?

---

### Post by empthollow on 2008-05-18
you could make a group and add permissions for that group to your .wine folder.  Then, add your wife to that group.  I believe then your simlink will work.

---

### Post by rkleemann on 2008-05-18
> **empthollow said:**
> you could make a group and add permissions for that group to your .wine folder.  Then, add your wife to that group.  I believe then your simlink will work.

Unfortunately, wine complains about the owner, even if the group is shared

I created a group "wine" and chgrp -R wine on the folder... but when trying to run wine off my wife's account it just complains that wine isn't owned by her account.

---

### Post by empthollow on 2008-05-18
hmm, i thought that would work, i'm kinda supprised it didn't.  the only other thing i can think of is to check permissions on the simlink, but i'm fairly sure it takes on the permissions of what it is linked to.  I'll let you know if i think of something else.

---

### Post by rkleemann on 2008-05-18
Thanks.

I think I might just have to copy the whole directory and chown... because wine checks the owner.

I think I'll visit winehq and see if there are any answers there.

---

### Post by Mr A Mouse on 2008-05-18
You could try making the /home/.wine folder owned by "Nobody", group "wine", and make sure both you and your wife are in the wine group. I don't know if it will work, but it's worth a shot, and can easily be fixed if it's not the right solution.

---

