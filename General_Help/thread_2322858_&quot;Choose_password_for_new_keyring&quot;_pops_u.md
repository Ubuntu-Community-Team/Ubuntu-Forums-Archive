---
title: "&quot;Choose password for new keyring&quot; pops up every time I open google Chrome"
date: 2016-04-30
forum: General Help
---

### Post by lethalfang on 2016-04-30
This window pops up every time I open Chrome for the first time after booting into Xubuntu, and only in one of my desktops. It doesn't matter what I do with it, e.g, Cancel, Continue without putting in anything, or Continue after putting in something.
[ATTACH=CONFIG]268737[/ATTACH]

It first started a few months ago in Xubuntu 14.04.4, and now that I've upgraded to Xubuntu 16.04 (kept the /home mount in a separate hard drive), removed .config/google-chrome, and removed .local/shared/keyrings, and this window still pops up.
Anyone has any clue how to get rid of that?

Thanks in advance.

---

### Post by T.J. on 2016-05-02
> **lethalfang said:**
> This window pops up every time I open Chrome for the first time after booting into Xubuntu, and only in one of my desktops. It doesn't matter what I do with it, e.g, Cancel, Continue without putting in anything, or Continue after putting in something.
[ATTACH=CONFIG]268737[/ATTACH]

It first started a few months ago in Xubuntu 14.04.4, and now that I've upgraded to Xubuntu 16.04 (kept the /home mount in a separate hard drive), removed .config/google-chrome, and removed .local/shared/keyrings, and this window still pops up.
Anyone has any clue how to get rid of that?

Thanks in advance.
 [ATTACH=CONFIG]268802[/ATTACH]

In XFCE's settings, Session and Startup.  Make sure Gnome services are turned on so that the key-ring service is active.  Try that and see if it takes care of it. Many GTK programs are so tied into Gnome sessions these days that at times the problems can be hard to separate.

---

### Post by lethalfang on 2016-05-07
Thanks. I did that and it didn't help. 
I believe it must be some bad config files in my home directory that's causing this issue, because it hasn't happened with all my other computers. 
I may have a real clean install if it can't figure out what's exactly causing this annoying popup.

[Did a clean install and that annoying popup still will not stop]

---

### Post by trag on 2016-05-07
From the Software Center install "Passwords and key's" then follow these steps to disable the prompt
1)  Open Applications --> Accessories -->Password and Encryption Keys
2) Right-click on the "login" keyring
3) Select "Change Password"
4) Enter your old password and leave the new password blank
5) Press ok, read the security warning, think about it and if you still want to get rid of the Unlock Login Keyring dialog, choose "use unsafe storage"

Good Luck
Tragic

---

