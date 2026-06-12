---
title: "install cups in lubuntu 16.04"
date: 2016-06-28
forum: General Help
---

### Post by bin_bash on 2016-06-28
I have recently installed lubuntu 16.04. It now comes with cups no longer pre-installed..
I would like to install cups, as I need it for my printer.
The command, ```
sudo apt install cups
```, produces this message.


```
Package cups is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source

E: Package 'cups' has no installation candidate
```

Can anyone tell me how to install cups, or do I need to go back to lubuntu 15.10?

---

### Post by leozinho29_eu on 2016-06-28
You could try to install it thought **synaptic**, I installed cups this way in Lubuntu 16.04 (the command line worked here too).

If you did not find it there, then there must be some issues with the repositories.

---

### Post by Bucky Ball on 2016-06-28
Welcome. Install through Synaptics, as suggested. Search for cups, install.

Look in Synaptics first when you need to install something unless there is some necessity for the terminal.

---

### Post by roler2 on 2016-06-29
The command may be sudo apt**-get** install cups not sudo apt install cups. However, if you are having difficulty, here is a link to installing cups from a .deb file. On the right hand side, under 'builds' make your selection and then it will go to the next page where all the .deb files are located on the left near the bottom of the page.

[https://launchpad.net/ubuntu/+source/cups/2.1.3-4](https://launchpad.net/ubuntu/+source/cups/2.1.3-4)

---

### Post by vasa1 on 2016-06-29
> **roler2 said:**
> ..., if you are having difficulty, here is a link to installing cups from a .deb file
...
Let's wait awhile before recommending that :)

---

### Post by bin_bash on 2016-06-29
Thanks for the suggestions, a search in synaptic shows the assorted cups packages as being already installed. The only problem being that when I download the drivers from the Brother site and try to configure my printer, I find that cups is not installed. Perhaps I should ty LPR?
Or just go back to 15.10 which worked flawlessly?

---

### Post by howefield on 2016-06-29
> **roler2 said:**
> The command may be sudo apt**-get** install cups not sudo apt install cups.[/url]

apt install is a legitimate command in recent versions of Ubuntu, as of course is the older apt-get.

> **bin_bash said:**
> Thanks for the suggestions, a search in synaptic shows the assorted cups packages as being already installed. The only problem being that when I download the drivers from the Brother site and try to configure my printer, I find that cups is not installed. Perhaps I should ty LPR?
Or just go back to 15.10 which worked flawlessly?

15.10 is weeks away from being end of life, so it's probably worth trying some more to fix the issue in 16.04. What is the printer model name ?

---

### Post by leozinho29_eu on 2016-06-29
> **bin_bash said:**
> Thanks for the suggestions, a search in synaptic shows the assorted cups packages as being already installed. The only problem being that when I download the drivers from the Brother site and try to configure my printer, I find that cups is not installed. Perhaps I should ty LPR?
Or just go back to 15.10 which worked flawlessly?

I had this same issue with a HP printer. Cups and other dependencies were not being detected, even if installed.

To solve this, there was the hp-doctor utility, which came with hplip-gui, that made the (re)installation of them. It installed the same version of cups and the other packages, then it started to detect it.

I sincerely don't know why the installation I have made by myself was not detected.

I don't know if Brother has this sort of utility, but if it has, then it could solve the issue.

I can't grant this will work: If no other option is found: maybe, just maybe, the HP utility may solve the Brother issue. I can't grant this nor I can test now. HP has its own Unix system, so this utility may be flexible enough. This may or may not work.

---

### Post by bin_bash on 2016-06-29
> **howefield said:**
> apt install is a legitimate command in recent versions of Ubuntu, as of course is the older apt-get.



15.10 is weeks away from being end of life, so it's probably worth trying some more to fix the issue in 16.04. What is the printer model name ?

Thank you for the response, my printer is a Brother DCP-7030, I have always been able to get it working with ubuntu, Mint and lubuntu, up to
this new version of lubuntu 16.04. I could always install ubuntu 16.04 again as I had it working there as well, but lubuntu has been my favorite
"buntu" version and I would like to keep using it.

---

### Post by bin_bash on 2016-06-29
> **leozinho29_eu said:**
> I had this same issue with a HP printer. Cups and other dependencies were not being detected, even if installed.

To solve this, there was the hp-doctor utility, which came with hplip-gui, that made the (re)installation of them. It installed the same version of cups and the other packages, then it started to detect it.

I sincerely don't know why the installation I have made by myself was not detected.

I don't know if Brother has this sort of utility, but if it has, then it could solve the issue.

I can't grant this will work: If no other option is found: maybe, just maybe, the HP utility may solve the Brother issue. I can't grant this nor I can test now. HP has its own Unix system, so this utility may be flexible enough. This may or may not work.

Thank you for the input. From the verbiage I have read lubuntu has made the decision not to install cups by default, not sure why although I have read that some users don't like cups. I don't know why it should be this difficult to install something that has been around as long as cups?

---

### Post by bin_bash on 2016-06-30
An update here, rather than go back to an older version or struggle with something that doesn't want to work, I have opted to
install ubuntu 16.04. Which I have done and just now downloaded and installed the drivers for my Brother printer, using the instructions
from this site.
[https://sites.google.com/site/easylinuxtipsproject/15](https://sites.google.com/site/easylinuxtipsproject/15)
Quick and easy, I am now up and running with ubuntu 16.04, complete with a working printer. Lubuntu 16.04 is gone and I am happy.:)

Thank you to everyone for your input.

---

### Post by Lozio Bonzo on 2016-11-18
> **leozinho29_eu said:**
> I had this same issue with a HP printer. Cups and other dependencies were not being detected, even if installed.

To solve this, there was the hp-doctor utility, which came with hplip-gui, that made the (re)installation of them. It installed the same version of cups and the other packages, then it started to detect it.

I sincerely don't know why the installation I have made by myself was not detected.

I don't know if Brother has this sort of utility, but if it has, then it could solve the issue.

I can't grant this will work: If no other option is found: maybe, just maybe, the HP utility may solve the Brother issue. I can't grant this nor I can test now. HP has its own Unix system, so this utility may be flexible enough. This may or may not work.

 After chasing around in reaction to my old hp f350 quit, I came across this bit on YouTube which did the trick.  sudo apt-get install hplip-gui                    All now ticketyboo!

---

