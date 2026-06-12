---
title: "Nautilus freezes"
date: 2007-10-22
forum: General Help
---

### Post by grantwfuller on 2007-10-22
I have just upgraded to Ubuntu 7.10. I had been using Konqueror as a file browser because I had problems with Nautilus freezing for no apparent reason in feisty fawn. After the upgrade, the file browser froze after it opened and I was trying to expand a folder. Sometimes it freezes but allows me to use other programs from the desktop launchers, other times the desktop icons vanish. And other times everything freezes solid and I need to shut off the power. On reboot, things go back to normal until I try to access "Places>Home" and begin managing folders. I took Konqueror off (uninstalled) in case that created a conflict but Nautilus is still not working right. My computer is a Compaq Presario and originally came with Windows XP. That has since crashed and I went to Ubuntu 6.10, upgraded to 7.04 and now to 7.10. 
Is there any way to find the conflict or problem, or can I unistall Nautilus and switch to Konqueror with this new upgrade? any ideas?

---

### Post by BruisedQuasar07 on 2007-10-22
Have you considered visiting linuxcd.org and ordering Ubuntu 7.04 
on a professional quality burned CD for $1.95? and doing a 
complete, fresh install? 

If you decide to do so, be sure to examine and clean the CD before you 
use it, so a defect or debris doesn't cause you hours of hair pulling and
wondering if Linux is for you. 

I've tracked down so many insane problems friends complained to me 
about to simple cd problems that when I hear new install and insane 
behavior I immediately want to examine the CD. This was for Windows
 systems but CDs are CDs. 

In the Linux world, I've read many strange problems reported by newbies 
tracked down by experienced users to an ISO  download error, misunderstanding 
of how to burn an ISO, or a simple CD problem.

--Bruised

---

### Post by grantwfuller on 2007-10-22
I had not considered the CD as the problem, I guess because Ubuntu had worked so well for so long. However, you have me thinking that this would be a good idea. You mention getting 7.04, does that mean that 7.10 is more of an adventure than a "bug fix" version? I'll start with 704 and get the upgrade when available. Upgrading over the internet was a painfully slow process, it took about 20 hours on a cable connection.

---

### Post by seventyeights on 2007-10-22
Maybe your download is borked? It won't hurt to check the md5sum.

---

### Post by grantwfuller on 2007-10-23
I don't have a clue how to check the md5sum or what it is. I have ordered the new 7.10 CD but if you can explain a bit about things to chec and how to go about it,  I could try that in the meantime. thanks all.

---

### Post by grantwfuller on 2007-11-01
"Have you considered visiting linuxcd.org and ordering Ubuntu 7.04
on a professional quality burned CD for $1.95? and doing a
complete, fresh install? " 
I bought the CD for 8.95 and received it yesterday. I now find out that I can't reinstall Ubuntu without losing all my data. One bit of forum advice suggests I put my home folder on a separate partition, then I might be able to preserve my files. All I want is a URL to a tutorial that will help me  to get a file browser working properly whether it can be fixed, fresh reinstall, partly reinstalled or files retrieved from a back up after an install? I would like to do it right because this is my last hope before I go back to Windows.

---

### Post by grantwfuller on 2007-11-04
I launch Nautilus from "Places > Home" and then expand the home directory. It usually gets as far as expanding the folder list but then when trying to open a folder, it freezes. The whole screen except for the cursor goes dead, meaning I can't shut down the computer or open other apps.  I need to pull the plug and start over. I can get to the files if I go through a program such as Gimp. I can launch Gimp and go to File Open and access the graphics files. I can use open office and text editor for accessing most other files but I can't rearrange or delete with this work around. Any help would be appreciated but this looks hopeless to me.

---

### Post by JJNova on 2007-11-04
You are not alone with this problem. I believe the problem is with a filename problem inside of the directory. This happens whenever I look into a directory with music files, where generally have a lot of underscores ( _ ) as well as other less commond characters ( & / * ) in the filenames. You can still access the directory perfectly fine if you go through the Terminal. If you don't like the command line, you can install Thunar as a file browser.

If you wind up liking Thunar, and want it to be your default file browser (so that it opens instead of Nautilus when you click HOME) then just follow the steps at this URL - [http://psychocats.net/ubuntu/nonautilusplease](http://psychocats.net/ubuntu/nonautilusplease)

The problem was so persistent that I just wound up replacing Nautilus. Now everything works great! Hope this is of assistance.

---

