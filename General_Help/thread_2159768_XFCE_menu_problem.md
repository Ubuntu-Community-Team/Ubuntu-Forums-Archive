---
title: "XFCE menu problem"
date: 2013-07-04
forum: General Help
---

### Post by drfox on 2013-07-04
I have a problem with the menu editor in Xubuntu 13.04. in that I have a couple apps which show up in the menu which I don't see when I run Settings Manager>Main Menu.
Specifically, I have uninstalled LibreOffice 4.0 from Synaptic, and I have installed LO 4.1 from the LO website (using dpkg -i). All the icons and programs from 4.1 are showing up, both in the menu and in the menu editor, but LO Writer 4.0 and LO 4.0 are showing in the menu under Office. They do not have icons because their icons were removed when I removed LO 4.0. They do not show up in the list of items when I run Settings Manager>Main Menu
I have searched for a file to edit, but I have not found the proper file. Can you help?
Thanks very much.
Larry

---

### Post by Frogs Hair on 2013-07-04
Hello drfox 

I have resolved this in the XFCE session by opening Session and Startup > Session  and clearing saved sessions . Strange , because I don't save my sessions.

---

### Post by drfox on 2013-07-04
> **Frogs Hair said:**
> Hello drfox 

I have resoved tihis in the XFCE session by opening Session and Startup > Session  and clearing saved sessions . Strange , bucause I don't save my sessions.

Thanks, Frogs Hair, but I tried it and it didn't work for me. I tried logging out and in again, still no luck.
There has to be a default menu somewhere, maybe under /usr which has the code in it...
Larry

---

### Post by Frogs Hair on 2013-07-04
It may be in alacarte if you can locate it . I have just the XFCE session running in Ubuntu and not Xubuntu and I'm guessing the folder setup is different in the file system.

---

### Post by Bashing-om on 2013-07-04
drfox; Hi !

As in xfce4;
Every application installs a .desktop file in /usr/share/applications/ that specifies application settings (name, comment, exec command, icon, menu, etc).
The files in the directories are editable ...
And see here:
creating a customized menu:
[http://forum.xfce.org/viewtopic.php?id=7738](http://forum.xfce.org/viewtopic.php?id=7738)

[INDENT][INDENT]knowledge==ability[/INDENT][/INDENT]

---

### Post by drfox on 2013-07-04
Thanks Bashing-on. I looked at all the files in /usr/share/applications, and there are no LibreOffice 4.0 entries.
Interestingly, it shows that the "Main Menu" program *is* alacarte, which may explain this discrepancy:
I use Cairo-Dock for eye candy as my bottom dock. Its Applications Menu does not show the 4.0 programs, but the XFCE Applications Menu (in my XFCE panel left side dock) does show the entries. Oh well, it will probably correct itself later this month when I upgrade to the 13.10 Alpha 2.
Thanks for looking at my problem, and if you have any other suggestions, I'll be happy to try them.
Larry

---

### Post by Bashing-om on 2013-07-04
drfox; Welp ... that kinda set me back .. seems things do not always go as was planned ... HUh .

Ok how bout looking from another direction:
xfce4 Panel config files are where :
/home/<user_name>/.config/xfce4/xfconf/xfce-perchannel-xml/xfce4-panel.xml
also see:
[http://git.xfce.org/xfce/xfconf/tree/docs/spec/perchannel-xml.txt](http://git.xfce.org/xfce/xfconf/tree/docs/spec/perchannel-xml.txt)

Gotta be something somewhere that point to some application.

[INDENT][INDENT]hey it's ubuntu, there is a way[/INDENT][/INDENT]

---

### Post by drfox on 2013-07-04
You got me on the right track, Bashing-om! I looked at the code in /home/user/.config/xfce4/panel/launcher(s). Each of the launchers referred to /home/user/.local/share/applications.  
The faulty (leftover) files were in that directory, plain as day! I deleted them and all is as it should be, at least until I tweak my system some more, but hey it's x/ubuntu, which is essentially debian, whose motto is, "If you break it, you get to keep both parts." And it's fun putting it back together, especially with a support group like this forum.
Thanks very much!

---

### Post by Bashing-om on 2013-07-04
drfox; Outstanding..

Also said..."if it ain't broke, you have not tweeked on it enough".
The more I use xfce, the more I like it ....fully configurable, just find that config file !

If you are happy:
Please mark this thread as solved; Aides others seeking a solution, as well as; Helps keep the forum tidy.
Interim method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.

[INDENT][INDENT][INDENT]cheers
[/INDENT][/INDENT][/INDENT]

---

