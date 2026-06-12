---
title: "Will Kubuntu kill internet in Ubuntu?"
date: 2006-12-05
forum: General Help
---

### Post by klittzzer on 2006-12-05
I am probably asking a really dumb question here but I need to know.

I have managed to get on the internet under Ubuntu Edgy 6.10 (2.6.17-10-generic) after 3 weeks of frustration trying to configure my USB ADSL modems (Sagem fast 800 just refused to work so I dug an old SpeedTouch one out and got it going second attempt).

I tried to get Ubuntu 6.06 LTS loads of times but never got past the burn stage. I used 3 different recommended (Ubuntu wicki)burners at speeds as low as 1x but had no joy at all. I gave up trying 6.06 and went for Edgy which I downloaded, burnt, and installed on first attempt. Seriously.

I would like to try Kubuntu now I can use Synaptic Package manager but am scared I might lose my net connection. Will this happen? Or will the settings that I have entered for my modem remain untouched if I get Kubuntu with Synaptic?

I would be grateful if anyone could tell me if I will be safe with Kubuntu.

Also, does anyone know why those 6.06 downloads were all no good?
Seems strange that I downloaded, burnt disc image, and installed 6.10 first go eh.

Give thanks for any advice.

Klittzzer

---

### Post by reech on 2006-12-05
Your settings should remain the same - they're in a text file called interfaces in /etc/networking/ . You might want to back up your working interfaces file, do the update to your system and if anything goes wrong you can simply replace the interfaces file and restart networking like so:

```
sudo /etc/init.d/networking restart
```

Changing the display manager should not affect your modem drivers or setup.

---

### Post by madcow72 on 2006-12-05
I assume you just want to try out the KDE desktop to compare it with Gnome?  You can do this without losing anything, because it will only start another session...meaning that when you log in, you have the option of booting into Gnome (like you presently do), or booting into the new KDE desktop.  Some instructions for doing this are here:[http://www.howtogeek.com/howto/ubuntu/install-kde-kubuntu-on-ubuntu/]("http://www.howtogeek.com/howto/ubuntu/install-kde-kubuntu-on-ubuntu/")

---

