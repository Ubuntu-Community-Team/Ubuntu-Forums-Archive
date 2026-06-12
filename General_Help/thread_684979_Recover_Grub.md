---
title: "Recover Grub"
date: 2008-02-01
forum: General Help
---

### Post by benniebrown07 on 2008-02-01
Once i installed Mandriva it didnt give me the option to start Ubuntu. But all my stuff is still here. So I bumped around the forums and found that ubuntu's grub was overwritten by mandriva's. No one really told me how to fix it so i bumped around again found some guides but Im a beginner and i dont really understand what they mean. So i was wondering if someone could dumb down the process for me.

---

### Post by taurus on 2008-02-01
You have a few options here.

1.  Open /boot/grub/grub.conf (or does Mandriva uses /boot/grub/menu.lst just like Ubuntu?) and add an entry for Ubuntu.

If you are not sure how to add an entry for Ubuntu under Mandriva, look at /boot/grub/menu.lst from Ubuntu for howto.

2.  [https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles](https://help.ubuntu.com/community/?action=fullsearch&context=180&value=grub&titlesearch=Titles)

3.  [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by Butthead on 2008-02-01
This might be of help to you:

[SIZE="2"](especially since I was forced to do it once too[/SIZE]). :eek:

**restore grub** [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

