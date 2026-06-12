---
title: "problem logging in to live seesion user (ubuntu)"
date: 2015-03-04
forum: General Help
---

### Post by jones5 on 2015-03-04
I am using live ubuntu 14.94lts on a usb with persistence. I tried to create a admin account with password - thinking this would protect my root. However what has happened is I cannot now log back into my live session user account. It never had a password and it is now asking for one. I need to get into the live session account as I had set many settings as I want them. I do not want to lose many hours of work. What I would ideally like to do is get into my live session account - then delete  the admin account. I have tried for hours - no luck. Any ideas?

---

### Post by TheFu on 2015-03-05
Login under the new admin account, set a password for the other account using **sudo passwd {other-username}**
Then logout and try to login using it with the newly set password.

Or

Login with the new admin account (which really is just a sudo-capable userid), then **sudo -i -u {other-username}** - to become the other userid and copy the files where you want them.

Might be a good idea to learn about the multi-user file and directory permissions. Those old files are there, just stored under a different userid. With proper understanding of file and directory permissions - this is a non-issue.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Thinking multi-user takes time, but it will come, with practice.

---

### Post by jones5 on 2015-03-05
Thanks for reply. If I use sudo passwd in terminal it asks for the password for admin. Admin is now sudo. It is not the user account I am interested in. The password I need is for the original user account (ubuntu) which is automatically there with the live ISO. It does not have a password. I cannot explain it in any other way. When I try to login through the desktop (gear wheel at top) it ask me authenticate 'live session user (ubuntu)'. Underneath it asks for password for ubuntu. This does not exist. I am new to Ubuntu and Linux. Can anyone explain simply how I do this?

---

### Post by ajgreeny on 2015-03-05
You should just leave that user's (ubuntu's) password box empty and hit Enter; that should log you in as the normal live system user.

---

### Post by jones5 on 2015-03-05
error

---

### Post by jones5 on 2015-03-05
Thanks but leaving the box empty and hitting enter does not work. Tried it several times.

---

### Post by Portaro on 2015-03-05
The default user count is Ubuntu, without password - so is blank passcode -

You can try simply press Enter on the password field, if not work there are a password and you need to reset this -> [https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)

You need to boot with **advanced options enabled on grub** , then **select the recovery mode** , text dialog choose **root &#8211; drop to root shell prompt**

> mount -o rw,remount [B]/
[/B]
list home user [B]
[/B]
> ls /home/

now replace passwd of user 


> sudo passwd [B]yourusername


[/B]confirm with ->[B]password updated successfully

[/B]> exit  - on console 


You return to the recovery mode window, choose , [B]resume normal boot


[/B]Boot process, and see if works[B].
[/B]

---

### Post by jones5 on 2015-03-05
Thanks but cannot get into grub screen. This seems to have been a long running bug also. The fix for the grub screen cannot be  implemented because /etc/default/grub is read only. Does anyone have an answer (without older problems) to clearing the new user (admin) out of the way and restoring the original Ubuntu user with no password. I would obviously like to keep my changes in that user. Otherwise I will simply reinstall the live OS  on the  USB and wipe whatever is there. I will never change the user again though if I do this. This would leave my data 'un-passworded'. I cannot think that was intended in the design?

---

### Post by TheFu on 2015-03-05
I've already provided a way. Unfortunately, you don't have the background yet to understand and I don't have the skill to help any more that I already have.

I've attempted to clarify my post #2 above. Hope that helps. I've had to make lots of assumptions which may NOT be true.  The more details you can provide, the better we can help.

---

### Post by Portaro on 2015-03-06
> **jones5 said:**
> Thanks but cannot get into grub screen. This seems to have been a long running bug also. The fix for the grub screen cannot be  implemented because /etc/default/grub is read only. Does anyone have an answer (without older problems) to clearing the new user (admin) out of the way and restoring the original Ubuntu user with no password. I would obviously like to keep my changes in that user. Otherwise I will simply reinstall the live OS  on the  USB and wipe whatever is there. I will never change the user again though if I do this. This would leave my data 'un-passworded'. I cannot think that was intended in the design?


- [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)


- [https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

If you go to reinstall the system - you need (dont format) your current (/home - partition) and you need to give a different user to your new user instalation, and in persistent modes I dont have idea if works or not.

---

### Post by jones5 on 2015-03-06
Thanks The Fu, but I need someone who can help me on my level as a newbie to Ubuntu -As I did make clear before. If you do not want to break down your advice to someone at my level that is of course your privilege.

---

### Post by jones5 on 2015-03-06
> **Portaro said:**
> - [https://wiki.ubuntu.com/RecoveryMode](https://wiki.ubuntu.com/RecoveryMode)


- [https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

If you go to reinstall the system - you need (dont format) your current (/home - partition) and you need to give a different user to your new user instalation, and in persistent modes I dont have idea if works or not.

Sorry Portaro - I am not sure what you are saying here. I cannot try your original suggestion because I cannot get into Grub and advanced screen as explained before. This seems to be a well known issue on reading other threads.

---

### Post by jones5 on 2015-03-06
Does one of the moderators want to put this post onto - New to Ubuntu - as some of the posters seem unhappy it is here?

---

### Post by jones5 on 2015-03-07
> **TheFu said:**
> Login under the new admin account, set a password for the other account using **sudo passwd {other-username}**
Then logout and try to login using it with the newly set password.

Or

Login with the new admin account (which really is just a sudo-capable userid), then **sudo -i -u {other-username}** - to become the other userid and copy the files where you want them.

Might be a good idea to learn about the multi-user file and directory permissions. Those old files are there, just stored under a different userid. With proper understanding of file and directory permissions - this is a non-issue.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Thinking multi-user takes time, but it will come, with practice.


Part 2 of this worked. Login under new 'admin' user , then open terminal enter,  sudo -i -u ubuntu. (ubuntu is the username of the preset account). then type in terminal,  firefox -p
This brings up a profile screen and you can choose the profile of the old session in firefox.
Now you can save this profile (using Febe) to say - downloads in your file manager in the new admin user account. This allows you to open firefox in the new account and view all your old settings. 

Thanks to the Fu. As a beginner I still feel  it might be useful if Ubuntu put on their otherwise excellent new home page/download area - that people trying out the live USB with persistence version should be careful when opening new accounts, that there is a Ubuntu user account that has no password in operation (maybe also remove the box in authentication for this non- password as it is very confusing) and suggestions as to how Root can be safeguarded with a password. It seems strange to have an OS and two accounts without passwords as soon as you start to use it?

---

### Post by TheFu on 2015-03-07
This was all about a firefox profile? I must have missed that in earlier posts.

Firefox settings are completely portable. I've moved them between systems even between different OSes.

jones5 I get that you are frustrated, but none of this is odd. The real warning is that people new to any Unix-like OS need to learn to think a little different when doing slightly unusual things.  Follow the reading here: [http://blog.jdpfu.com/2014/12/28/learning-linux](http://blog.jdpfu.com/2014/12/28/learning-linux) and read at least the first 4 items to get the background which seems to be missing. It won't make you into a Unix-wizard. That takes years.

Also - be VERY careful running any GUI programs with sudo. Doing that can cause the program to become unworkable as the normal user account. Had to help someone last weekend because he'd used **sudo gedit** once following instructions at a random blog. Afterwards, he couldn't run any other gnome-based applications on his system (at least none that he tried).  This was all due to file and directory permissions and the fact that he didn't understand those.  See my very first post ... and please, please, please go and learn that stuff.

---

### Post by jones5 on 2015-03-09
Understood and suggestions taken on board. I will continue with Ubuntu trial as I can see there is a lot to learn before making any real assessment. 

I think I have now retained the profile I wanted (sorry if that was not clearer earlier). I will try and use it on a fresh install (assuming file permissions are still correct). I will read the material suggested. And thanks again to those who answered - I know people are only trying to help.

---

