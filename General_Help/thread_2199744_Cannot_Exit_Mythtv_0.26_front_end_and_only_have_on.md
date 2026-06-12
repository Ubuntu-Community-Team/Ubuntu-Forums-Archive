---
title: "Cannot Exit Mythtv 0.26 front end and only have one workspace ubuntu 13.04"
date: 2014-01-15
forum: General Help
---

### Post by PaulRSte on 2014-01-15
Can anyone help with this please as I have a real Catch-22 situation.  At the begining of the month I upgraded from 12.04 LTS to 12.10 and then upgraded mythtv from 0.25 to 0.26.  I then found that I had a few issues including the black screen problem when logging out of ubuntu and not being able to log back in again without powering off & on again, a persistent mythtv issue - backend setup has closed unexpectedly whilst backend and frontend are both running.  As I wanted to upgrade to myth 0.27 anyway, I thought the best path was to upgrade to 13.04 and then use mythubuntu control centre to upgrade to 0.27.

The problem is that I have the system to autologin to mythtv and the front end freezes whan I try to exit.  I cannot go into another workspace on 13.04 as I need do run a compiz change to allow multiple woirkspaces.  I cannot run this because when I exit mythtv it freezes and I have to reboot the pc and then it auto logs in to mythtv again.

Is there any way out of this?

---

### Post by steeldriver on 2014-01-15
boot into recovery mode, remount the root filesystem rw and edit the /etc/lightdm/lightdm.conf file to disable autologin?

---

### Post by PaulRSte on 2014-01-20
Edited the lightdm.conf file as above.  Only problem was that when logging in manually, it still autoran mythtv front end.  Tried looking for mythtv front end autorun instructions but found conflicting information.  I had noticed that there was a slight pause on the system between getting the desktop displayed and mythv front end starting.  I tried it again and managed to get dash running and type "settings" rtn.  Myth front end came up but alt + tab brought the settings screen into focus so I was then able to go into Appearances and re-enable workspaces.

Thanks

---

