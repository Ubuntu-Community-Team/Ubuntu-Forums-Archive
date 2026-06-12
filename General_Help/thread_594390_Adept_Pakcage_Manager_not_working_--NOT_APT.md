---
title: "Adept Pakcage Manager not working --NOT APT"
date: 2007-10-27
forum: General Help
---

### Post by jackmg on 2007-10-27
This is an update to a previous posting I made earlier tonight. I mistakenly referred to the program as Apt package manager. Actually, it is the Adept Package Manager. I had no trouble using it in earlier versions of Ubuntu. I recently installed version 7.1 and can not use Adept. When I install it and try to use it I get an opening message saying that no administrator rights are available and Adept will make no system changes. All options are grayed out. I can scroll through package descriptions but can not apply anything. How do I fix this? Thanks in advance for any suggestions.

---

### Post by brennydoogles on 2007-10-27
> **jackmg said:**
> This is an update to a previous posting I made earlier tonight. I mistakenly referred to the program as Apt package manager. Actually, it is the Adept Package Manager. I had no trouble using it in earlier versions of Ubuntu. I recently installed version 7.1 and can not use Adept. When I install it and try to use it I get an opening message saying that no administrator rights are available and Adept will make no system changes. All options are grayed out. I can scroll through package descriptions but can not apply anything. How do I fix this? Thanks in advance for any suggestions.

maybe try opening a Terminal window (Alt+F2) and typing ```
gksudo adept
``` and then entering your password.

---

### Post by jackmg on 2007-10-27
Thanks for responding. I tried your suggestion. The prompt returned after running the command but still no change in how Adept Manager is working. This is the message I get when I load Adept Package Manager:

"You will not be able to change your system settings in any way (install, remove, or upgrade software) because this application needs special administrator (root) privileges. Please run it as root or through kdesu or sudo programs to be able to perform these actions."

I never had this problem in previous versions of Ubuntu. Any ideas on solving this?

Thanks.

---

### Post by jackmg on 2007-10-27
As an added wrinkle to this problem with Adept Package Manager, now I can not remove the program from the system. A message tells me that other programs are using it. How do I get Adept Manager to work?

Thanks.

---

### Post by oldos2er on 2007-10-28
You want to run 'kdesu adept'. 'gksudo is for Gnome.
What program are you trying to remove?

---

