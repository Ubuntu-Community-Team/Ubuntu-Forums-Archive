---
title: "Azureus Update problem"
date: 2005-06-27
forum: General Help
---

### Post by Digitallysick on 2005-06-27
Azureus wont update automaticlly, how do i update it manually??

---

### Post by bored2k on 2005-06-28
[QUOTE=Digitallysick]Azureus wont update automaticlly, how do i update it manually??[/QUOTE]
 Are you using the backport ? If not, you could easily download the package and over write the current directory.

---

### Post by SGC on 2005-06-28
Download the jar file from here:
[http://voxel.dl.sourceforge.net/sourceforge/azureus/Azureus2.3.0.4.jar](http://voxel.dl.sourceforge.net/sourceforge/azureus/Azureus2.3.0.4.jar)
or here:
[http://heanet.dl.sourceforge.net/sourceforge/azureus/Azureus2.3.0.4.jar](http://heanet.dl.sourceforge.net/sourceforge/azureus/Azureus2.3.0.4.jar)

Rename it to: 
Azureus2.jar

And replace the current Azureus2.jar  in /usr/share/java with the new one

EDIT: if you Azureus2.jar is not installed in /usr/share/jave then try to locate where is it installed by running this command from the terminal:
```
locate Azureus2.jar
```

---

### Post by Digitallysick on 2005-06-28
when i do that azureus no longer loads at all!!!

---

### Post by SGC on 2005-07-01
[QUOTE=Digitallysick]when i do that azureus no longer loads at all!!![/QUOTE]
 This is the only for manual upgrades, are you sure you did right?

---

