---
title: "Home folder Recovery.. Permissions"
date: 2007-12-13
forum: General Help
---

### Post by brohan on 2007-12-13
After having my laptop hard drive die, I got a new one. I was very happy with my xubuntu configuration on the old one, so I just copied the home folder over to an ext2 formatted external hard drive.

On copying the folder back to my newly installed home folder, File permissions got the best of me, some of my configuration settings didn't work, a swift chmod -R 777 * fixed my issues, but that isn't a good idea.

I'm wondering if there is some way to get the permissions on my external hard drive to jive with the permissions on my local hard drive.

EDIT: I have the same username, and the command I used to copy the files over was cp -R /media/river/brohan /home/brohan

---

### Post by dondad on 2007-12-14
> **brohan said:**
> After having my laptop hard drive die, I got a new one. I was very happy with my xubuntu configuration on the old one, so I just copied the home folder over to an ext2 formatted external hard drive.

On copying the folder back to my newly installed home folder, File permissions got the best of me, some of my configuration settings didn't work, a swift chmod -R 777 * fixed my issues, but that isn't a good idea.

I'm wondering if there is some way to get the permissions on my external hard drive to jive with the permissions on my local hard drive.

EDIT: I have the same username, and the command I used to copy the files over was cp -R /media/river/brohan /home/brohan

Try this:
To fix file permissions after copying (works on home directory also DAMHIKT)

Navigate to the top file that you want to change along with everything below,

sudo chown -R username:username .

[COLOR="Red"]Note the dot[/COLOR]

then 

sudo chmod -R u_rwx .

[COLOR="Red"]again, note the dot.[/COLOR]

This will set your top level to 755 and the other stuff under it to 644

---

