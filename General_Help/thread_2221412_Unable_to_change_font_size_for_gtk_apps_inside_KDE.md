---
title: "Unable to change font size for gtk apps inside KDE"
date: 2014-05-02
forum: General Help
---

### Post by silv3rm00n on 2014-05-02
[COLOR=#333333][FONT=UbuntuRegular]I am using Kubuntu, and trying to configure the fonts for gtk apps from systemsettings > Common Appearance and Behavior > Application Appearance > GTK[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Changing the themes and font family works fine. But the font size is not working. It sticks to 10pt, no matter what font size is selected.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]
Here is a screenshot
[/FONT][/COLOR]http://postimg.org/image/rgdvq86fj/full/[COLOR=#333333][FONT=UbuntuRegular]

[/FONT][/COLOR][IMG]http://i58.tinypic.com/9ury9v.png[/IMG][COLOR=#333333][FONT=UbuntuRegular]

[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]My KDE font is Droid Sans 9pt, and I have set the same for GTK apps. But gedit is using Droid Sans 10pt, and so are all gtk apps like pidgin. If I change the font, it will use it but at the fixed 10pt size, irrespective of whatever size is specified.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]
So how do I fix this issue ? I verified that the issue is present on a fresh install of Kubuntu.

Here is some more information
[/FONT][/COLOR]
```

$ env | grep gtk
GTK2_RC_FILES=/etc/gtk-2.0/gtkrc:/home/enlightened/.gtkrc-2.0:/home/enlightened/.kde/share/config/gtkrc-2.0
GTK_RC_FILES=/etc/gtk/gtkrc:/home/enlightened/.gtkrc:/home/enlightened/.kde/share/config/gtkrc
GTK_MODULES=overlay-scrollbar:unity-gtk-module

```

Contents of ~/.gtkrc-2.0
                                                                                 
```

$ cat .gtkrc-2.0
# File created by KDE Gtk Config
# Configs for GTK2 programs 


include "/usr/share/themes/oxygen-gtk/gtk-2.0/gtkrc"
style "user-font" 
{
        font_name="Droid Sans [unknown] Regular"
}
widget_class "*" style "user-font"
gtk-font-name="Droid Sans [unknown] Regular 9"
gtk-theme-name="oxygen-gtk"
gtk-icon-theme-name="oxygen"
gtk-fallback-icon-theme="oxygen"
gtk-toolbar-style=GTK_TOOLBAR_ICONS
gtk-menu-images=0                                                                                                                                     
gtk-button-images=0                    


```


Contents of ~/.gtkrc-2.0-kde4                                                                                                        

```

$ cat .gtkrc-2.0-kde4                                                                                                        
# File created by KDE Gtk Config                                                                                                                      
# Configs for GTK2 programs                                                                                                                           
                                                                                                                                                      
include "/usr/share/themes/oxygen-gtk/gtk-2.0/gtkrc"                                                                                                  
style "user-font"                                                                                                                                     
{
        font_name="Droid Sans [unknown] Regular"
}
widget_class "*" style "user-font"
gtk-font-name="Droid Sans [unknown] Regular 9"
gtk-theme-name="oxygen-gtk"
gtk-icon-theme-name="oxygen"
gtk-fallback-icon-theme="oxygen"
gtk-toolbar-style=GTK_TOOLBAR_ICONS
gtk-menu-images=0
gtk-button-images=0

```

---

### Post by SeijiSensei on 2014-05-02
I gave this a try on my Kubuntu 14.04 and encountered the same problem.  I changed the font and size in the dialog box but saw no difference in either Firefox or Thunderbird, the only GTK apps I run routinely.

---

