---
title: "Can't Install Pepperflash in Firefox"
date: 2015-10-17
forum: General Help
---

### Post by lelouch2 on 2015-10-17
I'm trying to display [this page]("http://www.mspaintadventures.com/?s=6&p=001931") properly right now, but Flash fails to work in other places as well. I assume that it's because I have an ancient version, which is weird because I've installed Pepperflash before. I'm using Firefox 41.0.2.

I've tried using these commands:

```
sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install freshplayerplugin
```

I have the latest version of Google Chrome installed, and I launched it, because one guide I looked at said that it must be launched first to activate Pepperflash.

I've tried uninstalling and reinstalling Google Chrome, closing and opening Firefox, removing all non-official PPAs except this one to make sure there is no conflict, and rebooting. Nothing. Here's the full list of things I tried doing:

```
TEST PAGE: http://www.mspaintadventures.com/?s=6&p=001931

~~~~~~~~~~~~~

http://www.makeuseof.com/tag/how-to-get-chromes-latest-flash-player-to-work-in-firefox-on-linux/

sudo add-apt-repository ppa:nilarimogard/webupd8 && sudo apt-get update && sudo apt-get install freshplayerplugin

Restarted Firefox

No change

~~~~~~~~~~~~~

http://www.webupd8.org/2014/05/install-fresh-player-plugin-in-ubuntu.html

sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get install freshplayerplugin

sudo apt-get remove google-chrome-stable
sudo apt-get install google-chrome-stable

Restarted Firefox

No change

~~~~~~~~~~~~~

http://www.pcworld.com/article/2993902/browsers/how-to-get-the-latest-version-of-flash-on-firefox-for-linux-after-adobes-abandonment.html

sudo add-apt-repository ppa:nilarimogard/webupd8
sudo apt-get update
sudo apt-get remove freshplayerplugin
sudo apt-get install freshplayerplugin

Launch Google Chrome
Close Firefox
Launch Firefox

No change

Close Firefox
Close Chrome
sudo apt-get remove google-chrome-stable

Remove some software sources, including an old source for Pepper Flash

Reboot

~~~~~~~~~~~~~

sudo add-apt-repository ppa:nilarimogard/webupd8

kirucat@Stardust:~$ sudo apt-get update
E: Type 'ain' is not known on line 3 in source list /etc/apt/sources.list.d/nilarimogard-webupd8-precise.list

Opened file, removed "ain"

sudo apt-get update
sudo apt-get upgrade

The following packages will be upgraded:
  firefox firefox-globalmenu firefox-locale-en firefox-locale-ja

sudo apt-get update
sudo apt-get remove freshplayerplugin
sudo apt-get update
sudo apt-get install freshplayerplugin
sudo apt-get update

google-chrome-stable_current_i386 (1).deb from https://www.google.com/intl/en-US/chrome/browser/

google-chrome-stable

Close Chrome

sudo apt-get update

Reboot
Launch Firefox

No change
```

If I view about:addons, there is nothing called Flash in either Extensions or Plugins. I know that I have Flash because if I change Youtube to use Flash, it still works.

All of the tutorials I found are from 2014. Is this information just outdated? What am I supposed to do instead?

Thanks.

---

### Post by lelouch2 on 2015-10-18
I figured out the problem. To install Pepperflash, you have to first install Flash 11 to Firefox. I don't really understand why I didn't have it since I could use Flash Youtube (or at least, non-HTML5 Youtube?), but I didn't.

So I installed Flash 11 following these steps: [https://support.mozilla.org/en-US/kb/install-flash-plugin-view-videos-animations-games#w_installing-the-flash-plugin-manually](https://support.mozilla.org/en-US/kb/install-flash-plugin-view-videos-animations-games#w_installing-the-flash-plugin-manually)

Then I closed Firefox, removed Chrome and freshplayer plugin, and reinstalled them. Now [this website]("http://vhttp://flashbuilder.eu/flash-player-version.html") says that I have Flash 19, and my plugins list Flash 11 and Flash 19.

Hooray!

Here are my exact steps just in case anyone needs to know how to solve this problem in the future.

```
https://support.mozilla.org/en-US/kb/install-flash-plugin-view-videos-animations-games#w_installing-the-flash-plugin-manually

download Flash tar
close Firefox
tar -zxvf install_flash_player_11_linux.i386.tar.gz
sudo cp libflashplayer.so /usr/lib/mozilla/plugins/

sudo apt-get update

Launch Chrome
Close Chrome
Launch Firefox

Firefox now has Flash 11 instead of nothing.

~~~~~~~~~~~~~

sudo apt-get remove freshplayerplugin

Close Firefox

sudo apt-get remove google-chrome-stable
sudo apt-get update
sudo apt-get install freshplayerplugin

Reinstall Chrome from previous deb

Launch Chrome

http://flashbuilder.eu/flash-player-version.html -- Chrome Flash is 19.

Chrome freezes up.
Ctrl+C Chrome.

Launch Firefox.

http://flashbuilder.eu/flash-player-version.html Firefox Flash is 19!

SUCCESS.
```

---

### Post by Bucky Ball on 2015-10-18
Just a tip to speed up the process.

```
sudo apt-get install flashplugin-installer
```

... will install flash 11.2 directly from the official repos. :)

Thanks for sharing.

---

### Post by lelouch2 on 2015-10-18
> **Bucky Ball said:**
> Just a tip to speed up the process.

```
sudo apt-get install flashplugin-installer
```

... will install flash 11.2 directly from the official repos. :)

Thanks for sharing.

Ah, thanks for the tip! :smile:

---

