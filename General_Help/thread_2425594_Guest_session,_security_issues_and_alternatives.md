---
title: "Guest session, security issues and alternatives"
date: 2019-08-27
forum: General Help
---

### Post by volterral on 2019-08-27
Hello,
We're trying to install Lubuntu 18.04 on some computers in a public library, and we need the data created by users to be deleted when logging out or rebooting. I read in the Ubuntu documentation ([https://help.ubuntu.com/community/CustomizeGuestSession](https://help.ubuntu.com/community/CustomizeGuestSession)) that it can be enabled by installing LightDM but it says it was disabled due to a security bug which consist of AppArmor not limiting the guest session.

Ubuntu 16.04 and its variants appear to be unaffected, but the problem with installing Lubuntu 16.04 is that the packages that have 3 years of support are not supported now. As it's a lightweight flavor, it's the most appropriate choice of the Ubuntu flavors.

I thought of making an ordinary user account and automatically delete its stored data when logging off or rebooting, but I would like to know if this is possible. I it were, I would also like to know if I can make a skeleton directory for such account like you can do with the guest session because we would like the guest to have some files in the desktop folder when logging in (and we want them not to be removed).

Thanks in advance.

---

### Post by HermanAB on 2019-08-27
/etc/skel is used for new user accounts.

I suppose you can make a script that will delete the guest account and make a new guest account whenever the guest logs out.

---

### Post by TheFu on 2019-08-27
Yes, guest sessions were disabled due to a security issue. I guess they didn't think it could be fixed, to the feature was removed from newer releases.

Yes, you can setup 1 or more accounts using skel files and pre-copy the files over. The creation of accounts has the ability to run arbitrary scripts to setup anything you need, including removing all files that were previously there.  adduser or **useradd** (I never remember which) are the 2 commands to add users. 1 is friendlier. You want the other one that provides complete control. Checked the manpages - you want useradd.

How the HOME directory should be setup would completely depend on the purpose of the computer.  If it is to be a full Linux computer where students can run anything, then there would be different techniques than if it was just a web browser platform.  

For a web-browser only platform, I'd probably use either something based on ChromiumOS or TinyCore instead of Ubuntu.  ChromiumOS works like schools use chromebooks, so anybody with a gmail account could login and have access to their information stored in google.  There is a Guest mode too, but it doesn't delete files stored under it by default.  When someone returns their access to the computer, a librarian could run a script to login and remove all the Guest files.  Perhaps this could be automated. Since ChromiumOS is F/LOSS, you should be able to customize the Guest login process to remove files.

Do you plan to allow people to connect their USB devices to the computer or will they only have physical access to the keyboard and mouse?  Restricting physical access prevents many security issues.  With physical access, experts can almost always hack in and get around many intended security steps.  But access to USB devices might be a requirement.  If so, then TinyCore probably wouldn't be a good choice, but both ChromiumOS and Ubuntu+LXQt would be ok.

ChromiumOS would be more secure, provided you refresh the install monthly.  There are commercial support vendors who provide an inplace upgrade similar to what ChromeOS does.  If you aren't aware, ChromeOS only runs on specifically approved-by-google hardware which doesn't include regular PCs or laptops.  I know a college student who has been running CloudReady on her old laptop for over a year and using it for coursework.  I've had a few chromebooks since 2012-ish. I believe a chromebook running chromeOS is the most secure useful platform with networking in the world today, but one of the lease private platforms, unfortunately.

TinyCore is used for many kiosk needs.  It is really small and only has the minimum needed to run a GUI.  Without a web browser, it is 16MB for the entire OS.  It runs from RAM, so it is very fast on almost any hardware.  

Most other really small distros are complete security failures. They run everything as root, which simply cannot be allowed if you care anything at all about security.

---

