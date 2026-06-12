---
title: "[SOLVED] Internet Flash"
date: 2008-07-06
forum: General Help
---

### Post by amergermandude on 2008-07-06
Hi I am new here and to Linux in general so I will explain the best I can.

When I go on line and look at sites such as Walmart I move my mouse over
the sections to search the sites and the drop down boxes come down, now if there is a picture underneath the drop down box the box goes underneath the picture and I cant view the selections to search the sites. Is there any fix to this ? I have also installed the Ubuntu restricted extras which installed the flash plugins I believe. Thanks for your help


Ok now I am confused i just went to walmart.com to show my wife the flash problem and my web browser shuts down immediately upon the web page loading every time, but now after I post this thread never before. WHAT is happening it does not shut down on any other site.

---

### Post by kuja on 2008-07-06
Something is definitely causing your web browser to crash, possibly also related to the flash problem, but not neccessarily. Try removing or disabling the flash plugin and see if the crashes persist. If that does persist, file a bug against the web browser at [launchpad](https://launchpad.net).

The problem with the flash content appearing in front of things such as dhtml menus and the like is a well known with Flash 9. I've heard that it may be fixed in version 10, which is currently in Beta status.

---

### Post by amergermandude on 2008-07-06
Thanks for the tip kuja I will try that and let you know how it works.

---

### Post by ubuntu-freak on 2008-07-06
Make sure you don't have libflashsupport installed and disable the Adblock Plus extension if it's installed, they both caused me problems. Also, take a look at the troubleshooting section of my [how-to](ubuntuforums.org/showthread.php?t=766683) and give Flash v10 beta a try.

---

### Post by amergermandude on 2008-07-06
wow that worked awesome I know have flash player 10 and it works amazingly 
well. Thanks a million reassuringlyoffensive.

---

### Post by ubuntu-freak on 2008-07-06
> **amergermandude said:**
> wow that worked awesome I know have flash player 10 and it works amazingly 
well. Thanks a million reassuringlyoffensive.

 
You're welcome. :-)
 
If you're gonna do part 1 and 2 of my how-to, don't let it install flashplugin-nonfree, as that will install v9 again.

---

