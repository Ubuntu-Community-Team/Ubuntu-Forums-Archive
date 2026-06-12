---
title: "How to re-install Google browser"
date: 2024-08-24
forum: General Help
---

### Post by satimis on 2024-08-24
Hi all,

Ubuntu 24.04

Revently Google browser continues to be attacked, receiving advertising materials and/or false warnings.  I have to delete them manually.

Please advise whether I need to re-install Google browser?  If YES please advise the steps to remove the old one and install a new Google browser.  Thanks.

Regards

---

### Post by currentshaft on 2024-08-24
[https://www.google.com/chrome/browser-tools/](https://www.google.com/chrome/browser-tools/)

Download the deb

sudo dpkg -i google-chrome-stable_current_amd64.deb

---

### Post by satimis on 2024-08-24
> **currentshaft said:**
> [https://www.google.com/chrome/browser-tools/](https://www.google.com/chrome/browser-tools/)

Download the deb

sudo dpkg -i google-chrome-stable_current_amd64.deb
Hi,

Thanks for your advice.

Do I need to un-install the running Google browser first before running your suggested command?

Thanks

Regards

---

### Post by currentshaft on 2024-08-24
It shouldn't be necessary, but you it shouldn't hurt to uninstall either:

sudo apt remove "google-chrome*"

---

### Post by satimis on 2024-08-25
Hi currentshaft,

Tried both versions - withtout uninstall google-chrome and uninstall google-chrome first.  The intruder still popup saying from Nortor that my PC  is infected, needing to delete it.

The link coming from "cr5jbie071bc73932ung.enhanceflows.com/04/........"

How can I remove it?  Thanks

Regards

---

### Post by currentshaft on 2024-08-25
> **satimis said:**
> Hi currentshaft,

Tried both versions - withtout uninstall google-chrome and uninstall google-chrome first. The intruder still popup saying from Nortor that my PC is infected, needing to delete it.

The link coming from "cr5jbie071bc73932ung.enhanceflows.com/04/........"

How can I remove it? Thanks

Regards

You have malware on your system. Back up any remaining data and reinstall the OS.

---

### Post by satimis on 2024-08-25
> **currentshaft said:**
> You have malware on your system. Back up any remaining data and reinstall the OS.
Sorry, no.  Problem comes from Google-chrome.  There is no such problems running Firefox browser.

Following link helps me out:
Remove Typicalsecuritydevice.com (virus removal guide)
...//malware.guide/adware/remove-typicalsecuritydevice-com-virus-removal-guide/#google_vignette

Read more at: ...//malware.guide/adware/remove-typicalsecuritydevice-com-virus-removal-guide/#google_vignette

But still having some more.  I'll keep watching

Regards

---

### Post by currentshaft on 2024-08-25
> **satimis said:**
> Sorry, no. Problem comes from Google-chrome

Following link helps me out:
Remove Typicalsecuritydevice.com (virus removal guide)
...//malware.guide/adware/remove-typicalsecuritydevice-com-virus-removal-guide/#google_vignette

Read more at: ...//malware.guide/adware/remove-typicalsecuritydevice-com-virus-removal-guide/#google_vignette

But still having some more. I'll keep watching

Regards

It really doesn't. You got tricked into installing malware and now your system is compromised.

This has nothing to do with Chrome, other than you possibly used it to become infected.

---

### Post by satimis on 2024-08-25
> **currentshaft said:**
> It really doesn't. You got tricked into installing malware and now your system is compromised.

This has nothing to do with Chrome, other than you possibly used it to become infected.
I followed their steps on;
Remove Typicalsecuritydevice.com from Google Chrome

to remove:
1.  Typicalsecuritydevice.com
and then again to remove
2.  free.aditsafeweb.com

They don't popup anymore

On "Not allowed to send notifications" item
I can add the websites not allowing to send notification

---

### Post by currentshaft on 2024-08-25
> **satimis said:**
> I followed their steps on;
Remove Typicalsecuritydevice.com from Google Chrome

to remove:
1. Typicalsecuritydevice.com
and then again to remove
2. free.aditsafeweb.com

They don't popup anymore

On "Not allowed to send notifications" item
I can add the websites not allowing to send notification

You're literally being phished/tricked into divulging more credentials and/or installing more malware.

---

### Post by satimis on 2024-08-25
> **currentshaft said:**
> You're literally being phished/tricked into divulging more credentials and/or installing more malware.
Hi,

I only install packages on Ubuntu REPO or running their AppImages.  I never install new packages from unknown source or induced by intruders.

Up to now there is no further disguised intruders popup on Google-Chrome.  Besides when I start Google-Chrome the first time they would continue popup.  But now it doesn't happen.  I'll continue watch them.

Regards

---

### Post by werewulf75 on 2024-08-26
The whole thing still smells very 'phishy'! Best follow the previous advice and back up your data, then get rid of your current install of Ubuntu, reformat, and reinstall Ubuntu. And then keep away from Chrome - it's neither safe, nor private - it's a complete data thief! Use something like Librewolf, Firefox, Waterfox or similar private browser.

Better safe than sorry!

---

### Post by satimis on 2024-08-26
> **werewulf75 said:**
> The whole thing still smells very 'phishy'! Best follow the previous advice and back up your data, then get rid of your current install of Ubuntu, reformat, and reinstall Ubuntu. And then keep away from Chrome - it's neither safe, nor private - it's a complete data thief! Use something like Librewolf, Firefox, Waterfox or similar private browser.

Better safe than sorry!
Up-to-now no further intruders coming on Google-chrome browsing.  That document, link, works for me.  Neither there are phishing links popup on starting Google-chrome the first time.

I have all working data saved on another drive, not the drive running Ubuntu.

Regards

---

### Post by werewulf75 on 2024-08-26
Well, it's your funeral. ;)

---

