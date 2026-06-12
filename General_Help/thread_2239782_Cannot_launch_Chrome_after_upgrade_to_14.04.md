---
title: "Cannot launch Chrome after upgrade to 14.04"
date: 2014-08-15
forum: General Help
---

### Post by amplexus on 2014-08-15
Hi,

Just upgraded to Trusty Tahr. Chrome won't start from the launcher. In the terminal, inputting google-chrome produced:

[4144:4144:0815/231526:ERROR:nss_util.cc(853)] After loading Root Certs, loaded==false: NSS error code: -8018
[4144:4144:0815/231526:ERROR:process_singleton_posix.cc(264)] Failed to create /home/paul/.config/google-chrome/SingletonLock: File exists
[4144:4144:0815/231526:ERROR:chrome_browser_main.cc(1156)] Failed to create a ProcessSingleton for your profile directory. This means that running multiple instances would start multiple browser processes rather than opening a new window in the existing process. Aborting now to avoid profile corruption.

Grateful for any help, but please talk to me as if I'm an idiot, because when it comes to this stuff, I am.

---

### Post by westie457 on 2014-08-15
Hi have you tried re-enabling the 'http://dl,google.com/linux/chrome/deb/stable main' repo in your sources list?

Followed by (in the terminal)```
sudo apt-get update
sudo apt-get upgrade
```

Hope this helps.

---

### Post by amplexus on 2014-08-15
> **westie457 said:**
> Hi have you tried re-enabling the 'http://dl,google.com/linux/chrome/deb/stable main' repo in your sources list?

Thanks for the quick reply, but (apologies) I don't know how to do this.

---

### Post by Ace700 on 2014-08-15
Auto: Ubuntu Software Center **>** Edit **>** Software Sources **>** Add

Then paste the link in apt line box.

Manually:

Edit: /etc/sources.list and paste the repository on the bottom.

---

### Post by deadflowr on 2014-08-15
> **Ace700 said:**
> Auto: Ubuntu Software Center **>** Edit **>** Software Sources **>** Add

Then paste the link in apt line box.

Manually:

Edit: /etc/sources.list and paste the repository on the bottom.


Do the first part of the advice, but stop short of pasting the line and instead look over at the section marked "Other Software" and see if it needs to be re-enabled.

Or quickly run 
```
sudo apt-get update
```
and see if it enabled already.
Or if any other errors are cropping up.

More over, chrome adds a file to the subfolder /etc/apt/sources.list.d typically called google-chrome.list.
This is where that line would be, and not in the main sources.list file. fwiw...

---

### Post by Ace700 on 2014-08-16
Well that is assuming the OP don't have the repository. When I use chrome, I just get the deb file, and do 

1: [https://www.google.com/chrome/browser/?platform=linux](https://www.google.com/chrome/browser/?platform=linux)
2: Download the bit that you're on; either 32 or 64 bit deb.
3: Open terminal and cd your downloads or move to desktop.
3a: If you choose to do it in downloads type:
```

cd Downloads
#if on 64 bit ubuntu
dpkg -i google-chrome-stable_current_amd64.deb
#or if you're on ubuntu 32 bit
dpkg -i google-chrome-stable_current_i386
```
3b: If you choose to do it in Desktop type:
```

cd Desktop
#if on 64 bit ubuntu
dpkg -i google-chrome-stable_current_amd64.deb
#or if you're on ubuntu 32 bit
dpkg -i google-chrome-stable_current_i386
```

4: Enjoy chrome. Probably a lot better to just re-install chrome over messing with it trying to fix it.

---

### Post by amplexus on 2014-08-16
Thanks for the suggestions guys. 

Earlier, I installed Chrome again. I still wasn't able to run it from the launcher, but could now do so from the terminal. However, I think I had two different versions of Chrome on the system, and I want to be able to use the launcher. 

So, I did a complete uninstall from Synaptic Package Manager, then reinstalled with no apparent problems. Now it won't run from the launcher or the terminal, and the message is as it was in the first place:

[3989:3989:0816/192408:ERROR:nss_util.cc(853)] After loading Root Certs, loaded==false: NSS error code: -8018
[3989:3989:0816/192408:ERROR:process_singleton_posix.cc(264)] Failed to create /home/paul/.config/google-chrome/SingletonLock: File exists
[3989:3989:0816/192408:ERROR:chrome_browser_main.cc(1156)] Failed to create a ProcessSingleton for your profile directory. This means that running multiple instances would start multiple browser processes rather than opening a new window in the existing process. Aborting now to avoid profile corruption.

Something surely has to be done with that Singleton file that 'already exists'.

---

### Post by deadflowr on 2014-08-16
Perhaps try creating a brand new profile and move the old one into a backup file.
```
mv -R /home/paul/.config/google-chrome /home/paul/.config/google-chrome.bak
```
Chrome will generate a fresh profile folder.
Downside is that it will be fresh without any added stuffs such as saved passwords or extensions.
if it doesn't help you can then simply reverse the command and restore it as it was and start again.

---

### Post by amplexus on 2014-08-16
Thanks deadflowr. That didn't work, but I decided to see if using a different launcher would help. So I downloaded Unity and a Cairo dock, and I can launch Chrome from that, so I'm happy with that. Others will surely have the same problem with the Trusty Tahr launcher, though.

---

