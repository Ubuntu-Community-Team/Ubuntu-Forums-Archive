---
title: "how to set up password login at startup"
date: 2015-08-22
forum: General Help
---

### Post by freddyfields on 2015-08-22
please, how do i make it where ubuntu comes to a login screen instead of logging straight into system at start up? i had this problem before and fixed it, but cant seem to find a solution this time. I downloaded ubuntu tweak and have gone to system> user and groups to no avail. Thought i remembered typing in a command in terminal last time that removed my screenname from auto login but dont remember the key words i googled to find that command. Really hate having my computer boot to first person on login. Any help? ubuntu studio 14.04.3

---

### Post by deadflowr on 2015-08-22
Open the dash and search "user accounts"
You need to click on the lock (or unlock) button in the top right corner before you set anything.
Then toggle the automatic login button.
It's most likely set to on.

Alternatively, look to see if you have a file in /etc/lightdm/lightdm.conf, or /etc/lightdm/lightdm.conf.d/XX_some-file-name.conf.
More likely autologin would be set in the first lightdm.conf file, but the sub-folder lightdm.conf.d may also hold it.

The file will have a simple one-liner like "autologin-user=you"
You can simply delete the file.

---

### Post by freddyfields on 2015-08-26
Great Thanks, got it.  Found that text file and removed my name. Now if i can get the profile pic changed.  Oddly enough, Ubuntu tweak supposedly set the background on login to my costume background, but it has not worked even thou its set in tweaks settings. leads me to believe that Ubuntu tweak doesnt work well in 14.04.3

---

