---
title: "Opera Long Start Up"
date: 2021-12-16
forum: General Help
---

### Post by tedeye on 2021-12-16
Hello Gals and Guys - 

I have 21.04 installed on my notebook.  For the most part it works well, but I like to use Opera Browser and when I click on it, it takes a really long time to start.  Comparatively, Firefox pops open in seconds.  I read somewhere if you delete it using the software installer and then download it from Operas website, it runs much better, but that didn't work for me as the software installer gave me an error message.  Is there some way I can get this running better?  It's my only gripe about using Ubuntu.  Thanks for any help.

---

### Post by speartip on 2021-12-16
You've probably installed the Snap version of Opera. Snap apps do take a long time to load. You need to completely uninstall that and install the 64 bit deb version from here:
[https://www.opera.com/download](https://www.opera.com/download)
It works fine on 20.04, not sure about 21.04, but it should work.
Also the software installer isn't always the best way to install packages, use the "dpkg -i" command.
So download the Opera .deb package, then open a terminal in the folder you downloaded it to, & run:
```
sudo dpkg-i opera-stable*
```
Make sure you have completely uninstalled your previous version of opera first though.

---

### Post by tedeye on 2021-12-17
Thank you for the reply speartip.  I appreciate the help.  I did as you suggested.  I navigated to the the downloads folder via terminal where Opera was downloaded and then typed: 


sudo dpkg-i opera-stable_82.0.4227.33_amd64


I tried with the .deb added at the end as well, but both times I got "command not found", so I must have done something wrong?

Do I need to delete the profile folder in addition to uninstalling it to completely uninstall it?

Thanks again.

---

### Post by Holger_Gehrke on 2021-12-17
There's a blank missing in that command. It should be
```

sudo dpkg -i opera-stable_82.0.4227.33_amd64.deb

```
with a space between 'dpkg' (program name, short for 'debian package') and '-i' (option meaning 'install').

Holger

---

### Post by speartip on 2021-12-18
My bad. Your right Holger_Gehrke. There needs to be a space, "dpkg -i". And yes I would delete the opera profile folder as well, and start with a clean profile.

---

### Post by tedeye on 2021-12-18
Though I did not delete the profile folder, Opera seems much more snappy with the new install method.  Thanks for the help.

---

