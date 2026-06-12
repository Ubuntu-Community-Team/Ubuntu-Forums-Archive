---
title: "I need an untouched copy of a file I messed up:"
date: 2005-04-03
forum: General Help
---

### Post by Jujimufu on 2005-04-03
I was trying to install the ubuntu icon in the menu panel:  [http://www.gnome-look.org/content/show.php?content=22413](http://www.gnome-look.org/content/show.php?content=22413)

I followed the guy's directions who left comments on this download and it didn't work; editing the file:

**/etc/gconf/gconf.xml.defaults/apps/panel/default_setup/objects/menu_bar/%gconf.xml**

Well I didn't damage anything, but it didn't work. I should have backed it up: But I didn't.  If anybody who has gotten this to work could help me that be great - but otherwise if anybody could copy and paste the contents of that file so I can change it back to default and try something else that be good too.

Thanks guys.

---

### Post by Gandalf on 2005-04-03
[QUOTE=Jujimufu]I was trying to install the ubuntu icon in the menu panel:  [http://www.gnome-look.org/content/show.php?content=22413](http://www.gnome-look.org/content/show.php?content=22413)

I followed the guy's directions who left comments on this download and it didn't work; editing the file:

**/etc/gconf/gconf.xml.defaults/apps/panel/default_setup/objects/menu_bar/%gconf.xml**

Well I didn't damage anything, but it didn't work. I should have backed it up: But I didn't.  If anybody who has gotten this to work could help me that be great - but otherwise if anybody could copy and paste the contents of that file so I can change it back to default and try something else that be good too.

Thanks guys.[/QUOTE]
 here's mine
```

<?xml version="1.0"?>
<gconf>
        <entry name="action_type" mtime="1112408997" schema="/schemas/apps/panel/objects/action_type"/>
        <entry name="launcher_location" mtime="1112408997" schema="/schemas/apps/panel/objects/launcher_location"/>
        <entry name="menu_path" mtime="1112408997" schema="/schemas/apps/panel/objects/menu_path"/>
        <entry name="use_menu_path" mtime="1112408997" schema="/schemas/apps/panel/objects/use_menu_path"/>
        <entry name="custom_icon" mtime="1112408997" schema="/schemas/apps/panel/objects/custom_icon"/>
        <entry name="use_custom_icon" mtime="1112408997" schema="/schemas/apps/panel/objects/use_custom_icon"/>
        <entry name="tooltip" mtime="1112408997" schema="/schemas/apps/panel/objects/tooltip"/>
        <entry name="attached_toplevel_id" mtime="1112408997" schema="/schemas/apps/panel/objects/attached_toplevel_id"/>
        <entry name="bonobo_iid" mtime="1112408997" schema="/schemas/apps/panel/objects/bonobo_iid"/>
        <entry name="locked" mtime="1112408997" schema="/schemas/apps/panel/objects/locked" type="bool" value="true">
        </entry>
        <entry name="panel_right_stick" mtime="1112408997" schema="/schemas/apps/panel/objects/panel_right_stick" type="bool" value="false">
        </entry>
        <entry name="position" mtime="1112408997" schema="/schemas/apps/panel/objects/position" type="int" value="0">
        </entry>
        <entry name="toplevel_id" mtime="1112408997" schema="/schemas/apps/panel/objects/toplevel_id" type="string">
                <stringvalue>top_panel</stringvalue>
        </entry>
        <entry name="object_type" mtime="1112408997" schema="/schemas/apps/panel/objects/object_type" type="string">
                <stringvalue>menu-bar</stringvalue>
        </entry>
</gconf>

```

---

### Post by Jujimufu on 2005-04-03
Thanks man! : )

---

### Post by Gandalf on 2005-04-03
[QUOTE=Jujimufu]Thanks man! : )[/QUOTE]
 no problem

---

