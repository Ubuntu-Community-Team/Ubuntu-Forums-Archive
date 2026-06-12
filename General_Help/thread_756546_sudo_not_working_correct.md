---
title: "sudo not working correct?"
date: 2008-04-15
forum: General Help
---

### Post by Linux&amp;Gsus on 2008-04-15
I tried the other day to connect an external screen to my laptop and therefore wanted to check and set the settings in: *K Menu -> System Settings -> Monitor & Display*. I clicked on "Administrator Mode", the field to enter the password came up but that was about it.
It either locked me out from trying that again or gave me a message saying that it's the wrong password. Just out of curiosity I tried the same with the 2nd user I have here, didn't work, of course, but even the original user doesn't do it. No matter if I enter the user password or root password (yes, I have a root password). The user belongs to adm and admin group, so that should work, right? Is there anything else I need to or can check?

I ended up using Windows for the presentation I made. That worked just fine. But on Linux a 2nd screen or projector just doen't come up and I can't change the settings.

Any ideas?
Thanks,
Steve

---

### Post by gsmanners on 2008-04-16
If you have doubts about whether sudo is properly configured, you can use "visudo" to edit your sudoers file, but first read the "man visudo" and make sure you know what you're doing as you can really mess up your system.

As for adding a display device, you will need to consult "man xorg.conf" (or use a program that can edit it for you) and restart X (ctrl-alt-backspace) when you have that properly configured to use the device.

---

### Post by Linux&amp;Gsus on 2008-04-16
I had a look at visodu and I would say it looks all fine to me. And since that is the fact plus I'm pretty good with messing up systems I better don't do a whole lot there to see what things would change.

Any ideas why I don't get root privileges when I type in my password in the system settings? Since I have a password for root which password do I need to type in anyways?

Thanks for any advise,
Steve

---

### Post by gsmanners on 2008-04-16
If you use sudo and your user name is in the admin group, then sudo gives you root priviledge (the same as if you were root).

Type "groups" in a terminal to see if admin is one of your groups.

To be sure type this in a terminal:

sudo -i
pwd

If you entered your own password and received "/root" in response to "pwd" then it's safe to say that you can get root access. That being the case, you may have discovered a bug in one of the KDE settings applications/applets.

---

### Post by Linux&amp;Gsus on 2008-04-16
So, I tried all that in the console. My *ordinary every day* user account shows his home dir with "**pwd**" after the "**sudo -i**", as expected. The original user account is part of the **adm** and **admin** group (I guess that are the relevant ones?) and "**pwd**" shows "**/root**". So, from that point of view everything should be fine.



> **gsmanners said:**
> If you entered your own password and received "/root" in response to "pwd" then it's safe to say that you can get root access. That being the case, you may have discovered a bug in one of the KDE settings applications/applets.

Before I go that far to say that I might have found bug I guess I would need to test a little bit more. E.g. what happens when I try to get admin privileges at, say, the user administration, etc. I might as well just have messed up my system. Which from experience I'm very capable of.

Which also leads me to the question if I actually can mess up my system in a way that sudo would not work in a gui but still be fine in a terminal. Any insight here? Also, any suggestions how I could efficiently test the whole thing to more accurately say whether this is a bug or not?

Cheers,
Steve

---

### Post by Linux&amp;Gsus on 2008-04-24
So, I guess I need to revive that thread.

I just installed the Hardy RC in virtual box. Means, I have a clean install of Kubuntu. After the install finished I went straight to the System Settings and tried to get administrative privileges. But I had no success at all.

I tried 'sudo apt-get update' in a terminal. It asked me for the password, entered it, and all worked fine.

So, anyone an idea what that means? Is there someone who can confirm that behavior? Is that just my machine, or am I doing something wrong?
I could hardly believe that I have found a bug here. I mean, not getting admin privileges in the System Settings is a bit of a problem, I guess... :lol:

Cheers,
Steve

---

