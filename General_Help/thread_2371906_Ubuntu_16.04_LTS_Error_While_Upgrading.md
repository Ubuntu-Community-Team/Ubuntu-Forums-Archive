---
title: "Ubuntu 16.04 LTS Error While Upgrading"
date: 2017-09-19
forum: General Help
---

### Post by mophead2 on 2017-09-19
I am a relative newbie to Linux. I posted this in the Ubuntu StackExchange but never got the issue resolved. Hoping you guys could help. Here is the link to the Stack Exchange problem:

[https://askubuntu.com/questions/957207/cryptsetup-error-while-doing-sudo-apt-upgrade](https://askubuntu.com/questions/957207/cryptsetup-error-while-doing-sudo-apt-upgrade)

Thanks for the help!

---

### Post by oldos2er on 2017-09-20
You're more likely to get help if you post the error messages here, and things you've tried, rather than asking people to read an external link.

---

### Post by mophead2 on 2017-09-20
I receive an error when I try to post a long message. So I made a pastebin. 
[https://pastebin.ubuntu.com/25582305/](https://pastebin.ubuntu.com/25582305/)Also to note, I am booting from a USB and am using Ubuntu 16.04 LTS. Here are screenshots of the error,
it would take me long time to type these out, hope this is ok:
[pasteboard.co/GL2LJjd.png]("http://Also to note, I am booting from a USB and am using Ubuntu 16.04 LTS. Here are screenshots of the error, it would take me long time to type these out, hope this is ok: pasteboard.co/GL2LJjd.png pasteboard.co/GL2M4Kz.png")
[pasteboard.co/GL2M4Kz.png]("http://pasteboard.co/GL2M4Kz.png")

---

### Post by ian-weisser on 2017-09-20
Looks like the AskUbuntu folks are doing a good job trying to help you.
Be patient, helpful, and positive.

On line 785 of your pastebin, the command
[code][COLOR=#000000]sudo apt-get dist-upgradesudo dpkg -P --force-remove-reinstreq package_name[/COLOR][code]
obviously isn't what you are really running as part of your upgrade.

Do you use cryptsetup? If not, one simple solution is to uninstall it.

---

### Post by mophead2 on 2017-09-21
Thanks. Uninstalling it before running my upgrade worked.

---

