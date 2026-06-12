---
title: "Which virus protection software does Ubuntu 22.04 use?"
date: 2022-04-27
forum: General Help
---

### Post by fabi651 on 2022-04-27
Dear community,

On the Ubuntu Desktop [website]("https://ubuntu.com/desktop") I read, that Ubuntu 22.04 has a built-in firewall and virus protection software (see attachment).
I think the firewall must be ufw, right?
But which virus protection software does Ubuntu use? I can not find it in my applications.

Thanks!
Fabian







[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290347&stc=1[/IMG]

---

### Post by HermanAB on 2022-04-27
In general, Linux doesn’t use virus protection software. It is more efficient to fix potential security problems, than to try to detect thousands of pieces of malware.  ClamAV is a Linux filter used to remove Windows malware from email on a mail server.  It doesn’t do anything for Linux users.  If you ever find a Linux virus, please send it to me, I would like to take a look at it.

---

### Post by fabi651 on 2022-04-27
> **HermanAB said:**
> In general, Linux doesn’t use virus protection software. It is more efficient to fix potential security problems, than to try to detect thousands of pieces of malware.  ClamAV is a Linux filter used to remove Windows malware from email on a mail server.  It doesn’t do anything for Linux users.  If you ever find a Linux virus, please send it to me, I would like to take a look at it.

Ah okay, thanks for the information.
I was only surprised when I read that on the homepage - so maybe they meant ClamAV :mrgreen:

---

### Post by grahammechanical on 2022-04-27
> ufw is a program for managing a netfilter firewall and aims to provide an easy to use experience for the user.
 
Uncomplicated Fire Wall (UFW) is a firewall not a virus detector. It is in the Ubuntu software store. It can be used to block ports that might be used to access a machine connected to the internet.

An explanation of the phrase "virus protection software."

[https://askubuntu.com/questions/42284/what-is-the-ubuntu-built-in-virus-protection](https://askubuntu.com/questions/42284/what-is-the-ubuntu-built-in-virus-protection)

Regards

---

### Post by GhX6GZMB on 2022-04-27
> **grahammechanical said:**
> 
An explanation of the phrase "virus protection software."

[https://askubuntu.com/questions/42284/what-is-the-ubuntu-built-in-virus-protection](https://askubuntu.com/questions/42284/what-is-the-ubuntu-built-in-virus-protection)


Yes, the phrasing on the Ubuntu site is an unwarranted marketing plug. Good link, Graham.

---

### Post by issh on 2022-04-27
Seems quite misleading... probably a marketing ploy to new users and businesses. That is implying that there is a specific piece of software like an AntiVirus Program or Suite included with Ubuntu for free. That's what the average Windows user or probably even a Windows Server admin would think when they read that. It's dishonest and misleading. How about coining a new term instead that encompasses the AppArmor feature, Firewall, sandboxing of Snaps, Flatpaks, and AppImages? Why not just use the phrase, "Linux Hardened for Security" instead?

---

### Post by TheFu on 2022-04-27
Marketing providing "false facts", I suppose.  Linux isn't like a commercial OS. Thousands of project teams create the software and Canonical snags the version of that software to place into repos.  Just because a package isn't pre-installed, doesn't mean it isn't available. It certainly shouldn't matter when comparing OS-A vs OS-B, since what is preinstalled is hardly difficult to resolve in a scripted, predictable, way, available to **every** admin on the system.

To my mind, the best AV software (wetware?) is between our ears.  Use that, unless you have a contractual mandate created by some corporation used to MSFT-only solutions.  I've been there. We installed, ran, and updated clam AV to meet the requirements of the contract. It was a Professional Errors & Omissions insurance policy, BTW. Had we not had current, supported, OSes and AV on the systems, the payments to that policy would be completely wasted and it would void the coverage.  The second we left the company that mandated the E&O insurance, we canceled the policy and removed clam AV except on our email gateway and on Windows systems. Only 2 of the Linux/Unix systems kept it - the email server and our document management server - both of which could be a transfer method from Windows to Windows.  We cared about our clients.

If you run as an unprivileged user, which you should, then there is very little that 99.9% of viruses can actually accomplish against a well-maintained, patched, Unix-like OS.

Plus, having daily, automatic, 'pulled', backups will help restoration of any services and files that do get compromised. Versioned backups are a mandate against viruses, malware, cryptoware, and failing hardware which can cause data loss or data corruption.

*Linux Hardened for Security* has historically meant locking down a system by professionals who care more about security than usability.  Usually there's a 300+ item checklist to be worked through, since the defaults for pretty much every Linux desktop doesn't implement those 300+ items.

AppImages don't provide any security and snaps provide too limited accessibility, BTW, IMHO.  Of the two, I use appimages because they tend to work much more often than snaps on my systems.  Thanks to flatpaks allowing local control, I believe they are the right mix of usability and security, but I don't have any first-hand experience to actually KNOW if that is true.

---

### Post by fabi651 on 2022-04-28
Thanks a lot to you all for your detailed answers! :)

---

