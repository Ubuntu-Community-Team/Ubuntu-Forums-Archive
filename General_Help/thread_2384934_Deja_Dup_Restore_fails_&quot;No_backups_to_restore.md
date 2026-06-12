---
title: "Deja Dup Restore fails: &quot;No backups to restore&quot;"
date: 2018-02-14
forum: General Help
---

### Post by nicolasdiogo on 2018-02-14
Hello,

I posting here in case others come across this minor problem.

In my case, I backup the dejadup/deja-dup to back-up my user's home

when I tried to restore the back up onto a fresh install on the same machine I found the error

"No backups to restore"

the steps to replicate this error:
- complete a fresh installation of ubuntu
- plug a usb storage with the back-up from the previous installation
- try to restore the previous back-up
- give the directory of the previous back-up and click forward
- the Error is shown

the reason for this error seems to be the configuration of the 'Backup Tool/
the path to the location of the previous back-up *has* to be entered in the tab 'Storage Location'

then repeat the process for Restoring the back-up and everything works fine


I hope it saves others from having a 'big scare'


Regards,

---

### Post by rbmorse on 2018-02-14
Many thanks.  This is useful information, but I'm wondering,  should be reported as a bug? One ought to be able to restore from any valid backup fileset.

---

### Post by nicolasdiogo on 2018-02-16
Done!

[https://bugs.launchpad.net/deja-dup/+bug/1749984](https://bugs.launchpad.net/deja-dup/+bug/1749984)

---

### Post by peredurabefrog on 2018-07-02
I see the latest comment on the bug report is that (presumably) a dev couldn't reproduce the error on Ubuntu 16.04.  I have it on Ubuntu 18.4, so it's still a live bug.  And I'm very grateful to the OP.  I thought my data was lost for ever.

---

### Post by araruna on 2018-08-27
> **nicolasdiogo said:**
> Hello,

I posting here in case others come across this minor problem.

In my case, I backup the dejadup/deja-dup to back-up my user's home

when I tried to restore the back up onto a fresh install on the same machine I found the error

"No backups to restore"

the steps to replicate this error:
- complete a fresh installation of ubuntu
- plug a usb storage with the back-up from the previous installation
- try to restore the previous back-up
- give the directory of the previous back-up and click forward
- the Error is shown

the reason for this error seems to be the configuration of the 'Backup Tool/
the path to the location of the previous back-up *has* to be entered in the tab 'Storage Location'

then repeat the process for Restoring the back-up and everything works fine


I hope it saves others from having a 'big scare'


Regards,

Just to add a little more information. For me, in addition to entering the path in the 'Storage Location' tab, I also had to close and reopen the application in order to the changes to "commit". I don't really know why, but you can tell that you have to do this if you see a different path or storage point when you open the "restore" dialog.

---

### Post by Karti on 2018-11-24
Many thanks for this - Saved my life :)

Regards

Karti

---

### Post by t-vassallo on 2018-12-01
Saved my backup as well! Many thanks

---

### Post by denn1s-r on 2018-12-28
This really is an annoying little bug!!!

 It took me a long time to find this topic, thank you very much!

---

### Post by denn1s-r on 2018-12-28
This really is an annoying little bug!!!

 It took me a long time to find this topic, thank you very much!

I'm getting this now though...

> Invalid data - SHA1 hash mismatch for file:
 duplicity-full.20181226T212031Z.vol4.difftar.gz
 Calculated hash: 3c96aadf1c412a565da07f4b18d78751e8156bd1
 Manifest hash: bb3d25292c63a9110c83c525e003bc752f4eac86 

---

### Post by Punksolid on 2019-01-03
Hi everyone

I have the same error but I cannot reproduce the solution. 

Could someone please explain me what I'm doing wrong?

[ATTACH=CONFIG]282086[/ATTACH]
[ATTACH=CONFIG]282087[/ATTACH]

its a fresh install of deja dup, the previous machine was a manjaro with KDE with the disk encrypted, the same that the actual machine. 


Thank you

---

