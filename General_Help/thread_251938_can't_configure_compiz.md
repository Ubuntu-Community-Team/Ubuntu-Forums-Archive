---
title: "can't configure compiz"
date: 2006-09-06
forum: General Help
---

### Post by Sewage on 2006-09-06
i installed and configured everything using this thread: [http://gandalfn.wordpress.com/howto-compiz-aiglx-on-dapper/](http://gandalfn.wordpress.com/howto-compiz-aiglx-on-dapper/)

it all works, I see shadows and effects, also the little red cube in the notification bar:

[IMG]http://img.photobucket.com/albums/v78/TowardZero/screenshot2.png[/IMG]

when i click prefernces i get this screen:

[IMG]http://img.photobucket.com/albums/v78/TowardZero/screenshot3.png[/IMG]

None of the choices in the tabs do anything except for the "configuration" tab, when I check the "Enable GL desktop" tab it just basically removes all the borders and turns off the effects, checking the "customizable window manager" does absolutely nothing and clicking the button below it does nothing as well.

All I really want to do is change the pop up wobble effect as it drives me crazy and I want to be able to change my border theme and turn off the opacity. D: I can't understand why none of the choices in the tab fail to work~? Any ideas?

---

### Post by ayoli on 2006-09-06
if you got an up-to-date compiz you should run csm to configure your compiz, press alt+F2 then type in: **csm**

---

### Post by Sewage on 2006-09-06
Thank you~ that took care of wobble effects and etc~ 

buuuut i still want to know if it's possible to change the window theme and opacity of it?

---

### Post by Sewage on 2006-09-06
okay well i installed cgwd and learned how to install themes, only thing is I can;t get them to work at all.

And after a restart no theme will load, my windows are all borderless. D: I've tried quite a few things and am getting pretty sad that I can't find a way to get this to work. >:

[IMG]http://img.photobucket.com/albums/v78/TowardZero/screenshot2-1.png[/IMG]

---

### Post by ayoli on 2006-09-06
you need a .cgwd dir in your home, do you have it ?:
if not:
```
mkdir ~/.cgwd && chmod -R ~/.cgwd 755
```
to select/set a theme hit ALT+F2 and type in:
```
gcompizthemer -i
```

---

### Post by Sewage on 2006-09-06
when i click on one of the themes in the CGWD themer list nothing happens at all, is there a specific way I am supposed to apply it?

---

### Post by Sewage on 2006-09-06
i should also point out that before the themer popped up i got these erros on terminal:

brad@brad-desktop:~$ gcompizthemer -i
Usage: -i /file/to/install

** (gcompizthemer:28730): WARNING **: /usr/lib/cgwd/engines/liboxygen.so: undefined symbol: get_meta_info

** (gcompizthemer:28730): WARNING **: Engine /usr/lib/cgwd/engines/liboxygen.so has no meta info, please update it, using defaults.

---

### Post by Sewage on 2006-09-06
i restarted and it worked for like a minute then i messed it up again. d:

---

