---
title: "File .ICEauthority unable to update"
date: 2014-05-21
forum: General Help
---

### Post by sofasurfer on 2014-05-21
My PC went kaput. When I start it I get a message, right after the POST screen, that says "can not authenticate .ICEathority file". I found info to indicate that this is probaly caused by my permissions being corrupted. So, is the permissions on .ICEauthority supposed to be for me, the user, or for the administrator? 
What might have caused this problem? Do you see another possible problem besides permissions as being the culprit?

---

### Post by coldcritter64 on 2014-05-21
The file should be owned by you:you and have 600 for the permissions (that is read and write for you only ... NO access for group or others, it is used for authentication purposes so that is important no one else can access it). The ownership of the file if taken over by root can cause the problem.

Have you been using graphical applications launched as root with sudo rather than either gksudo or gksu ? That is one possible means of corrupting the ownership and permissions of .ICEauthority. I also believe there is or was a bug on gnome3 that could cause it (don't know enough about the details on that one though).

This [[COLOR=#0000ff]--link--[/COLOR]]("http://galigio.org/2011/10/31/fix-iceauthority-problem-at-linux-boot-up/") has a pretty good description of what .ICEauthority is and how to fix problems with it. It is a guide from 2011 about Ubuntu 10.04, from what I know of .ICEauthority it should still be valid info for the repairs.

---

