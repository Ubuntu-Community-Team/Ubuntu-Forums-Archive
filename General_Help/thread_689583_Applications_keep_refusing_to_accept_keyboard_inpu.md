---
title: "Applications keep refusing to accept keyboard input"
date: 2008-02-06
forum: General Help
---

### Post by HangukMiguk on 2008-02-06
Ever since I updated to Gutsy, I have been having this problem.  It occurs mostly with GTK programs, but I've noticed a few KDE programs this will happen with, as well as others.

Here's what happens, I will be using a program normally, then all of a sudden, it will refuse to accept keyboard input.  It happens randomly, and I cannot give you a rhyme or reason for why this happens.

Also, other programs will work fine during this issue, so it's most likely not hardware related.

Programs this happens with:
Pidgin
Yakuake (I'm assuming, but haven't checked to see, that Konsole would also do this)
Opera (NOTE: Opera literally runs 10 seconds before refusing to accept keyboard input)
Epiphany
Rhythmbox
Galeon
GIMP
Wine applications

Programs this doesn't happen with:
Konqueror
Kopete
Firefox
xterm

Any help you guys could provide.  Any additional info, steps you'd want me to take to help pinpoint the problem, let me know.

---

### Post by pieisgood4589 on 2008-02-06
Try resetting the GNOME desktop. 

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

Don't worry, it just deletes the GNOME run data, so on the restart, it will create the default ones.

IT WILL NOT REMOVE YOUR ENTIRE FILESYSTEM. I tried it. I promise.:popcorn:

---

### Post by HangukMiguk on 2008-02-06
> **pieisgood4589 said:**
> Try resetting the GNOME desktop. 

```
rm -rf .gnome .gnome2 .gconf .gconfd .metacity
```

Don't worry, it just deletes the GNOME run data, so on the restart, it will create the default ones.

IT WILL NOT REMOVE YOUR ENTIRE FILESYSTEM. I tried it. I promise.:popcorn:
I'm running through KDE right now, will this crash any GTK apps?

Doubt it, but just checking beforehand.

---

### Post by jbsongaku on 2008-02-10
I have a similar problem. After reading around I'm starting to think it is related to the SCIM package. The solution I have found for SOME applications, is that on some text fields, for example, when you change the filename in Nautilus and find out you cannot input anything, it is useful to right click, go for input methods and change to DEFAULT.

Unfortunately, this doesn't work in firefox and other applications... I wonder if there is any way to change this for good...

---

### Post by yingzhou on 2008-02-11
how to remove the SCIM package? I dont like it so much?

---

### Post by jbsongaku on 2008-02-11
The SCIM has caused me some trouble, but I need it to input Japanese. Unless there is another IME package around. Anthy alone doesnt fit my needs

---

### Post by HangukMiguk on 2008-02-11
heh...I also use SCIM.

Would changing to SKIM fix anything?

I'm guessing it's the only one for Japanese?  I mainly use it for Korean though.  Any decent alternatives?

---

### Post by jbsongaku on 2008-02-12
I wonder if it is a specific ubuntu problem, or a gnome problem. In the University they use KNOPPIX with KDE. They use SCIM to input japanese and I have never had any problem like this...

---

### Post by mactalla on 2008-02-12
> **HangukMiguk said:**
> Ever since I updated to Gutsy, I have been having this problem.  It occurs mostly with GTK programs, but I've noticed a few KDE programs this will happen with, as well as others.
...
Programs this doesn't happen with:
Konqueror
...


Just a "me, too" except I run Kubuntu with very few gtk apps, so i cannot comment on those, but I have had it happen in Konqueror, so it's not immune.

[QUOTE=jbsongaku]I have a similar problem. After reading around I'm starting to think it is related to the SCIM package. The solution I have found for SOME applications, is that on some text fields, for example, when you change the filename in Nautilus and find out you cannot input anything, it is useful to right click, go for input methods and change to DEFAULT.[/QUOTE]

THANK YOU!  I didn't think about that.  I had one window that was giving me this problem just now and when I checked the input method it was listed as XIM.  Changing it to SCIM let me type again.

---

### Post by seshomaru samma on 2008-02-17
I have this problem as well . I think it's a Gutsy bug . To me it only happens in Opera, it never happened in Feisty or Dapper . My friend just installed Gutsy and has teh same problem. We are both running SCIM and Gnome.

---

### Post by forumboy on 2008-03-04
Please read teh solution of this article, it work for me. [http://ubuntuforums.org/showthread.php?t=705233&highlight=scim+cannot+input](http://ubuntuforums.org/showthread.php?t=705233&highlight=scim+cannot+input)

---

