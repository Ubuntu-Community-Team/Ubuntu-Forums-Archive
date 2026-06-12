---
title: "Freemind don't initiate :("
date: 2007-03-22
forum: General Help
---

### Post by CAFH on 2007-03-22
Hi,

I have got a problem when trying to initiate Freemind. I have installed Freemind on my laptop with Dapper about 2 months.

Using the console ive got the following output:
```

/home/hcastro/.freemind/user.properties

User properties found.
Default (System) Look & Feel: com.sun.java.swing.plaf.gtk.GTKLookAndFeel
/home/hcastro/.themes/LiNsta3/gtk-2.0/gtkrc:53: Failed to parse property value " GTK_SHADOW_NONE " for `GtkStatusbar::shadow-type'
/home/hcastro/.themes/LiNsta3/gtk-2.0/gtkrc:54: Failed to parse property value " GTK_SHADOW_NONE " for `GtkSpinButton::shadow-type'
[Freemind-Developer-Internal-Warning (do not write a bug report, please)]: Tried to get view without being able to get map module.
22/Mar/2007 10:47:30 freemind.modes.ModesCreator getAllModes
INFO: Modes:[freemind.modes.browsemode.BrowseMode, freemind.modes.filemode.FileMode, freemind.modes.mindmapmode.MindMapMode]
22/Mar/2007 10:47:30 freemind.modes.ModesCreator getMode
INFO: Initializing mode MindMap
22/Mar/2007 10:47:30 freemind.modes.mindmapmode.MindMapController <init>
INFO: createIconActions
22/Mar/2007 10:47:30 freemind.modes.mindmapmode.MindMapController <init>
INFO: createNodeHookActions
22/Mar/2007 10:47:31 freemind.modes.mindmapmode.MindMapController <init>
INFO: mindmap_menus
22/Mar/2007 10:47:31 freemind.modes.mindmapmode.MindMapController <init>
INFO: MindMapPopupMenu
22/Mar/2007 10:47:31 freemind.modes.mindmapmode.MindMapController <init>
INFO: MindMapToolBar
22/Mar/2007 10:47:31 freemind.modes.mindmapmode.MindMapController <init>
INFO: setAllActions
22/Mar/2007 10:47:31 freemind.modes.ModesCreator getMode
INFO: Done: Initializing mode MindMap
```

... any ideas?

Thanks for helping!

---

### Post by CAFH on 2007-03-22
I have found the problem.

The theme "LiNsta3" was somehow interfering with the initialize of the program.

Once again thanks

---

### Post by gritsul on 2007-04-21
May be it will help you:

[https://help.ubuntu.com/community/Freemind](https://help.ubuntu.com/community/Freemind)

---

