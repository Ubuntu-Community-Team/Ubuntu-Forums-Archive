---
title: "Update causes desktop chaos"
date: 2015-02-27
forum: General Help
---

### Post by Bruv on 2015-02-27
After most updates, but not every one the icons on my desktop reaarrange themselves along the left hand side.
If I put them where I want them, after reboot they revert back again.
Strangely not all the icons line up on the left at updates, but there doesn't seem to be any logic behind which ones move.
After the next update they might be OK, or not...... it seems to happen randomly.

Any suggestions ?

---

### Post by v3.xx on 2015-02-27
This also happens to me in 15.04, what are you running?

---

### Post by Bruv on 2015-02-27
It his Ubuntu 14.04.2 LTS  Release:	14.04.
This is something that started a few months ago, thought it may have disappeared by now, it is almost amusing.

---

### Post by ajgreeny on 2015-02-27
What icons are you talking about on which DE? There are normally no icons on the unity desktop apart from the launchbar, so I am a bit uncertain what you mean.

---

### Post by Bruv on 2015-02-27
I have a browser, calculator, Skype and many other folders of stuff, many remain static while others line up to the left.

---

### Post by v3.xx on 2015-02-27
Please post
```
echo $DESKTOP_SESSION
```

---

### Post by Bruv on 2015-02-27
xubuntu

---

### Post by ajgreeny on 2015-02-27
You didn't mention xfce or Xubuntu which would have helped us answer.

Put all you icons where you want them then run command ```
sudo chattr +i /home/username/.config/xfce4/desktop/icons*
```which will make the icons* files in that folder immutable and therefore all your desktop icons should stay where they are; if they should move you can put them all back where they should be with F5 to refresh.

---

### Post by Bruv on 2015-02-28
I got this result

> chattr: No such file or directory while trying to stat /home/username/.config/xfce4/desktop/icons*

---

### Post by ajgreeny on 2015-02-28
> chattr: No such file or directory while trying to stat /home/username/.config/xfce4/desktop/icons* 			 		Sorry, I should have made myself clearer; where I showed **username** in that command I meant you to type your own username on the system, not to really type "username" which will give that error as there is no user called username.

Try again with your own username and it should work.

---

### Post by Bruv on 2015-02-28
Sorry ajgreeny, I did try as you showed me, and then substituted my user name, first time capitalised, second time not, found out my username is not capitalised.
But still no joy.
I moved the icons that move to where I want them, rebooted, but they lined up left again. 
Then I moved all icons then clicked F5 and the formerly static ones went back where they started and the other rebels drifted back to line up to the left again.
I have put the moving folders into the fixed ones and they remain fixed, take them out and they line up left again.

I find it annoying more than a major problem.

---

### Post by Bruv on 2015-02-28
I have toyed around further.
I placed one of the fixed icons elswhere and ran the command, but after rebooting it moved back.
So, it seems how the icons are placed right now, cannot be changed.

---

