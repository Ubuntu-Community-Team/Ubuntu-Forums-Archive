---
title: "Google Chrome install"
date: 2016-11-07
forum: General Help
---

### Post by Frank_Snyder on 2016-11-07
I tried installing chrome a while back when I did a fresh install of 16.04. After installing I would try to run the program and I would see it pop up in the tray blinking for about 5 to 10 seconds before disappearing.

I just unistalled it and then got the current deb and installed it. I also ran sudo apt-get install -f afterwards which should install the dependencies needed but running this installs nothing. I noticed when installing the chrome deb that I got no errors so this would make sense. However I have the same issue. The chrome icon pops up in they tray for a little while before disappearing.

Any suggestions?

---

### Post by RobGoss on 2016-11-07
Hello and welcome the forum, Are you trying to install the **32 -bit **Google chrome or the **64-bit, **as you are probably already aware the 32 is no longer supported by Google and was drooped sometime ago so you will have to use Chromium instead if you're using the 32-bet

Google chrome 64-bit can be install using the software center with 16.04

You might want to completely remove what every packages of Google chrome you already install and then reinstall it

Run this command it will remove Google chrome

```
sudo apt-get purge google-chrome-stable
```

Then run this command to completely remove any remaining packages 

```
sudo apt-get autoremove
```


Open up the software center and search for Google chrome and install it from there

Or install it using the command line: 

```
 wget https://dl.google.com/linux/direct/google-chrome-stable_current_amd64.deb 
```

---

### Post by Frank_Snyder on 2016-12-02
Very late response but thank you!

---

### Post by RobGoss on 2016-12-02
Were you able to successful get google chrome installed?

---

### Post by Frank_Snyder on 2016-12-24
Late reply yet again. I don't frequent these forums and the issue has been not something I've made much effort to resolve as I only want Chrome for Netflix playback.

But no, I have yet to resolve it. It's giving me the same issue. I installed it through the terminal and therefore ran the command you provided to completely uninstall before I reinstalled. No dice. I also had Chromium on the system at one point as I thought that might be a work around. It seems having both Chromium and Chrome can cause issues. So I ran the same uninstall commands to remove Chromium and again ran the commands to uninstall the newest install of Chrome. Ran all program updates, and a distro update, rebooted the machine and tried using wget and then dpkg -i/apt-get install -f to reinstall. Still no luck.

If I try and run it by the icon in the GUI found by searching my computer, it just blinks in the taskbar for a little bit then disappears. If I try and run it via terminal, sudo google-chrome-stable, I just get the following output "Illegal instruction (core dumped)"

---

