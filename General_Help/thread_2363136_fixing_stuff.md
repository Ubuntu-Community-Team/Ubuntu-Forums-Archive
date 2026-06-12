---
title: "fixing stuff"
date: 2017-06-06
forum: General Help
---

### Post by jgw on 2017-06-06
I have the following stuff that I do every few months to deal with possible problems.  I have been doing this for a very long time and thought I would put this up to make sure I am not screwing up stuff.  Below is my list:
sudo apt-get update           # syncs the data bases between your system and your mirror site
sudo apt-get upgrade         # updates installed software to what is current on your mirror
sudo apt-get dist-upgrade   # installs new software (kernel) that 'update' does not handle
sudo apt-get -f install         # looks and tries to 'fix' broken packages
sudo dpkg -C                    # runs an 'audit' of the package management system

sudo apt-get install linux-firmware-nonfree   # installs other drivers ##  (this one no longer works)

sudo apt-get autoremove

# Check system sources (system update)
cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

Thank you.............

---

### Post by Bucky Ball on 2017-06-06
I can't add much as don't know much after 'sudo apt-get dist-upgrade', but I will add that I'd run 'sudo apt-get autoremove' to start with, before update and upgrade commands. Not much point in running autoremove after you've updated as not much point updating things you might be autoremoving. ;)

Also, you can use just 'apt' instead of 'apt-get' if you like.

---

### Post by Impavidus on 2017-06-06
On 16.04 you can use apt instead of apt-get. If you use apt, you can skip the dist-upgrade, as that is handled by apt upgrade. No need to run the apt install -f unless apt upgrade complains there's a problem. An occasional apt autoremove will remove old kernels, so that's useful.

You can configure your system to do this all automatically or show a popup when upgrades are available. And in any case it's better to install upgrades a bit more often than once every few months.

---

### Post by jgw on 2017-06-06
Thank you for the replies - appreciated!  I will mark this one as solved.

---

