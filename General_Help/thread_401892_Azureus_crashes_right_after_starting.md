---
title: "Azureus crashes right after starting"
date: 2007-04-05
forum: General Help
---

### Post by statictonic on 2007-04-05
Whenever I run azureus is exits after a couple seconds, I can delete the config file and get it working again, but then after about 10 minutes it exits, and the problem reoccurs.

I ran it in the terminal to see what the problem was, i got the following when it closed.  Any ideas on fixing this?

# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb05a3d02, pid=10485, tid=3085194928
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_08-b03 mixed mode, sharing)
# Problematic frame:
# C  [libglibjni-0.4.so+0x8d02]
#
# An error report file with more information is saved as hs_err_pid10485.log
#
# If you would like to submit a bug report, please visit:
#   [http://java.sun.com/webapps/bugreport/crash.jsp](http://java.sun.com/webapps/bugreport/crash.jsp)

---

### Post by tommcd on 2007-04-05
Which azureus did you install? The one in the ubuntu repos depends on java and has been known to have problems from what I read.
If you are using the one from the repos uninstall it and install it by the "Alternative Method" listed here:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_P2P_BitTorrent_Client_.28Azureus.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_P2P_BitTorrent_Client_.28Azureus.29)
This works fine. If you have trouble getting updates for this azureus do in terminal:
cd /opt
sudo chown your_user_name:users -R azureus
Then get the updates. Hope this helps.

---

### Post by sunset_studies on 2007-04-06
My Azureus worked fine for months, then crashed once, then displayed the 'crash after a few seconds' behaviour. This fix worked for me:

rm  .azureus/.lock
rm .azureus/logs/*.log
rm .azureus/logs/save/*


thanks to slayerboy for this.

---

### Post by vratnica on 2007-04-07
> rm .azureus/.lock
rm .azureus/logs/*.log
rm .azureus/logs/save/*

This works great!

Thank you!

---

### Post by Nachimir on 2007-04-07
Thak you very much sunset_studies, I've had this occur a few times and that just sorted it right out.

---

### Post by UbuntuniX on 2007-04-08
> **sunset_studies said:**
> My Azureus worked fine for months, then crashed once, then displayed the 'crash after a few seconds' behaviour. This fix worked for me:

rm  .azureus/.lock
rm .azureus/logs/*.log
rm .azureus/logs/save/*


thanks to slayerboy for this.

Thanks, that worked great!

Oddly, the first time I ran Azureus after trying that, it crashed after about thirty seconds.

I tried "rm  .azureus/.lock", now it's fine. :D

---

### Post by Zer0Nin3r on 2007-05-13
> **sunset_studies said:**
> My Azureus worked fine for months, then crashed once, then displayed the 'crash after a few seconds' behaviour. This fix worked for me:

rm  .azureus/.lock
rm .azureus/logs/*.log
rm .azureus/logs/save/*


thanks to slayerboy for this.
Thanks for the help.

---

### Post by roadrocket13 on 2007-05-13
thank you, worked like a charm :guitar:

---

### Post by SpeakerForTheDead on 2007-05-15
I was having the same problem... your fix worked like a charm. Thanks!

---

### Post by BLTicklemonster on 2007-05-16
Mine crashed, too. So I uninstalled it and run amule now.

---

### Post by asymmetric on 2007-05-17
cool, it worked perfectly :)

thanks!!

---

### Post by Zer0Nin3r on 2007-05-21
How do you like aMule?

Still have problems with Azureus doing the same thing from time to time.  The fix works still though...

Does anyone know how to change the default window colors in Azureus?  I run a high contrast setting so I'm not able to get some of the detail in the tabs.

---

### Post by majorlacko on 2007-05-21
When I upgraded to Feisty, Azureus always crashed so I installed it to /home/user from a simple .tar.bz2. After a week this problem has fixed somehow, so I reinstall it by Automatix2. I think it must work on the "normal" way either. Needs a short time command: sudo chmod a+w /opt/azureus/plugins/azplugins for an update but after all no need azureus folder in /home/user. Do not forget "a-w" after plugin update and restart.

---

### Post by Zer0Nin3r on 2007-05-22
Interesting.  Same results similar to the first fix suggested here.  What does the a+w argument do?  And why does the crashing have something to do with the permissions?

*UPDATE*
Still having problems with the crashing.  Will probably try a different install.  chmod is not working...

---

### Post by tommcd on 2007-05-22
> **majorlacko said:**
> When I upgraded to Feisty, Azureus always crashed so I installed it to /home/user from a simple .tar.bz2. After a week this problem has fixed somehow, so I reinstall it by Automatix2. I think it must work on the "normal" way either. Needs a short time command: sudo chmod a+w /opt/azureus/plugins/azplugins for an update but after all no need azureus folder in /home/user. Do not forget "a-w" after plugin update and restart.


You can accomplish the same thing with 
cd /opt
sudo chown -R  your_user_name:users azureus

This is safer from a security perspective also afaik.
The "chmod a+x" command gives everyone write permission to that directory.

---

### Post by barrack on 2007-12-24
> **Zer0Nin3r said:**
> Will probably try a different install.

I found a way to install Azureus 2.5.04 (the last one before version 3) without it shutting down.

I got the file from sourceforge.

[http://sourceforge.net/project/showfiles.php?group_id=84122&package_id=88270&release_id=481206](http://sourceforge.net/project/showfiles.php?group_id=84122&package_id=88270&release_id=481206)

Get the tar.gz one. Extract it and you get a folder called "azureus." Put it wherever you need to, I guess, but once point whatever launcher you want to the "azureus" file inside that folder and you're set.

---

### Post by shields on 2008-01-07
> **barrack said:**
> I found a way to install Azureus 2.5.04 (the last one before version 3) without it shutting down.

I got the file from sourceforge.

[http://sourceforge.net/project/showfiles.php?group_id=84122&package_id=88270&release_id=481206](http://sourceforge.net/project/showfiles.php?group_id=84122&package_id=88270&release_id=481206)

Get the tar.gz one. Extract it and you get a folder called "azureus." Put it wherever you need to, I guess, but once point whatever launcher you want to the "azureus" file inside that folder and you're set.

OK -- I placed it in /usr/bin.

How do I create a shortcut on my APPLICATIONS / INTERNET menu?

Thanks!

---

