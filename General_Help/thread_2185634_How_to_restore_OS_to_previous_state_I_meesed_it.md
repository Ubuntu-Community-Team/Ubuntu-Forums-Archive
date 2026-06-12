---
title: "How to restore OS to previous state? I meesed it"
date: 2013-11-03
forum: General Help
---

### Post by Manish_Kumar_Ruhil on 2013-11-03
Ok, so i was trying to install ATI media accelerator. Doing so from "additional drivers" in "system settings" did installed it but it was not currently in use. Than i download driver from HP websites (my laptop is of HP), extracted it and pasted it in file system by opening file manager in admin privelege. and after restart OS boot up and than comes black screen with just a "-" sign on top left. on doing hard restart and running "previous linux version" it boot up whithout any issue and load it to previous shut down state and I can use my laptop error free. But i have to select "previous linux version" every time. Is there a way I can restore to previous version permanetly.

Thank you!

---

### Post by deadflowr on 2013-11-03
What exactly and where exactly did you paste the HP stuff?

Simply copying and pasting files into various folders, with root or not shouldn't affect how the system works.
Unless the pasted file contains code specific to the system.

As far as the driver being installed but not in use, you need to initialize the driver.
Looky here
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Manish_Kumar_Ruhil on 2013-11-03
I Downloaded graphic driver from here:
[http://h20566.www2.hp.com/portal/site/hpsc/template.PAGE/public/psi/swdHome/?sp4ts.oid=5359422&spf_p.tpst=swdMain&spf_p.prp_swdMain=wsrp-navigationalState%3DswEnvOID%253D2020%257CswLang%253D%257Caction%253DlistDriver&javax.portlet.begCacheTok=com.vignette.cachetoken&javax.portlet.endCacheTok=com.vignette.cachetoken](http://h20566.www2.hp.com/portal/site/hpsc/template.PAGE/public/psi/swdHome/?sp4ts.oid=5359422&spf_p.tpst=swdMain&spf_p.prp_swdMain=wsrp-navigationalState%3DswEnvOID%253D2020%257CswLang%253D%257Caction%253DlistDriver&javax.portlet.begCacheTok=com.vignette.cachetoken&javax.portlet.endCacheTok=com.vignette.cachetoken)

and pasted in files in following directory (also replaced some files):
1. etc
2. lib
3. usr
4. var

I am looking in link provided by you...

---

### Post by deadflowr on 2013-11-03
As far as I see the drivers you downloaded are only for SUSE. Not Ubuntu.
Which probably explains the problems.
It's unclear where the bits and pieces where placed.
But what is clear is that those files you got from HP need to be removed.
However, since you stated that some of those files replaced files on the system, you would need to also reinstall the files/packages they replaced.

Do you know which files where installed?
Could you post a list?

---

### Post by Manish_Kumar_Ruhil on 2013-11-03
Well I known which files were copied and I can remove them (just a couple hundred files :D) but its is practical impossible to type them here. Also problem is, even if i will remove them than how can I get back original files:confused: . 

Also, is there a way to simply restore becuase I am using option "run previous linux" at boot and OS boot just fine. Just exactly how it was before recent incident, I can tell that because I installed skype second last time and it is displaying (and also cutom background).

---

### Post by deadflowr on 2013-11-03
Unfortunately, I don't know what files went where.
But My thoughts on it are that you messed up the linux-headers which are located in the /usr directory, with modules in the /lib directory.

The boot directory contains the linux-image files, which are what runs the base system, but from what I understand, if you need to run extra modules then you need the linux-headers and linux-headers-generic packages.
So the image and the headers relate to each version, so that image 3.1 will use headers 3.1 but won't use headers 3.2 or something else.
So since you only borked the headers for one, the older one was left untouched.

Of course this all my own speculation and can not be held as sacrosanct.
I could be completely or even mostly wrong.
Which I probably am.

---

