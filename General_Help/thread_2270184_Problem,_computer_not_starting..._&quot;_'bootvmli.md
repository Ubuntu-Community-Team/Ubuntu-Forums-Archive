---
title: "Problem, computer not starting... &quot; '/boot/vmlinuz-3.11.0-26-generic' not found.&quot;"
date: 2015-03-21
forum: General Help
---

### Post by jes5 on 2015-03-21
Hi there.

We were trying to install a program download for bandwidth monitoring.

Tried bmon, nethogs, and I think another program.

Kept getting "unmet dependencies" error, and it just wouldn't install.

Said the installer needed to be updated or was broken.

A program was run, and a bunch of "remove" dialogues were run.

Any idea why the program removed other programs from the PC?

And how to fix the problem?

---

### Post by deadflowr on 2015-03-21
moved to **General Help**

the 3.11.0-25-generic kernel was used in what is now an unsupported release.(Ubuntu 13.10)
What version of Ubuntu are you using?

---

### Post by jes5 on 2015-03-21
Thank you for the reply. I am uing ubuntu 13

---

### Post by jes5 on 2015-03-21
When I start the computer, it says GNU GRUB version 2.00 - 19ubuntu2.1 and when I click on Ubuntu it gives the error message 
[h=2]'/boot/vmlinuz-3.11.0-26-generic' not found.[/h]When I was downloading the bandwidth monitor it said that it was removing software, and it seemed like some important software so I stopped the process. When I restarted the computer and tried to access ubuntu it gave me the above message.

---

### Post by jes5 on 2015-03-21
Is it possible to fix this? Do i need to download a new version of ubuntu**?**

---

### Post by deadflowr on 2015-03-21
Do a fresh install from Ubuntu of 14.04.
It is the next version released after 13.10, but is what is known as a long-term-support release, so it's end of support is several years longer than 13.10.

Here's a link to 14.04
[http://releases.ubuntu.com/14.04.2/](http://releases.ubuntu.com/14.04.2/)

note that intel x86 means any 32-bit system, be it intel or another like amd.
And likewise, amd64 means any 64-bit system, be it amd or intel.
It's simply a legacy naming convention.

Unsupported releases lose their repositories, which house the updates and packages you can install on Ubuntu.
As such they also lose the ability to install updates to fixes for any security vulnerabilities, leaving you at the whim of whatever flaws have been discovered since it reached it's end of life. 

Upgrades from an unsupported release to a supported release is possible, but troublesome, and in the long of it easier to simply download a fresh copy and reinstall a fresh system.

---

### Post by jes5 on 2015-03-21
Thanks so much for the help.

I am downloading the "PC (Intel x86) desktop image" for this 64bit Lenovo G500 laptop, T-1 hour.

Legacy naming convension, hey. 

"repositories" sounds like Windows Control Panel.

"end of life" sounds pretty hectic. I was wondering whether you couldn't just somehow manually through the console connect to the internet and download the ISO, or something, and then somehow restore/boot/update like that.

But, what I am doing now is downloading that ISO, and going to try to figure out how to burn it to disk.

I think I am with you now, on this, though. It'll probably be too difficult for me to somehow manually update from the command.

---

### Post by Mike_Walsh on 2015-03-21
Hallo, jes5. 

After you've done a fresh install of Ubuntu 14.04 (about which I agree with deadflowr), IF you still want a bandwidth monitoring program, have a look at this:-

[https://codebox.org.uk/pages/bitmeteros](https://codebox.org.uk/pages/bitmeteros)

BitMeter OS is a nifty small app that will monitor ALL your bandwidth usage....even across multiple machines on a home network. I've been using it since June last year, shortly after moving to Linux, and Ubuntu. It works faultlessly. Download it from the site; go for the 0.76 stable version, not the bang-up-to-date one (0.8; this is still really in the testing stage). Once downloaded, just double-click on it, and it will install through the Software Centre.

One point to note:- When you start the install process, you WILL get a window come up that says "The package is of bad quality...you shouldn't install it", or something similar. I think this is because of the fact that it's NOT gone through the approval process for the repositories. However, click on '"Ignore, and install anyway"; it is **perfectly** safe to use, and will not have any adverse effects on ANY part of your system, if my months of usage are anything to go by. I can't recommend this app highly enough; I use it because at home, we like to keep within our monthly broadband allowance, and for this it's invaluable.

When it's installed, you access it via your web browser. Simply enter:-

```
 localhost:2605/index.html
```

in the address bar, and it will continuously monitor your network traffic on port 2605, and give you a live read-out as it does so. I have it bookmarked, to make it easy to find; it's always the first tab I open in the browser. If you WANT to set it up for monitoring multiple machines, just have a nose around the website; the instructions for doing so are there somewhere.....I forget where, exactly, but they ARE there...and quite clear and easy to follow.

The only thing you **may** occasionally notice, in the BitMeter tab in your browser. is a small window that appears, saying 'Error - The server is taking a long time to respond'; just 'OK' it, and carry on.

It works in ANY browser. I use it in Chromium, Firefox, and Pale Moon ( a Firefox 'fork'), and in several different OSs; it never gives any trouble.

Hope that helps.


Regards,

Mike. :)

EDIT: The 'legacy naming convention' that deadflowr refers to for the 'amd64' versions, is actually named after the very CPU that I myself run; an AMD Athlon 64. It was the very first commercially-available 64-bit CPU released to the general public.

Incidentally, you'll need to burn the Ubuntu download AS an 'iso' image; it won't work otherwise.

---

### Post by grahammechanical on 2015-03-21
When a new version of Ubuntu is released we are given a one click option to upgrade to the newer version and it is down through a utility with a graphical user interface (GUI) called Software Updater. If we fail to upgrade and the version becomes unsupported (no security updates) then upgrading becomes more difficult.

We get Long Term Support (LTS) versions every 2 years and each is supported for 5 years. Other versions with only 9 months support are released every six months. They are used to keep Ubuntu progressing until the time for the next LTS release.

I have no knowledge of Windows Control panel as I have not used a Microsoft OS for more than 7 years but I do not think that a Ubuntu repository is the same thing. Think of repositories as a kind of store room. They are computers where all Ubuntu software is stored. Each version of Ubuntu has its own set of repositories. They are also called archives.

Regards.

[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by bardo2 on 2015-03-22
Beside obove mentioned approach... Did you know about grub2 possibilities to diagnose and fix a boot problem like this?

Usually, /boot/grub/grub.cfg is used to create and display the boot menu. If - for whatever reason - this is outdated, you CAN be lucky to find an older kernel (like Ubuntu -> advanced (? not sure about the wording here) options -> select older kernel). But even if grub.cfg is unavailable, you can still use grub commandline to inspect the disk(s)/partition(s)/content (even tab-completion is there to help you find a kernel). But it requires some understanding of the boot process and your configuration/system setup. Thus it is very difficult to guide someone from afar. But it can be done... begin here: [https://help.ubuntu.com/community/Grub2/Troubleshooting](https://help.ubuntu.com/community/Grub2/Troubleshooting)

---

