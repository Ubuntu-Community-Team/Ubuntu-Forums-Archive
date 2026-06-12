---
title: "Installed Ndiswrapper, and cant install other apps"
date: 2008-03-30
forum: General Help
---

### Post by mattrobinson999 on 2008-03-30
Ive installed ndiswrapper to use my wireless usb adapter and i can get onto the internet now without any difficultly.

But, now i cant install anything at all, its as if my computer doesnt have an internet connection, but i know it does because i can get onto google with my mozilla firefox.

does any one have any suggestions for me?
thanks for the reading

---

### Post by DoctorMO on 2008-03-30
Can you post the errors that you get when you run the following command in a terminal:

```
sudo apt-get update
```

and then if there are no errors just post the entire log for us.

If you installed ubuntu and you didn't have an internet connection it could have disabled all of the repositories and you need to re-enable them: Goto Applications > Add/Remove... Then click on the preferences button in the lower left corner.

Now make sure each of the checkboxes are enabled and that all your repositories are correct.

---

