---
title: "LibreOffice 4.0 Unity Integration in 12.04"
date: 2013-02-07
forum: General Help
---

### Post by Paddy Landau on 2013-02-07
I know that Ubuntu doesn't (yet) support the latest version of Libre Office, which is 4.0 (released today).

Nevertheless, I have installed it, and it works very well.

Except&#8230;

Supposedly, [LibreOffice 4.0 has Unity Integration built in]("https://www.libreoffice.org/download/4-0-new-features-and-fixes") (scroll down to "GUI", roughly halfway down the page). But it doesn't work.

Installing lo-menubar is not an answer, because it uninstalls the Libre Office menus and installs a bunch of other applications that conflict with LibreOffice 3.6 or 4.0.

Any idea what the problem is, and how to fix it? I would like the Unity menu bar to work with Libre Office.

I am using 12.04 64-bit, fully updated.

---

### Post by grahammechanical on 2013-02-07
My guess, and it is an uneducated guess is that it depends on versions of Unity that are not in 12.04. As of today 13.04 still has Libreoffice 3.6. It also has Unity 6.12.

See, what happens to 12.04 when 12.04.2 point release comes out about the middle of February. I am sure that all the work done on Unity will be brought into 12.04 at some point. Otherwise 12.04 is going to look very dated in four years time.

Regards.

P.S. I do not know what OMGUbuntu is talking about when it says

> For Ubuntu users this release finally brings support for Unity&#8217;s App Menu baked in. No more extra plugins or packages.

I have had the Libreoffice File Edit View etc., menus in the top panel with Libreoffice 3.6 on 13.04 for some months. This should not be new for Libreoffice 4. Perhaps he means it is new for Ubuntu.

---

### Post by Maharifu on 2013-02-07
Hi, I'm using Ubuntu 12.10, 64bits and the unity integration is not working here either. Perhaps it's a problem with the 64bit build?

---

### Post by vanadium on 2013-02-07
I confirm this: global menu is not working. However, it is possible again to enable the global menu for other menu's and still have LO properly  integrated with gnome.

---

### Post by kjell75 on 2013-02-07
I can confirm this does not work on 32bit 12.04 either...

---

### Post by Paddy Landau on 2013-02-07
Based on [some discussion]("http://nabble.documentfoundation.org/LibreOffice-4-0-Unity-Integration-in-Ubuntu-12-04-td4035137.html"), I believe that it will not work until 13.04.

---

### Post by vanadium on 2013-02-08
I really have a hard time making sens of this discussion, where most of the users do not seem to get your point. Anyway, I am ready to wait. I had to downgrade anyway because the bibliographic software bibus would not communicate with the newly installed version.

What is more important: are menu hotkeys (e.g. Alt+f to open the file menu) going to work this time? Without this, it is unworkable.

The HUD is no substitute. It is complementary. It is simply faster to type <Alt+o>a to open the paragraph properties than to type alt to open the HUD, type "par" or something, then having to look and select between the options that appear. The HUD on the other hand would be great as an alternative to hunting through the menu's for less frequently used options that are deeply burried into the menu structure.

---

### Post by Paddy Landau on 2013-02-08
> **vanadium said:**
> I had to downgrade anyway because the bibliographic software bibus would not communicate with the newly installed version.
That's a shame. Have you raised a bug report?

> **vanadium said:**
> What is more important: are menu hotkeys (e.g. Alt+f to open the file menu) going to work this time? Without this, it is unworkable.
I see no reason why they wouldn't work. They do currently work with the default Libre Office installation (3.5) — but not when [lo-menubar]("apt:lo-menubar") is installed. If they don't work in 13.04, this will have to be raised as a bug.

Tell you what — I'll install 13.04 on a VM and let you know how it works. It may take several hours before I get to it, though.

> **vanadium said:**
> The HUD is no substitute…
That is correct. The HUD was meant for discovery rather than for continuous use (although you can use it that way). For example, if you forget where in the menu to format the page properties, the HUD is useful. But it doesn't work when the global menu integration doesn't work!

---

### Post by vasa1 on 2013-02-08
> **vanadium said:**
> I really have a hard time making sense of this discussion, where most of the users do not seem to get your point. ...
Yes,  there was only one person there who was even close to getting Paddy's point. And the way they just requote everything is a bit tiresome. Long live mailing lists ;)

---

### Post by Paddy Landau on 2013-02-08
> **vasa1 said:**
> … the way they just requote everything is a bit tiresome.
It's a mailing list, that's why. The link that I gave is a front-end for people like me who prefer web-based forums.

---

### Post by Paddy Landau on 2013-02-08
> **Paddy Landau said:**
> I'll install 13.04 on a VM and let you know how it works.
Guess what… Unity Integration doesn't work with Libre Office 4.0.0 in Ubuntu 13.04. Perhaps it is a work in progress!

---

### Post by vanadium on 2013-02-11
> **Paddy Landau said:**
> That's a shame. Have you raised a bug report?
No, because it is a bibus issue and related to different versions of supporting libraries. On the bibus website, they indicate to stick with the distribution version.
> **Paddy Landau said:**
> 
I see no reason why they wouldn't work. They do currently work with the default Libre Office installation (3.5) &#8212; but not when [lo-menubar]("apt:lo-menubar") is installed. If they don't work in 13.04, this will have to be raised as a bug.

Are you referring to stock LO on Ubuntu 13.04 here? Because menu hotkeys in LO never worked for me on Ubuntu 12.10. The LO menu indeed is global in stock Ubuntu 12.10, but you cannot use the keyboard to pull down a menu, e.g Alt+f for the file menu or Alt+e for Edit. I disable global menus because of that. I have checked last week, but it still did not work.

---

### Post by Paddy Landau on 2013-02-11
> **vanadium said:**
> The LO menu indeed is global in stock Ubuntu 12.10, but you cannot use the keyboard to pull down a menu, e.g Alt+f for the file menu or Alt+e for Edit. I disable global menus because of that. I have checked last week, but it still did not work.
Raise a bug report and paste the link to the bug report here so that we can vote for it.

---

### Post by vanadium on 2013-02-11
I checked the Ubuntu 13.04 daily build. The current LO is the same as that on 12.10: 3.6.2.2. Menu hotkeys still do not work with the global menu.

The bug report for that is here: [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/739184](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/739184)

---

### Post by Paddy Landau on 2013-02-11
> **vanadium said:**
> The bug report for that is here: [https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/739184](https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/739184)
Thank you. I have added my vote and a comment.

---

### Post by Pepe Lebuntu on 2013-02-12
So does anybody know of a time frame for integrating the Global Menu (and HUD) into LO4.0, a la lo-menubar?

---

### Post by Kopkins on 2013-02-12
I think I read somewhere that LO 4.0 will be default in 13.04. But that doesn't mean that it is right now or that everything is working. I was under the impression that the Unity integration would work with any version of Ubuntu but I guess that's wrong. They still have a couple months before release, and LO was only a few days ago. I say they still have time to upgrade a few packages so that LO 4.0 has integration. 

Kopkins

---

### Post by wrzomar on 2013-02-17
Menubar extension is still working with LO 4.0, but it can't be installed by dpkg. But remember to copy its files to "/opt/libreoffice4.0/share/extensions/menubar/" NOT "/usr/lib/libreoffice/share/extensions/menubar/". You can unpack deb package using midnight commander. Menubar is not working with LO Startcenter!

---

### Post by Paddy Landau on 2013-02-17
> **wrzomar said:**
> Menubar extension is still working with LO 4.0, but it can't be installed by dpkg. But remember to copy its files to "/opt/libreoffice4.0/share/extensions/menubar/" NOT "/usr/lib/libreoffice/share/extensions/menubar/". You can unpack deb package using midnight commander.
Thank you for the advice. Unfortunately, I don't know how to follow your instructions: how do I get the [FONT=Lucida Console].deb[/FONT] file? I thought of using the following:
```
sudo apt-get install --download-only lo-menubar
```But the messages indicate that it would uninstall [FONT=Lucida Console]libreoffice-debian-menus[/FONT] and install several other conflicting packages, and so will not work.

Please would you explain how to obtain the deb in order to install it into [FONT=Lucida Console]/opt/[/FONT]… as per your instructions?

> **wrzomar said:**
> Menubar is not working with LO Startcenter!
I believe that that has always been the case.

---

### Post by wrzomar on 2013-02-17
I downloaded it from: 
[http://www.ubuntuupdates.org/package/core/precise/universe/proposed/lo-menubar]("http://www.ubuntuupdates.org/package/core/precise/universe/proposed/lo-menubar")

Use mc to open lo-menubar_0.1.1-0ubuntu0.1_<your architecture>.deb.
There is folder CONTENTS/usr/lib/libreoffice/share/extensions/menubar with its contents. You need to copy entire menubar folder to /opt/libreoffice4.0/share/extensions/ .
This is how it would look like for amd64:
```
/opt/libreoffice4.0/share/extensions/menubar/
&#9500;&#9472;&#9472; Jobs.xcu
&#9500;&#9472;&#9472; Linux_x86_64
&#9474;** &#9492;&#9472;&#9472; menubar.uno.so
&#9492;&#9472;&#9472; META-INF
    &#9492;&#9472;&#9472; manifest.xml
```

To add LO 4.0 icons to launcher, just follow instructions from
[http://askubuntu.com/questions/65900/how-can-i-change-default-settings-for-new-users]("http://askubuntu.com/questions/65900/how-can-i-change-default-settings-for-new-users")

Ubuntu's default favorites are:
```
['ubiquity-gtkui.desktop', 'nautilus-home.desktop', 'firefox.desktop', 'libreoffice-writer.desktop', 'libreoffice-calc.desktop', 'libreoffice-impress.desktop', 'ubuntu-software-center.desktop', 'ubuntuone-installer.desktop', 'gnome-control-center.desktop']
```

just change every ```
libreoffice-<something>.desktop
``` to ```
libreoffice4.0-<something>.desktop
```.

After compilation of scheme override reset your launcher using command:
```
gsettings reset com.canonical.Unity.Launcher favorites
```

I hope it would be helpful.

---

### Post by Paddy Landau on 2013-02-18
> **wrzomar said:**
> I downloaded it from: 
[http://www.ubuntuupdates.org/package/core/precise/universe/proposed/lo-menubar](http://www.ubuntuupdates.org/package/core/precise/universe/proposed/lo-menubar)
…
Thank you, wrzomar. It worked for me…

But…

[Bug #739184]("https://bugs.launchpad.net/ubuntu/+source/libreoffice/+bug/739184") raised its ugly head, so I had to remove lo-menubar again. :(

I guess we'll have to wait until 13.04 (for those who use non-LTS) or 14.04 (for those who use LTS).

---

### Post by wrzomar on 2013-02-18
This bug affects me too, but I like HUD to much. ;)

PS. Don't reset launcher icons with ubuntu-tweak after scheme override. It removed all. Use gsettings instead.

---

### Post by Paddy Landau on 2013-02-18
> **wrzomar said:**
> This bug affects me too, but I like HUD to much. ;)
Unfortunately, I work faster (for certain tasks) when using the shortcut mnemonics.

> **wrzomar said:**
> PS. Don't reset launcher icons with ubuntu-tweak after scheme override. It removed all. Use gsettings instead.
Thanks, but I won't bother trying to reset the Launcher icons. It's much easier to simply "Lock to Launcher" while LibreOffice is running.

---

### Post by wrzomar on 2013-02-18
It's for newly created users e.g., guest session's user.

---

### Post by Paddy Landau on 2013-02-18
> **wrzomar said:**
> It's for newly created users e.g., guest session's user.
Ah, of course! I hadn't thought of that.

---

### Post by ronso0 on 2013-07-16
> **wrzomar said:**
> I downloaded it from: 
[http://www.ubuntuupdates.org/package/core/precise/universe/proposed/lo-menubar](http://www.ubuntuupdates.org/package/core/precise/universe/proposed/lo-menubar)

Use mc to open lo-menubar_0.1.1-0ubuntu0.1_<your architecture>.deb.
There is folder CONTENTS/usr/lib/libreoffice/share/extensions/menubar with its contents. You need to copy entire menubar folder to /opt/libreoffice4.0/share/extensions/ .

On 12.04 wit LO 4.0.4.2, it works for me if I just copy whole folder CONTENTS/usr/lib/libreoffice/share/extensions/menubar to...well /usr/lib/libreoffice/share/extensions/ .
no reset necessary.
was looking for a quick solution, didn't want to reinstall 4.xx from repos. which may be 'cleaner', but heij... it works o_O

---

