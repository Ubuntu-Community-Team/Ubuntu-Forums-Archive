---
title: "[SOLVED] Gutsy: I am confused about which Java to install and  where to get it."
date: 2007-11-14
forum: General Help
---

### Post by brjoon1021 on 2007-11-14
With the multiverse repository in place, I can install JRE 5 or 6 I believe. There is also a selection of what seem to be just browser plugins available through "ubuntu addons" in the firefox add-ons menu. There is also Java 1.6. I am never sure which to install and  what the best way to install it is. What does Azureus need to work properly ? There is also another application 
that I want to be able to run which has the following instructions:

>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
" You have to install Sun Java JRE and make it the default Java JRE. Run the following command: 

update-java-alternatives -l

If java-1.5.0-sun or java-1.6.0-sun is not listed in the result, then you have to install sun-java5-jre or sun-java6-jre. To install sun-java5-jre run the following command:

sudo apt-get install sun-java5-jre

You have to make Sun Java JRE the default JRE. The following command makes java-1.5.0-sun the default JRE:

sudo update-java-alternatives -s java-1.5.0-sun"
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>



Can you clarify where to get which Java that I should install and which is the best way to install it? And I don't just mean for the above pasted instructions, I can read that just fine. If I install that will my Firefox surf with Java properly ? Will Azureus work ? Do I need to install two things ?

Thanks,

B.

---

### Post by g2g591 on 2007-11-14
the web browser plugin can be installed with sudo apt-get install 
[B]sun-java6-plugin . and you may want to set  sun-java6-jre  as the defualt jre (as it will be installed anyway as a dependance as sun-java6-plugin)
 im guessing all you should have to do is replace java-1.5.0-sun with java-1.6.0-sun in the command you posted above
[/B]

---

