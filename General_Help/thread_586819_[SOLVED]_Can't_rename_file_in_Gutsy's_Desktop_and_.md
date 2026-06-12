---
title: "[SOLVED] Can't rename file in Gutsy's Desktop and Nautilus? See here."
date: 2007-10-22
forum: General Help
---

### Post by jenhsun on 2007-10-22
[PROBLEM'S SYMPTOM]

Here are the combination of problem conditions arise from:

<Condition A>
SCIM ON + Desktop for Complex Characters Input-----> Freeze
Solution: Kill SCIM

<Condition B>
SCIM ON + Nautilus for Complex Characters Input ------> Freeze
Solution: Kill SCIM

<Condition C>
SCIM ON + Applications ( Firefox, OpenOffice, Terminal...etc) for Complex Characters Input ---> Good

If Condition C plus A or B (do thing at the same time) ----Freeze.
Solution: Kill SCIM

I think the bug location is very clear now. It might be in between the application and global environment level.
Probably the recent add-in of language support in Gutsy version.

During these testing, I did get the worst scenario: my all file icons in my desktop all gone, the logout doesn't work.
I have to do the manual power off and on.

Same problem in different machine: 32 and 64 bits, both different Graphic Card (Intel and nvidia)
[https://bugs.launchpad.net/ubuntu/+bug/153233](https://bugs.launchpad.net/ubuntu/+bug/153233)

---

### Post by jenhsun on 2007-10-28
[SOLVED]

Problem solved.

Please take a look at this bug report
[https://bugs.launchpad.net/ubuntu/+bug/34282](https://bugs.launchpad.net/ubuntu/+bug/34282)
or below #6
And the most important is the document in your
/usr/share/doc/scim/README.Debian.gz

If nothing wrong with your keyboard input and your system but only the input of complex characters, you should take a look into the scim documents.
I think I made a big mistake not doing this.

---

### Post by kstan_79 on 2007-10-28
As jensun mentioned, I restart scim then thing come back normal. To make my life easier I do following scrip:

~/bin/restartscim.sh

> 
#!/bin/bash
#filename = restartscim.sh

killall -9 scim scim-launcher
scim -d


create a custom application launcher at gnome-taskbar.

When something wrong come out I just click the short cut at task bar. So far I use it happily.

regards,
Ks

---

### Post by jenhsun on 2007-10-28
> **kstan_79 said:**
> As jensun mentioned, I restart scim then thing come back normal. To make my life easier I do following scrip:

~/bin/restartscim.sh



create a custom application launcher at gnome-taskbar.

When something wrong come out I just click the short cut at task bar. So far I use it happily.

regards,
Ks

Great post, dude.
However, the problem is not that simple.

---

### Post by dmontalvao on 2007-10-31
> **kstan_79 said:**
> As jensun mentioned, I restart scim then thing come back normal. To make my life easier I do following scrip:

~/bin/restartscim.sh



create a custom application launcher at gnome-taskbar.

When something wrong come out I just click the short cut at task bar. So far I use it happily.

regards,
Ks

Didn't solve for me and I can't access the desktop icons. lol.

---

### Post by jenhsun on 2007-10-31
I think we got a winner. Here you go.
[http://ubuntuforums.org/showpost.php?p=3676161&postcount=6](http://ubuntuforums.org/showpost.php?p=3676161&postcount=6)

The problem he present doesn't show in SCIM document.
I think this kind of (XIM to GTK Module) bug also exist in realplayer because some people can't run realplayer 10 client, I mean even open the player. 
The solution is to change the /usr/bin/realplay
on the next line of #!/bin/sh, type
export GTK_IM_MODULE=xim


The SCIM is opposite, that's funny.

---

### Post by ELMIT on 2007-11-21
To restart did not help me to get typing back.

I had to stop (kill) and not to restart SCIM.

Fortunately I do not need SCIM often, so I can start it when I really need it.
Thanks to point out what to do.


bye

Ronald

---

