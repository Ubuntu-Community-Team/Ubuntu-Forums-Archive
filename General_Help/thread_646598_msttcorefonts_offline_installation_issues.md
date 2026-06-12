---
title: "msttcorefonts: offline installation issues"
date: 2007-12-21
forum: General Help
---

### Post by jenkinbr on 2007-12-21
> **jonathanjg said:**
> This worked for me, but there is probably a more elegant way to do this (but not at 2am!!):-

[LIST=1][*]Get the following files from a friend, another pc or download manually from the internet by some means (like in my earlier post above):-
andale32.exe  comic32.exe   impact32.exe  verdan32.exe
arial32.exe   courie32.exe  times32.exe   webdin32.exe
arialb32.exe  georgi32.exe  trebuc32.exe
[*]Create the following directory and put them into it: /tmp/mstt/
[*]Manually launch the postinstall script, telling it to use your local copy:
/usr/sbin/update-ms-fonts /tmp/mstt
[*] Remove your temp directory
rm -rf /tmp/mstt/
[*] To ensure apt/dpkg is happy rerun
 apt-get install msttcorefonts[/LIST]

I have tried following these instructions, but when I try to launch update-ms-fonts, I find that the file does not exist. A listing of the directory /usr/sbin verifies this.  msttcorefonts is now left broken and cannot be completely installed or removed due to the fact that I do not have internet at home.

Apparently, someone else also had a similar problem to mine, as I found in the following post:

> **raul_ said:**
> ```

 /usr/sbin/update-
update-alternatives       update-gconf-defaults     update-pango-modules
update-binfmts            update-gdkpixbuf-loaders  update-pangox-aliases
update-ca-certificates    update-gtk-immodules      update-passwd
update-catalog            update-inetd              update-rc.d
update-default-aspell     update-initramfs          update-usbids
update-default-ispell     update-java-alternatives  update-xmlcatalog
update-default-wordlist   update-mime               update-xpdfrc
update-dictcommon-aspell  update-mozilla-chrome
update-flashplugin        update-openoffice-dicts

```

No update-ms-fonts here :-?

Any suggestions?

---

### Post by ruibernardo on 2007-12-21
Hi jenkinbr,

from the [debian changelog for gutsy]("http://changelogs.ubuntu.com/changelogs/pool/multiverse/m/msttcorefonts/msttcorefonts_2.2/changelog"), the "update-ms-fonts" command is no longer installed since 01 May 2007, so this should only apply to Ubuntu 7.10 Gutsy:

> msttcorefonts (2.0) unstable; urgency=low

  * **No longer install the update-ms-fonts** command. It's only
    needed upon package installation/upgrade, so it's now part
    of the package postinst. [B]In the rare case that it needs to
    be ran again, just dpkg-reconfigure[/B] (Closes: #401698 ).So I suppose that now you have to run
```
sudo dpkg-reconfigure msttcorefonts
```to complete the install. 

Can you confirm it?

---

### Post by jenkinbr on 2007-12-21
Will give that a try and reply with my results.

---

### Post by adben on 2008-02-13
> **epimeteo said:**
> Hi jenkinbr,

from the [debian changelog for gutsy]("http://changelogs.ubuntu.com/changelogs/pool/multiverse/m/msttcorefonts/msttcorefonts_2.2/changelog"), the "update-ms-fonts" command is no longer installed since 01 May 2007, so this should only apply to Ubuntu 7.10 Gutsy:

So I suppose that now you have to run
```
sudo dpkg-reconfigure msttcorefonts
```to complete the install. 

Can you confirm it?

Doesn't work

sudo dpkg-reconfigure msttcorefonts
/usr/sbin/dpkg-reconfigure: msttcorefonts is broken or not fully installed


im behind a proxy, that blocks.exe files 


i try too

   1. Get the following files from a friend, another pc or download manually from the internet by some means (like in my earlier post above):-
      andale32.exe comic32.exe impact32.exe verdan32.exe
      arial32.exe courie32.exe times32.exe webdin32.exe
      arialb32.exe georgi32.exe trebuc32.exe
   2. Create the following directory and put them into it: /tmp/mstt/
   3. Manually launch the postinstall script, telling it to use your local copy:
      /usr/sbin/update-ms-fonts /tmp/mstt
   4. Remove your temp directory
      rm -rf /tmp/mstt/
   5. To ensure apt/dpkg is happy rerun
      apt-get install msttcorefonts


 andale32.exe: no valid cabinets found

what else can i do?

---

### Post by jenkinbr on 2008-02-25
Sorry about the *extreamly* late reply, but reconfigureing didn't help.

My fix was to dl the font files directly from sourceforge and use cabextract to extract them manually.  Then, in nautilus (gksu nautilus), I edit the location to read 
```
fonts:///
``` copy the font files in, and call it good.  This has seemed to work, as I am able to use the fonts.

---

### Post by ruibernardo on 2008-03-04
Hi jenkinbr,

this is important to many offline Ubuntu users. I though that the reconfigure thing would work (the changelog file pointed that way).
> **jenkinbr said:**
> Then, in nautilus (gksu nautilus), I edit the location to read 
```
fonts:///
``` copy the font files in, and call it good. This has seemed to work, as I am able to use the fonts.
Simple solution indeed.

Thanks.

---

