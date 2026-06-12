---
title: "Unable to access anything as a User in Linux due to Users and groups option modified"
date: 2017-03-09
forum: General Help
---

### Post by sagar.r.n on 2017-03-09
I logged in as root and went into "**system> administration> user &  groups**" and changed the Users **Primary Group** option to a new group that i just created so that i can remove the previous group and users... and also changed the Home directory to **/home**

turns out when i boot up the computer it asks for password of user account which i gave. But after login...

nothing comes up. at first..


then i get a message that says:

"Could not update ICEauthority file **/home/.ICEauthority **"

it gives me the option to click CLOSE.

and when i do

another message comes up that says:

"[B]There is a problem with the configuration server.
(/usr/libexec/gconf-sanity-check-2 exited with status 256)"
[/B]
it gives me the option to click CLOSE

and when i do its just a empty background no panel nothing just a default wallpaper.

 a few moments later then another message


"[B]Nautilus could not create the following required folders: /home/Desktop, /home/.nautilus.
Before running nautilus. please create these folders or set permissions such that Nautilus can create them.[/B]"

I can then click ok.

There is nothing on the screen. Not even the home folder and Terminal... I did try to get into the terminal by pressing ctrl+alt+f1 and also through Accessories. But Terminal itself doesn't exist at all in Accessories. Help me out plzzz... Can't open anything. Need to access file system and folders in it

---

### Post by Impavidus on 2017-03-09
When you want to change something in users & groups, you normally open system&#8594; administration&#8594; users & groups, click on something you want to change and then you'll get prompted for your password. Logging in as root is not the way to go. There's a reason why it's disabled by default.

You've noticed that using /home as your home directory is a bad idea. You need write permissions in your home directory. On most systems the home directory would be /home/username. Sometimes administrators change it to /home/groupname/username or something like that, but never /home.

Try this: boot into recovery mode, drop to a root shell and mount the file system read-write. Follow the first steps of this tutorial: [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)
Then use your favourite terminal-based text editor to open /etc/passwd, for example nano or vim. Find the line with your user name. Probably the last line. It has several (it should be seven) entries separated by colons. The sixth entry is your home directory. Fix it, then save and resume booting.

I hope that's the only thing you messed up.

---

### Post by sagar.r.n on 2017-03-18
Thanks for the help. Your link to reset the password helped me to gain access. But i really did mess up all the things in that user permissions. So, i created another user from root permission and created the home path as you said inside another group and accessed the files and folders in the drive. Really appreciate your support.

---

### Post by oldrocker99 on 2017-03-18
If your problem is solved, please mark the thread as [SOLVED] to help other users. 

Logging in as root is **not** a good idea. Using sudo as a regular user give you *temporary* root access, which is the way it should be, in most people's humble opinions.

---

