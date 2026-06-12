---
title: "Terminal does nothing"
date: 2015-02-07
forum: General Help
---

### Post by foopo on 2015-02-07
Hello, I installed ubuntu about a week ago and everything was working fine. It seems as though one day everything decided to stop working. Fire fox does not connect to the web, where as before it did just fine. When I boot my computer, my key board does not work unless I unplug it and plug it back in again. If I click "restart" or "shutdown" it tries, but no matter how long I wait it won't turn off unless I manually hold down the power button. All of this did not happen before.

The main thing I want to know is, when I type a command in the terminal, it does NOTHING! How can I fix this?

For instance, If I type a command in, it does not ask for my password like it did before, it simply places my cursor down to the next line.

Example:

"jacob@jacob-GN567AA-ABA-s2220n:~$ sudo apt-get
_"


It did not do this before, and I did not change anything. It seems like everything just decided to stop working. I am a total beginner with ubuntu, can someone help me fix these issues without me having to re-install the OS or something? I am on 14.04 lts. As I said before none of these things happened for the first week of having Ubuntu

---

### Post by mooreted on 2015-02-07
Unless it's some kind of hardware failure: bad RAM, motherboard, hard drive, etc; you need to retrace your steps. What did you do in the last week or so? What did you install? What did you un-install? What did you delete? And so forth.

If your desktop is working at all, you cant hit ALT + F2 and try a different terminal such as xterm. There you can look at dmesg for errors, open up .xsession-errors, /var/log files and so on to try and figure out what happened. Sometimes a simple set of commands can help if you can get them to work:

sudo apt-get update
sudo apt-get upgrade

Another way to possibly get to a terminal would be to hit CTRL + ALT + F1. You can get back from there by typing CTRL + ALT + F7.

As it stands now, we would need more information to even guess what happened.

---

### Post by foopo on 2015-02-07
Thanks for replying! Well, I did install Java 7 and the minecraft.tar so I could play minecraft. I'm not sure that doing that effected anything though. I don't recall deleting or uninstalling anything else. I did'nt really change anything besides moving some stuff I don't use off the dock like the green and blue page icons. My desktop does work, Using alt+F2  I opened up xterm and searched for dmesg I tried to click on dmesg but as soon as I do it closes out of the terminal. I'm not sure if I'm going about that wrong or not. 

I managed to use both of those commands in the ctrl+alt+F1 terminal, the update went just fine but after the upgrade finished my screen is just black

---

### Post by mooreted on 2015-02-07
In xterm or after clicking CTRL + ALT + F1 you type the word "dmesg" without the quotes and press the ENTER key. After that you will see some messages on the screen that might point out what the problem is.

It might be faster to create a new user account, log into it and see if you have the same problems. If not, it's some configuration problem in your user's profile. There is a setting called "User Accounts". Open that, click "Unlock" then at the bottom click the "+" sign to add a new user.

---

### Post by mooreted on 2015-02-07
If your screen is now black, it could be you just need to press CTRL + ALT + F7 to get back to the desktop.

Do you know what video card you have? Have you installed the drivers for your video card?

---

### Post by foopo on 2015-02-07
I think my computer was just sleeping after I pushed space it came back to the ctr+alt+f1 terminal haha! When I type dmesg into xterm and hit enter, it simply closes out of xterm still. After the update/upgrade the basic terminal now works properly again though. When I type dmesg into the basic terminal I shows a whole lot of text but I'm afraid I don't understand any of it. Fire fox works after the update/upgrade but after booting my computer my keyboard still doesn't work until I unplug and replug it. Is there anything I can do to fix this?

Thanks for taking time to help so far, you have been very helpful and I'm very thankful for it!

---

### Post by mooreted on 2015-02-07
That's a weird one. I wonder if you have power supply or motherboard issues. Hopefully not.

Let's try and re-install your input drivers. Open a terminal and enter:

sudo apt-get install --reinstall xserver-xorg-input-all

---

### Post by foopo on 2015-02-07
I used that command and my keyboard works like normal again! Thank you so much :p

---

### Post by mooreted on 2015-02-07
Whew, I'm so glad we got that sorted out. I was afraid there was a bigger problem.

You are very welcome. Always happy to help.

---

### Post by foopo on 2015-02-08
Everything was working fine, and I changed nothing but now my terminal is broken again and fire fox can't connect to the web :0 I tried using sudo apt-get update from the ctr+alt+f1 terminal but now that terminal does nothing too! :c Also it no longer can restart or shut down unless I do it manually. I don't understand why does everything just randomly break?


EDIT: Turned off my computer and rebooted, managed to run the update and upgrade commands again! the upgrade command says: The following packages have been kept back: liboxideqt-qmlplugin linux-generic linux-headers-generic linux-image-generic python-cupshelpers system-config-printer-gnome

Also at the very end it says "6 not upgraded"

---

### Post by mooreted on 2015-02-08
Might be time to re-install. With this many problems, you could spend the next week trying to figure it out. You could re-install in a few minutes. If it happens with a fresh install, then you have to test the RAM and hard drive because something is wrong. Make sure you back up anything you want to keep.

---

### Post by mooreted on 2015-02-08
If this is a desktop computer you might also want to check your power supply. Also, open it up and look at the capacitors on the motherboard. The top of all the capacitors are supposed to be flat. If you see any that are domed on top, you have a motherboard going out.

---

