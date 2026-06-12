---
title: "Problems with alacarte (&quot;Main Menu&quot;)"
date: 2014-08-04
forum: General Help
---

### Post by Katzwinkel on 2014-08-04
Hi,
I've been using alacarte (aka "Main Menu") with ubuntu for some time now, because i'm really, really, really not happy with using the Dash in unity. Using alacarte has, up to now, always worked fine with me. However, i recently upgraded to ubuntu 14.04 and now suddenly there are problems with alacarte.
Some submenus, such as "Wine" (which contains starter-links to my office 2007 Programs) just aren't displayed. When i try to configure the menu using alacarte, I can check and uncheck the "display"-box for these submenus as much as i want, nothing changes. 
Did anybody experience similar problems?
Can you give tipps on how to solve this?

---

### Post by hariprasad2 on 2014-09-06
Because still there are some minor problems with customization **Main Menu** using the homonymous utility "**Main Menu**", which is the old known **alacarte** utility, there is simple explanation, how to edit menu partially manually, or repare wrong launchers. First I must say, that all menus has hierarchy structure - tree with branches and leaves. I will concentrate on the leaves, because how is menu build hierarchically I don't know and still I didn't found the documentation, how it is done.

The menu leaves are located in two directories according that, if the items are   globally visible (for all accounts) or if items are visible locally only   for dedicated user. First directory is** /usr/share/applications** directory. There are files with postposition (suffix) .desktop, e.g. **brasero.desktop**, **alacarte.desktop** etc. Second directory is in home of user **~/.local/share/applications**.   There are your own launchers after installations and sometimes, you   want to create yours launcher manually using front-end **Main Menu** editor. If you do it, there appears file   **alacarte-madex.desktop**, where **x** is integer (exactly first occurrence is without number).   Don't hesitate to rename it, nothing wrong happen, I suppose. The inner   content of files will be described further.
 For example after manually installed Eclipse, you want add launcher for it. Start "**Main Menu**" utility from **System Tools -> Preferences**. Add launcher as usually. Icon is in a new installation folder as **icon.xpm**.   When you click on the symbol of icon and select it, the icon of screw   disappears and nothing is visible behind the item. Mostly the item is falling  in  **Other** submenu, but you want to have it for example in **Programming** submenu. There is content of **alacarte-made.desktop**, which I renamed on **eclipse.desktop** after creating launcher:

[Desktop Entry]
Comment=Eclipse Luna
Terminal=false
Name=Eclipse
Exec=/opt/eclipse/eclipse
Type=Application
Icon=/opt/eclipse/icon

This launcher will be in **Other** submenu without proper icon suffix, thich causes unknown icon displayed.

For further work is advisable to close **Main Menu** editor, otherwise it can interfere with your changes to files.
Comparing with another similar items you can see, that proper content will be like this:

[Desktop Entry]
Comment=Eclipse Luna
Terminal=false
Name=Eclipse
Exec=/opt/eclipse/eclipse
Type=Application
Icon=/opt/eclipse/icon[I][B].xpm
Categories=Development;[/B][/I]
[COLOR=#0000cd][B]NoDisplay=false
Hidden=false[/B]
[/COLOR]
Than launcher item will be in proper **Programming** submenu and icon will be dispayed properly.
The last two lines are optional and they are about visibility item in menu. I suppose, that, **NoDisplay** feature supply check box in** Main Menu** editor. Second feature is for purpose when item is removed from **Main Menu** editor. In reality the file is marked **Hidden=true**. If another of this two flags is true, the item is not visible.
 Sometimes is needed to wait some time for changing menu or to do logout-login. It is possible to create the **.desktop** file completely manually. It works too.

Related topics: Desktop (**~/Desktop**), Launchpad.

Tags: Gnome, Compiz, Alacarte, edit Main Menu

---

### Post by hariprasad2 on 2014-09-06
I had the same problems with check, uncheck items in Ubuntu 13.10, but not in 14.04. I posted my own experiences in separate reply, where is written, what I can do manually. I hope, that it will be useful for you. If not, there can be mismatch in **~/.local/share/applications**, or collisions between the two parts of menu (explained above). Try to clean up here. Be careful and backup your launcher items first. Sometimes it is helpful to reinstall **alacarte**. If nothing from those advices helped, than think about deeper damaged **Main Menu**. Sometimes it can be caused during too much upgrades without clear installation, too much wild administration or any damaged files on storing medium.

---

### Post by Katzwinkel on 2014-09-27
Thanks for the help, expecially hariprasad2 for the very detailed instructions. 
Took me awhile to get back to this thread, due to some other issues, but the Info ist greatly appreciated!

---

