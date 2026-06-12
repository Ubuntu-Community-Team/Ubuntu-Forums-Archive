---
title: "Login problems to Ubuntu 14.04 LTS"
date: 2016-11-08
forum: General Help
---

### Post by Fernanddo Saenz on 2016-11-08
My Compaq Presario CQ50 developed the following symptom: The booting appears to be right (screen wallpaper ok, etc), the login dialog appears, the password is entered, apparently it is accepted - it seems to proceed as usual for a while, but then it goes back and presents the login dialog again. The same happens with the "invited user" account, (which has no pwd, just enter). The password is ***correct***; I can tell because if I deliberately type a wrong one, it immediately signals so (with red text). Only when the correct password is entered, it seems to accept it and then goes round forever.

This is quite annoying, because I am effectively locked out from the computer!

---

### Post by Jimysbil on 2016-11-08
This is usually a problem of a proprietary GPU driver.

 The solution the most of the times is to completely remove GPU drivers (the way you installed them) and reinstall an other version of them or the same one but disabling other drivers may conflict.

Check thus out:
[How to remove your GPU drivers](http://askubuntu.com/questions/693454/infinite-login-loop-with-nvidia-proprietary-graphics)

And this:
[How to install the most recent or older drivers from ppa](http://www.howopensource.com/2012/10/install-nvidia-geforce-driver-in-ubuntu-12-10-12-04-using-ppa/)

---

### Post by Fernanddo Saenz on 2016-11-09
Thanks for the prompt answer, Jimysbil; the provided links are enlightening. If I understood, it seems my problem is that my graphics (Nvidia C77, or GeForce 8200M G) is now "legacy" and is supported by Nvidia´s open source legacy driver, "340.98". The file (downloaded in another machine) is "NVIDIA-Linux-x86_64-340.98.run", and I have it in a USB stick.

I found that Ctrl+Alt+F1 works, and I have access to a console session. The question is how (and where) do I copy that driver file to the  affected laptop computer. Do I need that actually? Or is that included in the ppa repository? For the "sudo apt-get install nvidia-xxx" line, I need to know the "xxx"; how can I find that?
Thanks again

---

### Post by Fernanddo Saenz on 2016-11-09
Hello,
SOLVED! Using the Ethernet connection, the repository ppa could be added, after removing with "sudo apt-get purge nvidia*" (Apparently, after purging the video, the wireless dies). 

After rebooting, the process finally went past the login screen ok (although with flickering graphics), and in a regular terminal window I typed:

sudo apt-get update
sudo apt-get install nvidia-340 nvidia prime

and the problem went away (non-flickering graphics, wireless ok). Actually, the "nvidia-340" was just a guess, based on the info above.

---

