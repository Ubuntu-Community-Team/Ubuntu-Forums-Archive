---
title: "root.disk file lost, cannt start ubuntu, stop at Busybox when logon."
date: 2008-06-06
forum: General Help
---

### Post by yew98 on 2008-06-06
I cannt login to ubuntu this morning, the screen show me only "Busybox v1.1.3........".
I check the log ubuntu gives me and find it cannt find /host/ubuntu/disks/root.disk.
I knows it is the virual disk created by wubi, and i find it looks like be removed when i restart to windows xp.
I sware I never delete this file before.
I use FinalData and find all the things I installed in ubuntu are still there.

Is there any know anything about this problem?
Thank you in advanced.

ps: I use wubi install ubuntu 8.04 in WinXP SP3. It's work pretty well until this morning.

---

### Post by beanhead on 2008-06-06
I went through the same thing. It was because the partition i was installing on was formatted in fat 32. in your windows partition go to My computer,right click select manage, then disk management. It will show your drives if its not formatted as ntfs format it as such. That fixed my problem and I hope it works for you. :D, Ron:guitar:

---

### Post by yew98 on 2008-06-06
thanks beanhead, but i have used ntfs already.
I try to use chkdsk command and disk check tool supplied by windows, but both methods fail.
I am pool in english, and i just cannt descible how bad i feel.................

---

### Post by ago on 2008-06-06
see if there are hidden files named "found.0000" in C:\ or C:\ubuntu

---

### Post by shantanubhadoria on 2008-10-30
Ok here is something you guys could try . . .

boot up in windoz and fire the command prompt
go to the drive where the wubi/ubuntu is installed
I: for me

>I:

then run 'chkdsk /r'
I:>chkdsk /r

if you are lucky the damage is not big. I had a couple of bad clusters and rougue indexes. 

Best of luck :)

-----------------------------------------------------------------------------------------
Correction don't do this chkdsk ended up removing my root.disk for errors. I suffered mega damage to my work and deadlines.

---

