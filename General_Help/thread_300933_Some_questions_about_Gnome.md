---
title: "Some questions about Gnome"
date: 2006-11-16
forum: General Help
---

### Post by pfusco on 2006-11-16
Good morning, 
I have some questions about Gnome and the way Ubuntu assigns permissions to do things, or rather what Ubuntu "allows" me to do with my system.

When I first installed it over my Suse OS I got a nice handy little Education folder in the applications startup menu, just to keep my kids apps in one place, reinstalled it because I made some errors while playing around (and yes, I like to play with my OS, allows me to learn it alot better) and now I cant that menu option back. Matter of Fact, I installed quite a few programs that I know have insetion into the start menus built into their install process, that will not show up anyplace. Also using Automatix I tried t oinstall the Debian Menu system so I could see and access these items, but that didnt work either. 

Second issue is the tools that Ubuntu allows me access to as far as Disk Management. Which, from I can see so far as being none to speak of. Oh sure it will let me see, the drives I have and let me access them but it wont tell me the Disk space available, wont let me even see the gpart application that I have access to on the live cd. 

I really like what Ive seen so far in Ubuntu but this is something that is very frustrating.

---

### Post by mayonaise15 on 2006-11-16
I think what you are looking for is under System>Preferences>Menu Layout.  That will let you customize what shows up in your menus and what doesn't.

Also...

Ubuntu doesn't install gparted by default.  The reason it is installed on the livecd is because they figure it will be useful to people who need to repartition their drive in order to install Ubuntu.  If you want to install it just type this into your terminal:

```
sudo apt-get install gparted
```

Have fun

---

