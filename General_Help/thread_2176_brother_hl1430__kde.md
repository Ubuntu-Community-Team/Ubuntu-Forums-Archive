---
title: "brother hl1430 / kde"
date: 2004-10-26
forum: General Help
---

### Post by drunken-wallaby on 2004-10-26
hi there. after some weeks with ubuntu i'm currently thinking to switch back to fedora for several reasons. i really like ubuntu and would like to stay with this great distro, however if i can't solve my little problems i have to change distros again. anyway, perhaps somebody is here that may help me.

the first annoying thing is my printer. i own a brother hl 1430 laser printer. installing went fine, everything seemed perfect and i am able to print from most applications including open office. i can't print print anything directly from the print menu of firefox though. i just can print to a file (postscript) which is very annoying for me since i am used to print a lot of things directly from the browser. if i print the content of a webpage to a file and view it with ggv, i can't print at all and an error message is displayed as soon as i want to call the print menu. 

furthermore, i can't print more than one side on a piece of paper. i found an option in  the printer menu of gpdf but if i choose to print more than 2 pages on one paper nothing is printed, only white paper is returned. in open office, i wasn't able to find the option to print more than one page on a piece of paper. this is really annoying and i would be quite happy if someone has an idea how to solve this issue.

the other main problem i have to deal with is the following. i have to work quite a lot with (la)tex and since i am used to work with kile instead of emacs or vim i did a simple ```
sudo apt-get install kile
```, which installed kile. calling kile from the command line i get a lot of > kdecore (KIconLoader): WARNING: Icon directory /usr/share/icons/xxx/... not valid. errors. i know that i can solve this errors by locationg to the proper directories and using the following code fragment. ```
sudo cp index.theme index.desktop
```. however, since fonts in kile look ugly i installed kcontrol to fix the font-problem. i did ```
sudo apt-get install kcontrol
``` and it was installed fine. calling the control center works, however the index on the left side is empty as you can see in the attached file. therefore i can't change anything, neither the fonts nor anything else. anyone who knows how to solve this problem? 

thanks a lot for your support.

---

### Post by drunken-wallaby on 2004-10-27
sorry for bumping this topic, but does really nobody has any idea how to solve these issues?

---

### Post by drunken-wallaby on 2004-10-27
i just managed to solve the kde problem. i just had to manually remove the kdecache folder via ```
sudo rm /var/tmp/kdecache-user/ -Rf
```

if the printer issue can be solved as well i'd be very very happy with ubuntu :)

---

### Post by drunken-wallaby on 2004-10-28
i just managed to partially solve the printing problem. when i want to print a document within open-office, i have to preview the page. then i can choose how many pages should be displayed on one page and from there i can print 2 on 1 or 4 on 1 without any problems.

however, i want to be able to print 2/1 or 4/1 from pdf documents as well. unfortunately, neither xpdf nor gpdf seem to support this feature. anyone who has a hint for me? thanks a lot :)

---

