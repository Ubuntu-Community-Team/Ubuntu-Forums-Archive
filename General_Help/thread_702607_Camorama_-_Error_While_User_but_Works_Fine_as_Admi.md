---
title: "Camorama - Error While User but Works Fine as Admin"
date: 2008-02-20
forum: General Help
---

### Post by igfud on 2008-02-20
Hello,

I installed Camorama for my webcam, an Ezonics III, using Add/Remove programs.  The program works just great while I'm logged into my administrator account.  When I try to open the program while logged in as a user, I receive an error:

```
Could not connect to video device (/dev/video0). Please check connection.
```

My user account has all privileges, minus administration of the system.  I've been toying around with the webcam for some time, so it is quite possible I installed a driver in the admin account.  How can I get the camera to work while logged in as a user?  I don't see why it works with one and not the other.

Thanks,
igfud

---

### Post by igfud on 2008-02-24
bump :)

---

### Post by shock2d on 2008-02-27
check if user is in group "video"

---

### Post by igfud on 2008-03-07
While logged in as admin, I went to "Manage Groups" and was unable to find one named "video."  I went ahead and created one, and added both my admin and user accounts to it.  It didn't help the problem, but maybe I have to do more than just create a group named "video"?

Thanks,
igfud

---

