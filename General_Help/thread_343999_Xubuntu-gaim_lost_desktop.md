---
title: "Xubuntu-gaim lost desktop"
date: 2007-01-22
forum: General Help
---

### Post by DougieFresh4U on 2007-01-22
I have like 3 or 4 problems. 
**Problem #1**I have been trying to get the real AIM without success. so I thought I would do an upgrade to gaim 2.0 beta 6. when I followed Rapidshare it removed my gaim anbd Xubuntu desktop** (my fault for not paying attention to what was being removed)** So I would like to repair damage I did, but it will not let me re-install Xubuntu-desktop                                                                               **Problem #2** I cannot shut down using the "Quit" button. I click on it and nothing happens-any help with this one?                                                                                    **Problem #3** At the login screen it ask for user name, then password then a little window pops up with the following message::**User's $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writable by other users**. Any one have a clue as to what that is all about??:frown:

---

### Post by taurus on 2007-01-22
1.  ```
sudo aptitude update
sudo aptitude install xubuntu-desktop
```

2.  Could be related to Q 1.

3.  ```
cd ~
sudo chmod 644 ~/.dmrc
```

---

### Post by DougieFresh4U on 2007-01-22
when I go to Applications>Quit, nothing comes up for me to select whether I want to resatart or quit , nothing. Thanks for the help with putting Xubuntu-desktop back. I guess I still have to keep Windows XP around for games as well as AIM

---

### Post by DougieFresh4U on 2007-01-22
Ok , problem #1 solved. I still can not shut down as when I click "Quit" nothing comes up. How do I shut down from terminal until I can get this fixed??[-o<

---

### Post by taurus on 2007-01-22
```
sudo shutdown -h now
```

---

### Post by DougieFresh4U on 2007-01-22
Thank very much taurus. Why will no one let me know how to fix the problems I have stated? I still have that message upon start up and no shut down menu:frown:

---

### Post by taurus on 2007-01-22
I have to turn on my laptop since I have Xubuntu on that but since it's late and I am about to go home (shower and sleeeeeeeeeeeeeep), I can't check about the shutdown menu for you but I can shutdown my laptop last week alright when I used it.

---

