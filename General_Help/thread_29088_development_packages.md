---
title: "development packages?"
date: 2005-04-22
forum: General Help
---

### Post by mtz on 2005-04-22
Hi, 
i sm thinking of migrating to Kubuntu but before i do that, i need to know if it comes with development packages. I have looked everywhere on this website for that info to no avail. 

thanks

salaam kwa uwapendao ..

---

### Post by ubuntu_demon on 2005-04-23
[QUOTE=mtz]Hi, 
i sm thinking of migrating to Kubuntu but before i do that, i need to know if it comes with development packages. I have looked everywhere on this website for that info to no avail. 

thanks

salaam kwa uwapendao ..[/QUOTE]
 to be able to compile/build packages you need to install the package "build-essential" Most newbies don't need this that's why it's not installed by default.

All important development software that's available for debian is also available for ubuntu as far as I know. There are also kde specific programs like kdevelop.

Please be a bit more specific what kind of development software you need. 

[www.ubuntuguide.org](www.ubuntuguide.org) is a good start if you are new to ubuntu

---

### Post by mtz on 2005-04-23
[QUOTE=demon666_nl]to be able to compile/build packages you need to install the package "build-essential" Most newbies don't need this that's why it's not installed by default.

All important development software that's available for debian is also available for ubuntu as far as I know. There are also kde specific programs like kdevelop.

Please be a bit more specific what kind of development software you need. 

[www.ubuntuguide.org](www.ubuntuguide.org) is a good start if you are new to ubuntu[/QUOTE]

By development packages, i mean gcc, g++, make, automake, xine-dev, gimp-dev, imlib-dev, tcl/tk-dev. n more..the more the better, I hate being unable to compile a program cause i miss one or more packages or development packages..this is the main reason why i want to change my current distro. I have been using linux for more than 2 years now so i dont think i fit into the  newbie category...default, one cd installation isnt enought. And i have a dial up connection at home so trying to download each and every missing package is something i am not willing to do. If kubuntu doesnt come with additional cds, i dont think its right for me.

Are these "buil-essentials" in a cd? or in a place where i can download all of them at once?  ...i am interested in kubuntu, not ubuntu ..

---

### Post by ubuntu_demon on 2005-04-23
[QUOTE=mtz]By development packages, i mean gcc, g++, make, automake, xine-dev, gimp-dev, imlib-dev, tcl/tk-dev. n more..the more the better, I hate being unable to compile a program cause i miss one or more packages or development packages..this is the main reason why i want to change my current distro. I have been using linux for more than 2 years now so i dont think i fit into the  newbie category...default, one cd installation isnt enought. And i have a dial up connection at home so trying to download each and every missing package is something i am not willing to do. If kubuntu doesnt come with additional cds, i dont think its right for me.

Are these "buil-essentials" in a cd? or in a place where i can download all of them at once?  ...i am interested in kubuntu, not ubuntu ..[/QUOTE]
 ubuntu and kubuntu use the same repositories.

build-essential is just a meta-package that always depends on the packages that are needed to build debianpackages ... currently it depends on :
Depends: libc6-dev | libc-dev, gcc (>= 3:3.3), g++ (>= 3:3.3), make, dpkg-dev (> = 1.4.1.19)

You can create your own cd of packages. You might be interested in these threads :

[http://www.ubuntuforums.org/showthread.php?t=23843](http://www.ubuntuforums.org/showthread.php?t=23843)

[http://www.ubuntuforums.org/showthread.php?t=22620](http://www.ubuntuforums.org/showthread.php?t=22620)

---

