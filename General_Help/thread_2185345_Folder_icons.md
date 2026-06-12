---
title: "Folder icons"
date: 2013-11-02
forum: General Help
---

### Post by belnac on 2013-11-02
Yesterday I tried to set a custom icon for a folder and the only way I could think of to do this was to use nautilus. Now, there's a problem with this method in that the icons don't scale well at different zoom levels. So if, for instance, one selects [FONT=Courier New]/usr/share/icons/elementary-xfce/places/128/folder-documents.png[/FONT] as the icon for the home documents folder, it will look fuzzy at lower zoom levels and sharp only when the view is zoomed in. I know for a fact that, for every other default folder icon, the scaling does take place automatically with the right icon (24, 32, 48, etc) being picked depending on the zoom level.

[LIST=1]
[*]How can I set the icon of a folder such that it scales automatically depending on the zoom level? I'd rather learn how to do it manually using a text editor and/or the CLI.
[*]Where are both the default and user customised settings stored?
[*]Incidentally, how can I find out which of the icon-sets in [font=Courier New]/usr/share/icons[/font] is in use by the system?
[/LIST]

---

### Post by bug67 on 2013-11-02
> **belnac said:**
> 
1.  How can I set the icon of a folder such that it scales automatically depending on the zoom level? I'd rather learn how to do it manually using a text editor and/or the CLI.

I could be wrong but, I believe that the scalable icons are in an .svg format (scalable vector graphic) rather than a png.

[quote=]2.  Where are both the default and user customised settings stored?[/QUOTE]

Default, I believe are in usr/share/icons.  User customized should be in a hidden folder (revealed by pressing ctrl h) in your home folder.  The folder would be labeled ".icons" upon reveal.

[quote=]3.  Incidentally, how can I find out which of the icon-sets in [font=Courier New]/usr/share/icons[/font] is in use by the system?
[/QUOTE]

Should be as easy as looking in the system setting for which ever icon set is selected.  I don't have *buntu in front of me right now so I can't give exact answers.  I can't remember off top what Xubuntu uses for the default icon theme but, a quick look in system settings for the icon theme would tell you which one you have selected.

---

