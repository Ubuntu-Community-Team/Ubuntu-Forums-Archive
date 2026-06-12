---
title: "newbie needs help"
date: 2007-02-22
forum: General Help
---

### Post by Bashed on 2007-02-22
I'm brand new to Ubuntu. I'm coming from Vista, Office 2007 and the really crisp, clean Windows interface / fonts, etc.

**I need to know the following please:**
- how do I get the fonts in Ubuntu crisp and as close as possible as to Windows?
- any exporter / converter for Outlook to Thunderbird?
- where do I find the default Firefox bookmark file? I need to replace it with my own from Vista
- any workaround / trick to get Roboform working on Linux?

I'm using Ubuntu Dapper on desktop

---

### Post by bettlebrox on 2007-02-22
> **TalkJesus said:**
> I'm brand new to Ubuntu. I'm coming from Vista, Office 2007 and the really crisp, clean Windows interface / fonts, etc.

**I need to know the following please:**
- how do I get the fonts in Ubuntu crisp and as close as possible as to Windows?
- any exporter / converter for Outlook to Thunderbird?
- where do I find the default Firefox bookmark file? I need to replace it with my own from Vista
- any workaround / trick to get Roboform working on Linux?

I'm using Ubuntu Dapper on desktop
1. Fonts: [http://www.debianadmin.com/install-microsoft-corewindows-truetypeubuntu-titlemacintosh-fonts-in-ubuntu.html](http://www.debianadmin.com/install-microsoft-corewindows-truetypeubuntu-titlemacintosh-fonts-in-ubuntu.html)
2. I thought T-bird could import Outlook pst files?
3. Look in ~/.mozilla/firefox/ and there'll be a directory with a random name, usually it ends in .default. In that directory is a file named bookmarks.html that is your default bookmark file. If you want to create default bookmarks for all new users look at /etc/firefox/profile/bookmarks.html . Make a copy of either file before you change them.
4. Roboform? Is this what you mean [http://www.roboform.com/](http://www.roboform.com/) ? Try a native app such as gnome-keyring-manager .

---

### Post by Bashed on 2007-02-22
Thanks, but I'm still confused on the font part.

I already have the same font preference as shown in the first few pictures.

I also ran via terminal:
sudo apt-get install msttcorefonts
sudo apt-get install ttf-ubuntu-title
sudo mv fonts.txt .fonts.conf (this file was inside /home/chad)
sudo apt-get install fondu

Fonts still look choppy and poor in Firefox.  I'm confused on this. Please help.

---

### Post by Bashed on 2007-02-22
I also so no option to import mail in Thunderbird, only "Communicator"

---

### Post by slackware on 2007-02-22
In Firefox, go to Edit - Preferences - Content, and try your preferred font in the Default font section. See, if that can make difference for you.

---

### Post by Bashed on 2007-02-22
Its not firefox, it is global in Ubuntu. In Vista, FF has default Times New Roman on 16, same here in Ubuntu but the font is horrible anyway.

I saved fonts.conf inside /home directory, logged out and back in as suggested in the article, same problem.

See attached please

Quick other question: I have a MS Intellipoint Wireless Lasermouse 6000. The back button is void in Ubuntu where it acts as "back" in Vista correctly. Any drivers for this? Their (MS) does not have linux based drivers, naturally of course.

---

### Post by slackware on 2007-02-22
While I'm not familiar with that specific mouse, try these links. Hopefully it will lead you in the right direction.

[http://www.cs.cornell.edu/~djm/ubuntu/#enable-5button-mouse](http://www.cs.cornell.edu/~djm/ubuntu/#enable-5button-mouse)
[http://www.ubuntuforums.org/showthread.php?t=316441](http://www.ubuntuforums.org/showthread.php?t=316441)

---

### Post by Bashed on 2007-02-23
Thanks for the tip on the mouse.  

What about the fonts? Why are the fonts not super quality like Windows by default? I'm not understanding this

---

### Post by bettlebrox on 2007-02-23
Do you have LCD monitor? If you do turn on anti-aliasing (or sub-pixel smoothing the font preferences thingy).

---

### Post by Bashed on 2007-02-23
I do but its the nice shiny crystal clear Sony laptop LCD (Vaio) only a few months old.  Its not like the older LCD's without that brightness technology.

Why is it that by default Ubuntu's fonts are not crisp like Windows or MAC? Just curious. Its rather strange.

---

