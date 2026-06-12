---
title: "Ubuntu 15.10 problem when enabeling manual login"
date: 2015-12-29
forum: General Help
---

### Post by willi4 on 2015-12-29
I prefer manual login both on Windows and on Linux. The problem is that when entering this [COLOR=#666666]sudo sh -c 'echo "greeter-show-manual-login=true" >> /etc/lightdm/lightdm.conf'[/COLOR] and restart my PC, I get an error message and Ubuntu x64 desktop-edition won´t boot into graphical mode.

Has something been changed with lightDM causing this?

On my desktop I have installed the latest Ubuntu server version on a virtual machine. After having installed the GUI and entered the above line into the Terminal, it worked without problems.

Could anyone please tell my how to achieve manual login with Ubuntu 15.10. I have already reinstalled Ubuntu thrice, both from a USB drive and a DVD, so I doubt the installation image is corrupted.

UPDATE 1:
I have posted a clarifaction below to comply with requests. I hope everything is clear now.

---

### Post by buzzingrobot on 2015-12-29
You should describe what you mean by "manual login".  Do you mean entering your password into lightdm? Or, booting to a console, logging in there, and running startx?

---

### Post by grahammechanical on 2015-12-29
Is the Ubuntu 15.10 with the problem installed in a VM? Is it Ubuntu 15.10 server + GUI Desktop? Or is it Ubuntu 15.10 desktop as a stand-alone install. In which case the GUI installation procedure will ask if we want automatic log in or not.

Knowing the error message might also be helpful. It might give a clue.

Regards.

---

### Post by willi4 on 2015-12-29
Sorry for not having been clear enough.

manual login = enter username + password (see the picture from the Internet below)
[IMG]http://1426826955.rsc.cdn77.org/wp-content/uploads/2015/06/4.jpg[/IMG]
standard login = choose the user from a list and just enter the password

I have installed Ubuntu Server 15.10 with Unity GUI as a vmware workstation 12 virtual machine on a Windows 10 host. This works as good as Linux goes, including manual login. So there is nothing to be done.

The problem comes with my laptop. While Windows 10 is my primary OS, I´ll need Linux for certain programming tasks. While my desktop can easily handle two OSes without a noticeable performance impact my laptop can´t. So I have opted for dual-boot. Achieving dual boot is easier using a live DVD, so I have chosen Ubuntu 15.10-Desktop-x64. **Now here lies the problem**. 

Now when I enter [COLOR=#666666]sudo sh -c 'echo "greeter-show-manual-login=true" >> /etc/lightdm/lightdm.conf'[/COLOR], which has always worked for me until now (since Ubuntu 12.10 and still works on my virtual machine), and I log out, nothing has changed. When I restart the computer, I get an error message stating "**The system is running in low graphics-mode**" during the booting process.

[IMG]http://1.bp.blogspot.com/-PnFRiv7-WQs/UL-oVayYxQI/AAAAAAAAAOM/webTu83iqdA/s629/error-1.png[/IMG]

My aim is it to get a login screen like in the first picture and not repairing my OS. So I am going to reinstall Ubuntu from scratch. So please do not post any advices on how to repair my OS. What I asm interesting in is how to achieve manual login with Ubuntu 15.10 Desktop. Thanks for your time in advance.

---

