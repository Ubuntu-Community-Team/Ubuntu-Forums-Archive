---
title: "trouble installing anjuta"
date: 2004-11-13
forum: General Help
---

### Post by danfong on 2004-11-13
I'm getting these errors after trying to ./configure anjuta 1.2.2

configure: error: Library requirements (
glib-2.0 >= 2.0.6
gtk+-2.0 >= 2.0.8
ORBit-2.0 >= 2.4.0      
libglade-2.0 >= 2.0.0
libgnome-2.0 >= 2.0.2
libgnomeui-2.0 >= 2.0.2
libgnomeprint-2.2 >= 2.0.1      
libgnomeprintui-2.2 >= 2.0.1
gnome-vfs-2.0 >= 2.0.2
gnome-vfs-module-2.0 >= 2.0.2
libbonobo-2.0 >= 2.0.0   
libbonoboui-2.0 >= 2.0.1
vte >= 0.7.0
libxml-2.0 >= 2.4.23
pango >= 1.1.1
) not met; 
consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix 
so pkg-config can find them.


How do I find out what versions of these items are installed? How do I update if the above is true? Should I consider adjusting the PKG_CONFIG_PATH? How and to what?

I'm stumped. Someone please have mercy on me.

thanks, dan

---

### Post by randy on 2004-11-13
You can install Anjuta from a package.  All you'll have to do is add the Universe Repository to your sources.list.

---

### Post by danfong on 2004-11-13
[QUOTE=randy]You can install Anjuta from a package.  All you'll have to do is add the Universe Repository to your sources.list.[/QUOTE]
 Thanks Randy. Now, indulge me further... How do I add the Universe Repository to my sources.list.

thanks, dan

---

### Post by FLeiXiuS on 2004-11-13
[QUOTE=danfong]Thanks Randy. Now, indulge me further... How do I add the Universe Repository to my sources.list.

thanks, dan[/QUOTE]



Check the HOWTO section of this forum, its a sticky.


Sorry for not posting the link, im trying to encourage users to search the forum before asking.

---

