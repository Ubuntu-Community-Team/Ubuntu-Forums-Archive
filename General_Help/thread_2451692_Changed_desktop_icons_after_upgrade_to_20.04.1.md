---
title: "Changed desktop icons after upgrade to 20.04.1"
date: 2020-10-09
forum: General Help
---

### Post by David_Partridge on 2020-10-09
After upgrading to 20.04.1 some of my desktop have acquired exclamation marks:

[ATTACH=CONFIG]287130[/ATTACH]
and when I d'click them I get a prompt like this:
[ATTACH=CONFIG]287129[/ATTACH]
What's wrong, and how to fix please?

---

### Post by &amp;KyT$0P# on 2020-10-10
Please post the output from running the following command in Terminal -
```
ls -la ~/Desktop
```

---

### Post by David_Partridge on 2020-10-10
Here you go:

```
amonra@Charon:~$ ls -la ~/Desktop
total 36K
drwxr-xr-x 1 amonra amonra  1K Oct 10 17:34 .
drwxr-xr-x 1 amonra amonra  2K Oct 10 17:34 ..
-rw-rw-r-- 1 amonra amonra  1K Oct 10 17:34 computer.desktop
-rw------- 1 amonra amonra  1K Mar 31  2016 evince.desktop
-rw-r--r-- 1 amonra amonra 10K Sep 17 09:41 firefox.desktop
-rw-rw-r-- 1 amonra amonra  1K Oct 29  2018 lxterminal.desktop
-rw-rw-r-- 1 amonra amonra  1K Oct 10 17:34 network.desktop
-rw-rw-r-- 1 amonra amonra  1K Oct 10 17:34 trash-can.desktop
-rw-rw-r-- 1 amonra amonra  1K Oct 10 17:34 user-home.desktop
amonra@Charon:~amonra@Charon:~$ ls -la ~/Desktop
total 36K
drwxr-xr-x 1 amonra amonra  1K Oct 10 17:34 .
drwxr-xr-x 1 amonra amonra  2K Oct 10 17:34 ..
-rw-rw-r-- 1 amonra amonra  1K Oct 10 17:34 computer.desktop
-rw------- 1 amonra amonra  1K Mar 31  2016 evince.desktop
-rw-r--r-- 1 amonra amonra 10K Sep 17 09:41 firefox.desktop
-rw-rw-r-- 1 amonra amonra  1K Oct 29  2018 lxterminal.desktop
-rw-rw-r-- 1 amonra amonra  1K Oct 10 17:34 network.desktop
-rw-rw-r-- 1 amonra amonra  1K Oct 10 17:34 trash-can.desktop
-rw-rw-r-- 1 amonra amonra  1K Oct 10 17:34 user-home.desktop
amonra@Charon:~$ 

amonra@Charon:~/Desktop$ cat lxterminal.desktop
[Desktop Entry]
Type=Link
Name=LXTerminal
Icon=lxterminal
URL=/home/amonra/.local/share/applications/lxterminal.desktop
amonra@Charon:~/Desktop$

```

David

---

### Post by &amp;KyT$0P# on 2020-10-10
Try
```
chmod +x ~/Desktop/lxterminal.desktop
```

Does the LXTerminal icon now work as you expect?

---

### Post by GhX6GZMB on 2020-10-10
It would help incredibly if you announced which flavour you're using. It's not hard. You can even place it in your profile.

As you have references to LX, I suppose it's Lubuntu.

In that case, removing the exclamation marks is easy.

Richt-click on the icon, a menu should pop up.
Tick the field "Trust this executable".
Done.

If this doesn't work, delete the icon and drag the corresponding icon from the Application Menu onto the desktop again. Repeat above.

---

### Post by David_Partridge on 2020-10-10
No change, and none of the other desktop files have the execute bit set.

D.

---

### Post by &amp;KyT$0P# on 2020-10-10
Can you please also post the output from running this command in Terminal? -
```
ls -la ~/.local/share/applications
```

---

### Post by GhX6GZMB on 2020-10-10
Something's completely off with this setup.
LXTerminal belongs to the 18.04 Lubuntu installation and should not appear in a Lubuntu 20.04 setup, which uses QTerminal.
Sounds to me like a failed 18.04 to 20.04 upgrade, which is strongly discouraged due to the change from LXDE to LXQt. A fresh installation is the right way to do it.

Concerning the exclamation point: already answered in post #5, but only pertinent to LXQt.

Or am I ignorant of a distro that runs 20.04 with LXDE? Educate me, please.

---

### Post by David_Partridge on 2020-10-11
> **ml9104 said:**
> Something's completely off with this setup.
LXTerminal belongs to the 18.04 Lubuntu installation and should not appear in a Lubuntu 20.04 setup, which uses QTerminal.
Sounds to me like a failed 18.04 to 20.04 upgrade, which is strongly discouraged due to the change from LXDE to LXQt. A fresh installation is the right way to do it.

Concerning the exclamation point: already answered in post #5, but only pertinent to LXQt.

Or am I ignorant of a distro that runs 20.04 with LXDE? Educate me, please.

Failed upgrade - it looked like it went just peachy here.    Was it supposed to uninstall LxTerminal?  Somehow I don't think that's likely.

No one told me that this was strongly discouraged.   I was just offered the upgrade to 20.04.1.   

If something is strongly discouraged,. you NEED TO SAY SO AND PROVIDE COMPELLING REASONS.  Something like:

************* WARNING WILL ROBINSON - WARNING ***********
 You are attempting to upgrade from 18.04 to 20.04 and we really don't think this is good idea and here is why:

 Explanation of why it would be a REALLY bad idea

**************************************************************************
BUT!   In any case a full reinstall on Lubuntu plus all the tailoring and additional apps I have installed over time - just not going to happen  I don't have a detailed log book of every little bit of tailoring or additional apps installed - mea culpa.. .

Sorry but the approach of an full reinstall is needed is just not going to wash with me and millions of others.

Yes I have on occasion done complete re-installs of operating systems from the ground up, but that was in the Jurassic era - for goodness sake we are now 12020 years into the Holocene era - we can do better now.

---

### Post by David_Partridge on 2020-10-11
> **ml9104 said:**
> It would help incredibly if you announced which flavour you're using. It's not hard. You can even place it in your profile.

As you have references to LX, I suppose it's Lubuntu.

In that case, removing the exclamation marks is easy.

Richt-click on the icon, a menu should pop up.
Tick the field "Trust this executable".
Done.

If this doesn't work, delete the icon and drag the corresponding icon from the Application Menu onto the desktop again. Repeat above.

Yes that worked but I also had to do the same to ALL the desktop entries in .local/shared/applications 

Please could you explain why all the desktop entries I created yonks ago are suddenly untrustworthy. IOW what is the motivation for this behaviour - which you say is specific to LXQt - seems to me that if no other DM does this that it's not very useful.

D.

---

### Post by GhX6GZMB on 2020-10-11
I've no idea. I'm not a developer, just another Lubuntu user trying to help.

---

