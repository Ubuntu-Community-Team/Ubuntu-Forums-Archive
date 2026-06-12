---
title: "Lotus Notes 8.0 (Final) on Gutsy (Final!)"
date: 2007-10-19
forum: General Help
---

### Post by croftd on 2007-10-19
Morning.

I've had a look to see if anyone else has reported this. If they have I sincerely apologise.

When opening an email, in Lotus Notes 8, having just upgraded from Feisty to Gutsy, the area where it displays the email turns black, you can't see anything! 

I can only view the email if I click forward or reply and scroll down to see the email. So if it gets copied into an editable interface, such as reply or forward, there is no blackness.

Is this something to do with the Emerald Theme manager? It was working fine before upgrading to Gutsy using Feisty and the Compiz Desktop Effects.

:confused:

This is frustrating, I keep alternating the settings (and Ctrl - Alt - Backspacing) and it just doesn't fix it. Think I need to do something more substantial than that.

So I'm curious to know if anyone else has experienced this blackness in either Lotus Notes or any other program.

Cheers,

Dan.

---

### Post by mrat on 2007-12-02
Hi Dan

No, and I am new to Linux myself so not very knowledgeable at all.

2 of us at work are running Notes 8 Standard (Eclipse) and do not have this issue. We are using XGL and Compiz, those from the Ubuntu Repos. Well I am on 7.10 and the other chap is 7.04.

Have you tried reinstalling Notes as there may be a number of changes in 7.10 that Notes 8 is not configured for... there are quite a few How Tos in this forum which are pretty good.

I need to add though, that I noticed that the Post Install script tries to run RPM commands, so I would get Alien installed before reinstalling. It was much happier after that. After that all I had to do was add a group to the "/etc/lotus" and "/opt/ibm", of wihch I was a member.

Notes 8 is also expecting Mozilla Firefox to be installed as it would be on Red Hat and Suse, and on my system it don't like Sun Java Browser Plugin. The reason I am saying this is that is because I found my Notes crashing a lot on certain MIME emails, which was linked to the Sun Java Plugin... soon as I switched to Iced Tea no more crashes. Even reinstalled Sun Java completey, as well as Ubuntu, thinking it was something I had done. You can use Sun as you main JRE, just as long as you have Iced Tea installed. The "<home>\lotus\notes\data\workspace\.config\rcpinstall.properties" file will state the location of the alternative Firefox Plugins so make sure this is correct.
It is looking for a conf file that is just pointing to the Firefox install. The path of the conf is "/etc/gre.d/gre.conf". the contents are :
[2.0.0.8]
GRE_PATH=/usr/lib/firefox

If you are going to reinstall Notes, get rid of the "/etc/lotus", "/etc/ibm", "/opt/ibm" and the "lotus" folders in the home folders (root as well). You can just rename them as a back up. You can then just move your NSFs back in but I would leave out the "workspace" folder.

Hope this helps.

Regards
Mark

---

### Post by mrat on 2007-12-10
Oops, realised a slight mistake in my last post about Iced Tea JRE.

If you are having crashes on certain MIME messages, and can link it to the Sun JRE in Firefox (remove the soft link from "<firefox>\plugins\") and try open the email again. If all is well, then use the "gre.conf" to stipulate another location of a Firefox install with the Iced Tea plugin.

Without the "gre.conf", it will use the default broswer on the system.

Here is what I did ;
Install Iced Tea, but made sure that Sun was the default by "sudo update-alternatives --config java"
Default Firefox path (with Sun JVM) : "/usr/lib/firefox"
copy this to "/usr/lib/firefox-itjvm"
remove "/usr/lib/firefox-itjvm/plugins/libjavaplugin_oji.so"
in "/usr/lib/firefox-itjvm/plugins", softlink to "/etc/alternatives/firefox-javaplugin.so" and rename the softlink to "libjavaplugin.so"
set the "gre.conf" to the " /usr/lib/firefox-itjvm" path

Of course this may be different on your system and you can change the names of the alternate Firefox install (firefox-itjvm). To keep this up to date, repeat the procedure when Firefox is updated. 

I sense there is probably a better way of doing this.

Regards
Mark

---

### Post by erickramirez on 2007-12-10
Mark,

That is an excellent post! Based on that, I wouldn't have picked that you are new to Linux.

Cheers,
Erick Ramirez
Melbourne, Australia

---

### Post by mrat on 2007-12-11
Cheers !

Many late nights and a bit like Homer, but finally got round my issue.

Regards
Mark

---

### Post by mrat on 2008-01-14
Ahh, XULRUNNER, bad with Notes and did the same as you said. Use Firefox with Iced Tea JVM.

Regards
Mark

---

### Post by www.rzr.online.fr on 2008-03-11
What about hardy ? I can not manage to install the demo also :
[http://ubuntuforums.org/showthread.php?p=4495003&highlight=lotus+notes#post4495003](http://ubuntuforums.org/showthread.php?p=4495003&highlight=lotus+notes#post4495003)

Finally I installed it under crossover :

  [http://rzr.online.fr/q/wine](http://rzr.online.fr/q/wine)

---

### Post by croftd on 2008-04-09
Thanks for your replies folks I will check it out. I haven't got round to this issue and have been running notes on VMware via Windows.

Unless I can get RAD test environments working in Ubuntu 8.. whenever that's due out I think I'm going to have to go back to Windows anyway :( 

I'm hoping for a dual boot at the very least. then I can use Windows for work and Ubuntu for play.

---

