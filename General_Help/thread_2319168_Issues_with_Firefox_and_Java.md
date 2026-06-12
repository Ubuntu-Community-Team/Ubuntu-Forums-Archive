---
title: "Issues with Firefox and Java"
date: 2016-04-01
forum: General Help
---

### Post by acefromspace on 2016-04-01
I don't usually have issues with Firefox, but recently trying to use CalJobs website and it brings up a window (based on Java) and when I click save it shows "loading". I waited for 10 minutes... just keeps saying loading. Using Firefox 45. Any suggestions? I had pop-ups disabled, but will try allowing for this website. Would Chromium work better? Any differences between Firefox and Chromium concerning Java?

---

### Post by Ricardo_Velasco on 2016-04-03
Hello

Do you have a recent version of Java?

Which is your Ubuntu´s version??.

---

### Post by acefromspace on 2016-04-05
I am using Ubuntu 12.04 and do updates often. How do find what version of Java I am using? Going to 14.04 soon.

---

### Post by acefromspace on 2016-04-08
It seems the issue was with the website, not my computer. I found another way to make it work, so consider this solved.

---

### Post by QIII on 2016-04-08
For the benefit of others, could you explain both the condition and the solution?

This is a community forum.

Thanks.

---

### Post by acefromspace on 2016-04-09
Most of the website worked (caljobs... it's for help getting a job, and also required for unemployment benefits) Then the part where you choose an occupation brings up a window and has a list to choose from. When I clicked on the list, it shows an icon saying "loading" and no matter how long I wait, it never finishes. Instead of using the list, I chose another option to search for keyword and it worked fine. Not sure why, but many others said they also have problems with this website. My system shows java version as openjdk-6 and openjdk-7, not sure which one is being used. Hope this helps.

---

### Post by Ricardo_Velasco on 2016-04-20
Maybe have the solution.

OpenJDK try to uninstall versions to replace them with official versions of Java

Put on the terminal:

> sudo apt-get remove openjdk-6-jre default-jre default-jre-headless




Or if you have the version 7:

> sudo apt-get purge openjdk-7-jre gcj-4.7-base gcj-4.7-jre openjdk-6-jre-headless

Then be sure , with this command that is not installed any version of OpenJDK:

_***java-version.***_

After installing Java 8 and will surely work.:

***sudo add-apt-repository ppa:webupd8team/java***

***sudo apt-get update ***

_***sudo apt-get install oracle-java8-installer***_

We hope you can work . :)

---

