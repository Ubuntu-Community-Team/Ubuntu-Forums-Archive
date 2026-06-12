---
title: "Gusty &amp; CD/DVD Burning question"
date: 2007-10-08
forum: General Help
---

### Post by crackerizer on 2007-10-08
Hello everybody,
I have a very bad time with CD/DVD burning on feisty. It only burns at 2x. I tried every solutions I found but none of them works. I've heard a lot of good things in gusty. So, does CD/DVD burning works as it should do on gusty? Is there anybody try it yet? Please tell me your story... Thank you..:confused:

---

### Post by dptxp on 2007-10-08
try K3B , it is in add/remove. KDE libraries needed shall automatically be added.

---

### Post by crackerizer on 2007-10-08
Hello dptxp,
I've tried every burning programs(k3b, gnomebaker, nero). All of them only burn at 2x. I think there are a lot of people who have the same problem as me out there. Dont you have this problem?

---

### Post by dptxp on 2007-10-08
Never had a problem, in auto mode K3b burns images at about 20X.
Do not try Gutsy till final release.
Maybe it is a CD drive / driver or media problem. You can try with other drives or same drive with
other OS, on some other machine.

---

### Post by ericartman on 2007-10-08
Never had a speed problem in Feisty or Gutsy, I mainly use K3b also. BTW this is on my test beds (2) and my production machine. While my test beds are offer up slower speeds they are older units. Have no idea what could cause your problem though, good luck.

Cart

---

### Post by matigol on 2007-10-08
I already have the same problem.
I changed my CD, and it works perfectly.

I think i used a cd of bad quality...

Now, i use Sony and it works perfectly.

---

### Post by anaconda on 2007-10-08
Feisty used scsi- drivers for ide CD/DVD-drives, and with some people this caused no end of problems.

There was a way to switch back to using ide drivers for ide drives... logical.

I thin (and hope) that gutsy has moved back to ide drivers.

I will post the link here if I find it.
[http://ubuntuforums.org/showthread.php?t=515568&highlight=no+cd%2FDVD+writer&page=2](http://ubuntuforums.org/showthread.php?t=515568&highlight=no+cd%2FDVD+writer&page=2)
I think this was it. Read carefully. somewhere there should be instructions in how to move back to ide drivers..

---

### Post by crackerizer on 2007-10-10
anaconda,
Thank you, i'll try to change the driver back to ide and will post the report. :)

---

### Post by Phearicle on 2007-10-10
Brasero FTW! :lolflag:

---

### Post by RT236 on 2008-03-01
After I upgraded awhile ago to Gusty, K3B would not verify although the write to CD data was fine...  Tonight, I had a chance to investigate some.

I noticed the CD was ejected after write completed, but did not reload for verify.  This is a really simply fix I found...  namely, in Advanced Settings I checked/set "do not eject medium after write process."  Now, it is verifying perfectly and all is working correctly as in the past before the Gusty upgrade, although, now I have to do a manual eject after verify.  Unchecked/unset was the default setting  First time I've run into this, also have used K3b on SuSE for a long time and also earlier Ubuntu releases.

My drive is a Plextor PX-716A.  Yes, it's a simple fix, but I was starting to dig too deeply...  hope this helps someone if having similar problem...  Duane

---

### Post by RT236 on 2008-03-01
After I upgraded awhile ago to Gusty, K3B would not verify although the write to CD data was fine...  Tonight, I had a chance to investigate some.

I noticed the CD was ejected after write completed, but did not reload for verify.  This is a really simply fix I found...  namely, in Advanced Settings I checked/set "do not eject medium after write process."  Now, it is verifying perfectly and all is working correctly as in the past before the Gusty upgrade, although I just simply do a manual eject after verify.

My drive is a Plextor PX-716A.  Yes, it's a simple fix, but I was starting to dig too deeply...  hope this helps someone if having similar problem...  Duane

---

