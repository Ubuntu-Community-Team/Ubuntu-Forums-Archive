---
title: "some files missing from libplasma-dev package"
date: 2008-06-06
forum: General Help
---

### Post by adsly on 2008-06-06
hi all,

i am trying to compile a plasmoid from the kde-look website. after getting lots of errors and searching the web for a solution, i finally came up with this error...

```

[ 20%] Building CXX object CMakeFiles/plasma_applet_pretty_tasks.dir/plasma_applet_pretty_tasks_automoc.o                                   
In file included from /home/user/Downloads/prettytasks/prettytasks.h:7,                                                                     
                 from /home/user/Downloads/prettytasks/prettyicon.h:4,                                                                      
                 from /home/user/Downloads/prettytasks/moc_prettyicon.cpp:10,                                                               
                 from /home/user/Downloads/prettytasks/plasma_applet_pretty_tasks_automoc.cpp:2:                                            
/home/user/Downloads/prettytasks/prettylayout.h:10:39: error: plasma/layouts/layoutitem.h: No such file or directory                        
/home/user/Downloads/prettytasks/prettylayout.h:11:35: error: plasma/layouts/layout.h: No such file or directory                            
/home/user/Downloads/prettytasks/prettylayout.h:12:43: error: plasma/layouts/layoutanimator.h: No such file or directory                    

```

it says that i have some files missing. after googling yet again i found this list of files (at [http://packages.ubuntu.com/hardy/all/libplasma-dev/filelist](http://packages.ubuntu.com/hardy/all/libplasma-dev/filelist)) that were supposedly installed upon installing libplasma-dev. after comparing it with what was installed on my computer, i discovered that a few whole directories were missing namely the /usr/lib/kde4/include/plasma/ and /usr/lib/kde4/include/widget/. i tried reinstalling libplasma-dev but to no avail.

is there any way to resolve this problem?

---

