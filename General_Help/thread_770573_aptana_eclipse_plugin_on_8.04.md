---
title: "aptana eclipse plugin on 8.04"
date: 2008-04-27
forum: General Help
---

### Post by jsgarvin on 2008-04-27
It' looks like there may be an issue installing the Aptana plugin for Eclipse on 8.04.

[http://forums.aptana.com/viewtopic.php?p=20418#20418](http://forums.aptana.com/viewtopic.php?p=20418#20418)

I'm not sure if it's a Ubuntu issue or an Apatana issue at this point so I figured I'd post here to see if anybody had any brilliant ideas.  Maybe it's some new security setting in Ubuntu???

The instructions that I, and I assume the others, are following are here...

[http://update.aptana.com/update/3.2/](http://update.aptana.com/update/3.2/)

and the error occurs between steps 6 and 7.


[[img]http://img2.freeimagehosting.net/uploads/th.9894af756a.png[/img]](http://img2.freeimagehosting.net/image.php?9894af756a.png)

---

### Post by Lashiec on 2008-04-27
I just got the Aptana plugin for Eclipse and installed the PHP addon... Ubuntu 8.04. I didn't run into and problems. I also did this with the beta 5 of 8.04 a month ago.

---

### Post by jsgarvin on 2008-04-27
Well, that's interesting.  What's the "Remote Site" URL you're using in Eclipse to install Apatana?  I"m using...

[http://update.aptana.com/update/3.2/](http://update.aptana.com/update/3.2/)

Thanks.

---

### Post by Lashiec on 2008-04-27
[http://update.aptana.com/update/3.2](http://update.aptana.com/update/3.2)

That's the one that I used... I'm using the x64 version of Ubuntu.

---

### Post by jsgarvin on 2008-04-27
Ok, I think I found the "workaround" (if you can call upgrading Eclipse a workaround)...

It appears to me that the issue is related to the particular build of Eclipse in the 8.04 32bit repositories.  Based on the very last comment (at the moment) on this page...

[http://support.aptana.com/asap/browse/STU-392](http://support.aptana.com/asap/browse/STU-392)

I downloaded the latest Eclipse (3.3/Europa) directly from the Eclipse site.  After starting it up it did what started to look like an infinite loop of trying to update Mylyn, but after 4 restarts it finally finished.  Then I added Aptana as a remote site, and it installed and then wanted to immediately update itself.  It did install though and I also got the RadRails plugin to install install as well.

It's rather frustrating that Eclipse 3.3 has been released for nearly a year, and the very latest Ubuntu is still stuck on 3.2.

---

### Post by MystaMax on 2008-05-04
> **Lashiec said:**
> I just got the Aptana plugin for Eclipse and installed the PHP addon... Ubuntu 8.04. I didn't run into and problems. I also did this with the beta 5 of 8.04 a month ago.

I was able to get aptana studio plugin installed on ubuntu 8.04 beta, but not with a fresh install of the final release.

I'm still having this problem today.

In the meantime, I downloaded and installed the full Aptana Studio Install. It works, but the built in browser preview feature doesn't work. I haven't had time to follow the [Aptana wiki instructions]("http://www.aptana.com/docs/index.php/Installing_Aptana_on_Linux#Installing_Aptana_Studio_on_Debian") on getting firefox to work w/ aptana studio.

---

### Post by woomg on 2008-06-22
Hi...

I had a same problem on my Hardy AMD64, and fixed as follow.
This problem related with GCJ packages. So you need to uninstall these packages from your PC, and then install eclipse...

1. Uninstall "GCJ", in my case "sudo apt-get autoremove --purge gcj-4.2-base"
2. Install "Sun Java6(jdk, jre)" from apt-get or 'Synaptic Package Manager'
3. Install 'Eclipse'
4. Install 'Aptana' from 'Update Manager' with 'Remote Site'
5. Install additional packages you needed.(PHP toolkit, RadRails, Adobe AIR..)

Thanks,
MG

---

### Post by MystaMax on 2008-06-23
THANKS MG!, very helpful. I'm really surprised it took this long to find a fix, but grateful there is one. I began searching for another IDE / text-editor and came across [openkomodo.com]("http://www.openkomodo.com/"). It definitely isn't as full featured as Aptana, but is a good alternative.

BTW, I already had eclipse installed, and didn't need to remove it. I just uninstalled gcj-4.2-base, installed jre6 and jdk6, and rebooted eclipse. I then followed the instructions below to get aptana plugin to work:

[http://www.aptana.com/docs/index.php/Plugging_Aptana_into_an_existing_Eclipse_configuration](http://www.aptana.com/docs/index.php/Plugging_Aptana_into_an_existing_Eclipse_configuration)

Thanks again MG!

---

