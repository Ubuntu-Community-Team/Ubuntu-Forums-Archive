---
title: "Troubleshooting Technique"
date: 2008-04-26
forum: General Help
---

### Post by daniel. on 2008-04-26
Does anyone have any tips for troubleshooting problems, *in general*? That is, techniques that are universally applicable for taking a first cut at problems before coming to the forums? Any advice on logging, etc?

I ask because I have for quite a while experienced a considerable amount of instability, but nothing severe. A wide variety of applications frequently exit without giving an error message, windows come up blank, horrible 2d vid. performance - just a wide range of problems. 

I'd like to learn a little more about what I can look at on my own, before asking specific questions.

Thanks,

daniel

---

### Post by Archimedes0212 on 2009-03-16
sometimes, well, lots of the time, I find that my video card is to blame (it is rather terrible).  Therefore, my first thought is it's usually a problem with the graphics.  I try turning down my graphics to minimal or something lower than I have it set at currently and try the troublesome "thing" again.  6 or 7 times out of 10, I find my graphics card is the culprit.

---

### Post by mb_webguy on 2009-03-16
Well, it depends on the problem.

If it's application behavior and specific to one application, you could try backing up and then deleting the config files for that application to see if that helps.

If it seems to be happening with all applications, try disabling visual effects.

If it seems to apply to all programs and visual elements, try checking your video card driver.  If you have an nVidia card, for example, you can install and run EnvyNG.

If you think it might be a problem with hardware, the lspci command is a good place to start.

If it's a problem with hard drives or other storage, "sudo fdisk -l" will show you what's being detected.

But the best first step to troubleshoot a problem in my opinion is to post your problem here, using a meaningful subject line.

---

### Post by drs305 on 2009-03-16
For gui apps, trying to run the command in terminal will often provide information on the problem, and sometimes even suggest a fix.

The best help is an good internet search, especially of these forums. I have a link on my web page to search this forum within a date range:
[ubuntu forum search]("http://www.google.com/search?hl=en&as_q=+&as_epq=&as_oq=&as_eq=&num=30&lr=&as_filetype=&ft=i&as_sitesearch=ubuntuforums.org&as_qdr=w&as_rights=&as_occt=any&cr=&as_nlo=&as_nhi=&safe=images")

---

### Post by crokett on 2009-03-16
> **drs305 said:**
> For gui apps, trying to run the command in terminal will often provide information on the problem, and sometimes even suggest a fix.


This is the most useful troubleshooting tool I use and one of the things I most love about Linux. 

Other things to check are your log files in /var/log/syslog

---

