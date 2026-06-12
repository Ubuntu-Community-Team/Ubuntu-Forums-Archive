---
title: "how to turn off crash reporting in Xubuntu?"
date: 2013-06-05
forum: General Help
---

### Post by potiphera on 2013-06-05
I'm using Xubuntu 12.04, and when a program crashes, I get the popup dialog alerting me about it. I usually uncheck the option to send an error report, but several times I've forgotten it's there in my rush to make the dialog go away and get back to whatever I was doing. The option is checked by default, but I never feel the need to send a crash report and am wary of sending any sensitive information, so I'd like to either turn that off by default or eliminate the crash dialog entirely. (I'd still like to be able to use ubuntu-bug manually when it's really necessary, however.) The information about the error tracker [here]("https://wiki.ubuntu.com/ErrorTracker") mentions privacy settings that don't exist in Xfce, so I'm not sure how to do this. Does anyone know?

Also, does Xfce have any options anywhere for privacy settings? I realized I have no idea how they are set on my system, if they are even relevant to Xubuntu. Thanks!

---

### Post by mike555 on 2013-06-05
You could uninstall "apport".

---

### Post by greatsirkain on 2013-06-05
"sudo apt-get remove apport" does the trick in Ubuntu

---

### Post by potiphera on 2013-06-05
Thanks for the responses! I was hoping not to have to uninstall apport because I wanted to be able to use ubuntu-bug. But if there is no other option, I can uninstall it and reinstall whenever filing a bug report is necessary. But I'd still like to know if there is a way to access the settings listed on that error tracker Ubuntu wiki page.

---

### Post by Buntu Bunny on 2013-06-05
> **potiphera said:**
> Thanks for the responses! I was hoping not to have to uninstall apport because I wanted to be able to use ubuntu-bug. But if there is no other option, I can uninstall it and reinstall whenever filing a bug report is necessary. But I'd still like to know if there is a way to access the settings listed on that error tracker Ubuntu wiki page.

Would disabling it do? Directions[ here]("http://howtoubuntu.org/how-to-disable-apport-error-reporting-in-ubuntu#.Ua-pwRWf1ag").

---

### Post by slickymaster on 2013-06-05
> **potiphera said:**
> Thanks for the responses! I was hoping not to have to uninstall apport because I wanted to be able to use ubuntu-bug. But if there is no other option, I can uninstall it and reinstall whenever filing a bug report is necessary. But I'd still like to know if there is a way to access the settings listed on that error tracker Ubuntu wiki page.

You can just disable the automatic crash interception component of apport. There's no need to uninstall it, and I wouldn't do it if I were you.

To disable it just edit your **/etc/default/apport** file. Open a terminal window and run the following command:```
gksu geany /etc/default/apport
```and change the **enabled** value from 1 to 0. Save and close the file.

If later on you need it to report a problem, just turn it back on by reverting the enabled value back to 1.

---

### Post by potiphera on 2013-06-06
Thanks, that's what I was looking for!

---

### Post by slickymaster on 2013-06-06
You're welcome.

Please don't forget to mark the thread as SOLVED. See the link in my signature if you don't know how to.

---

