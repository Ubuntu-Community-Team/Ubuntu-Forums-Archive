---
title: "Microsoft-edge not opening in ubuntu 21.10"
date: 2022-03-22
forum: General Help
---

### Post by anandharaja3 on 2022-03-22
Hi recently installed Microsoft edge in Ubuntu 21.10 but edge not opening. if i run it through terminal it shows the error **Trace/breakpoint tra **How to solve this problem?

---

### Post by QIII on 2022-03-22
What instructions did you follow to install Edge?

Would you please include the *entire* results you get from the terminal?

---

### Post by anandharaja3 on 2022-03-22
installed it from .deb file from Microsoft official website, i tried stable, beta, dev all version showing the same error.

---

### Post by QIII on 2022-03-22
Rather than posting an image of the terminal, please copy and paste the text between code tags.

While there might well be someone here who can answer your question, it is more likely that you will get help from Microsoft venues.  I see you have already asked [here]("https://techcommunity.microsoft.com/t5/discussions/edge-not-opening-in-ubuntu-21-10/m-p/3260177").  I don't know what their policy is, but you might consider bumping your thread.

I wasn't able to find much in the way of definitive help, just a lot of generalities.


To use code tags:

1. If you are using the "Reply to Thread" button, please type or paste your text, highlight the text and use the # button in the text box header. Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by deadflowr on 2022-03-22
The only references I see for this error relates to mixed up ownership issues.
Meaning somehow root is owning the wrong things.
Like this arch linux thread here: [https://bbs.archlinux.org/viewtopic.php?id=258632]("https://bbs.archlinux.org/viewtopic.php?id=258632")
(though it relates to chromium, edge is built on chromium's base.)

I have no idea what edge's config naming scheme is,
and I probably never will, so you'll need to find that out yourself.

---

### Post by anandharaja3 on 2022-03-22
I found opt folder permission is set to user not root, **drwxr-xr-x   6 anandharaja anandharaja       4096 Mar 22 19:37 opt**, How to i change this folder permission to root ?

---

### Post by deadflowr on 2022-03-23
Where is this opt?
Is it in your home folder or is it the /opt directory?

If it's the /opt directory use the chown command like so
```
sudo chown root:root -R /opt
```
Read more on Basic file permission howto here: [https://help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions")


And if by chance it's some oddball directory inside your home folder, then the ownership is usually already correct.
Most folders and files in your home folder should be owned by your user.

---

