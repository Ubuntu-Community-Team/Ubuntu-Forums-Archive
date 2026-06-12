---
title: "Various Questions and General Performance Problem"
date: 2013-08-01
forum: General Help
---

### Post by blablabity on 2013-08-01
Hi, I recently switched from Windows 8 to Ubuntu 13.04, and I am having a performance problem. Everything seems to take longer than it should to start up, mumble especially. Also, while on windows I was able to run DOTA 2 on max settings, but while playing the Linux version I have to turn down the settings significantly to avoid lag. This could just be due to the game itself, but others claim that it runs as well as the Windows version, so I suspect it is also a performance issue. I just feel as if Ubuntu isn't utilizing my hardware fully.

I am running an AMD FX-8150 eight core processor, 8GiB of memory, Gallium .4 on AMD Barts, which is an AMD Radeon HD 6850 card. 64-bit OS and 500 GB of HDD space.

I have not done anything involving graphics drivers since switching, which may be the issue. Under software and updates>Drivers it says I am using the X.org driver wrapper.

What follows are random questions/issues. If these shouldn't be in the same thread feel free to ignore them.

[LIST=1]
[*]I am unsure of how to truly delete some applications/programs. Specifically, I do not want to use the Ubuntu One cloud sharing service. I uninstalled from the Software Center, restarted, but the little cloud by the clock remains. I then deleted as many Ubuntu One folders as I could find and restarted, no fix. I would also like to get rid of the mail icon that pops up by the clock as well, as it serves me no purpose. I also accidently clicked yes to install Twitter when I went to the site in firefox, and now any time I go to the site an extra icon pops up on the dock bar. I can not find it in the software center to uninstall. 
[*]At times it does not allow me to use my password to perform functions even though I am the only user, and an "administrator". For example, when I try to run the System Testing application, it asks for a password, but rejects the one I have been using to login, for the terminal, etc. I am sure I am typing the right password, caps lock isn't on, etc. 
[/LIST]

Sorry if any of the questions are, well, stupid. I was pretty good with windows, but this is a whole new beast. Any help is appreciated, and thanks in advance.

---

### Post by boast on 2013-08-02
the gallium drivers are good for desktop stuff, but if you want to game I would suggest giving the proprietary drivers a try (Software & Updates > Additional Drivers).

Did you follow this for removing ubuntu one? [https://one.ubuntu.com/help/faq/how-do-i-completely-remove-and-reinstall-ubuntu-one/](https://one.ubuntu.com/help/faq/how-do-i-completely-remove-and-reinstall-ubuntu-one/)

the twitter thing is "unity web apps." you can remove the twitter one with "sudo apt-get remove unity-webapps-twitter" in the terminal

---

### Post by blablabity on 2013-08-02
Thank you! After using [http://wiki.cchtml.com/index.php/Main_Page](http://wiki.cchtml.com/index.php/Main_Page) and the guides there I was able to install the proprietary drivers and they helped performance in all aspects of my computer by a ton. I was also able to uninstall the twitter and UbuntuOne apps. The only thing left is this mail application. Currently when I click on it it has a reddit button that opens a new firefox browser to reddit and a greyed out clear button. Anyone know how to remove this? Not sure where it came from or what it has to do with reddit.

---

