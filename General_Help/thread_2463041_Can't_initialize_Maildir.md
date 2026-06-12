---
title: "Can't initialize Maildir"
date: 2021-06-02
forum: General Help
---

### Post by daniilolegovich1995 on 2021-06-02
Good day! I did everything according to the instructions from this link [https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-postfix-on-ubuntu-18-04-ru](https://www.digitalocean.com/community/tutorials/how-to-install-and-configure-postfix-on-ubuntu-18-04-ru). I'll clarify, installed the postfix, then created two new users and added them to the mail group as root (the root was also added to the mail group). Next, I did everything according to the instructions (I tried it twice from scratch, once I followed the instruction on behalf of the root, the other from just the main account), when I start to do the Maildir initialization item, if I send a letter from the root or the main account to myself , then the cur, new and tmp folders are created, and if I do initialization from the created users, then these folders are not created, even Maildir is not created and letters do not come anywhere.
I also tried to issue full rights to the folders of created users and added them to the list of admins (sudoers), nothing changes. If I write ls -R ~ / Maildir (when I am in the account of the created user), I get a message: "ls: cannot access 'home / mailNDO / Maildir': No such file or directory". Help, please, I've already tried a bunch of different instructions and the same thing every time. Even in the main.cf file, My destinations left only localhost, local.domain and the same thing.

---

### Post by ActionParsnip on 2021-06-02
If you make the folders yourself (with the correct access. Copy root's but use the username instead of root) does it work OK?
Have you replied on the how to guide too? The authors can reply and assist.

---

### Post by HermanAB on 2021-06-02
Well, this is the error to solve: "ls: cannot access 'home / mailNDO / Maildir'

The 'ls' command probably runs as the postfix user, so either that directory does not exist at all, or the postfix user does not have access rights to it, or you made a typo somewhere in a configuration file.  I suspect a typo, since there are spaces around the '/' characters in your error message post.

You can check the permissions of the postfix user, by using 'sudo whoever' then try the 'ls' command.

Note that if you have Mandatory Access Control with SELinux or AppArmor enabled, then you have some more configuration to do.

---

### Post by daniilolegovich1995 on 2021-06-03
ActionParsnip, I copied the Maildir folder from root to the new user folder, gave it all the rights. When I logged in as a new user, these folders were visible, but no mail was sent or received either.
Thank you, yes, I'll write to the authors of the article now.
HermanAB, I tried to give all the rights to the postfix folder, but there is a dynamicmaps.cf file that prevents this from being done, then an error appears. Initially, I wrote without errors (no spaces), spaces appeared when uploading a message to the site, I did not put spaces in the terminal. Since postfix is not a user and it does not have its own folder in / home, I cannot / don&#8217;t know how to check its permissions. I do not have SELinux installed, and I disabled AppArmor, but this did not affect anything. I even did a clean install of ubuntu, and did it all from scratch, but the error still remains. The same problem with mailutils.
Anyway, thank you both for your help. But, if you still have thoughts on how to solve this problem, please write it.

---

### Post by HermanAB on 2021-06-05
You can see which user postfix is running as, with the ps or top commands.
$ sudo ps -e | grep postfix

---

