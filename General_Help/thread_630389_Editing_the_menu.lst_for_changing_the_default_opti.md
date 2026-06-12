---
title: "Editing the menu.lst for changing the default option"
date: 2007-12-03
forum: General Help
---

### Post by thirunavukkarasu on 2007-12-03
Hi guys,

I need to modify the default boot option in my menu.lst file thorugh shell script. I need script solution so that it can be done automatically.

Before excuting the script:
**default       0**

After excuting the script it should look like:
**default       1**


Plz...... help:)

Thanks in advance.

Rgds,
Thiru.S

---

### Post by jseiser on 2007-12-03
the way i go about this is 
sudo nano /boot/grub/menu.lst

---

### Post by chippy99 on 2007-12-03
Try this 

 sed -i 's/default\t\t0/default\t\t1/' /boot/grub/menu.lst 

This assumes that you have 2 tabs between default an 0 in your menu.lst. That is what I have in mine. Make sure you backup the file before executing this command in case something goes wrong.

---

### Post by teryowen on 2007-12-03
you can write a perl script:

heres the code

```

#!/usr/bin/perl

open (IN, "+</boot/grub/menu.lst");

@file = <IN>; 

seek IN,0,0; 

foreach $file (@file){
$file =~ s/default 0/default 1/g;
print IN $file;
}
close IN;


```

NOTE back up the menu file first and then execute under sudo.

Also to get this working just copy this into a file and save it and chmod it 700 to make it executable.

---

### Post by thirunavukkarasu on 2007-12-05
Thanks chippy99,  it worked and i can change the default option with this command

Hi teryowen, i will update you after i checked the script.

I am :) happy to see the replies.......

Thank you

---

