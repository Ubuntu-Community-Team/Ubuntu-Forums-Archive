---
title: "check for sucessful login"
date: 2006-08-07
forum: General Help
---

### Post by gorded on 2006-08-07
Ok, here is the situation what i'm trying to do is to get a script to start running when a certain user logs in eg. James

so when james logs in i want script /usr/bin/script to run until james logs out.

Is there a way for me to do this. 

Thanks in advance

---

### Post by Tomosaur on 2006-08-07
If you make it executable and load it in Sessions (System > Preferences > Sessions) then it may work.

---

### Post by gorded on 2006-08-07
That will have the script run for all users not just one specific one. I'm wondering if add some stuff to stop the script if the user i want is not logged in, will it start the script again if the user logs in via ssh while the first user is still logged in.

---

### Post by darkshadow on 2006-08-07
To get it to run for only a certain user you can encapsulate it in a "if" command. That only runs if the output of "id -u" is whatever the uid is of your specified user.

---

