---
title: "icons wont install?"
date: 2008-05-24
forum: General Help
---

### Post by todd_freeride on 2008-05-24
Hi there, I'm sort of new to linux, been trying to use ubuntu since 6.06 but it would never work with my wireless. Now I'm on 8.04 and loving it to death, since I can now have internet.

But, I have come into s strange little snag, I am trying to install this icon set ( [http://djany.deviantart.com/art/Gnome-Buuf-Deuce-1-0-r8-73339997](http://djany.deviantart.com/art/Gnome-Buuf-Deuce-1-0-r8-73339997) ) so I downloaded it, unzipped the file and got the " Buuf-Deuce-1.0-r8.tar.bz2 " archive out. So here is where I dont know if I'm doing this right, I've been going to System > Preferences > Appearance and then clicking "Install" and navigating to the archive. I had this theme on here once before, but now it just says "copying/'etc etc etc" then it says "Installation for theme "Buuf-Deuce" failed." is there something I'm doing wrong here? 

I would love to use this theme as I'm tired of "human" but I cant get it to work, and help is greatly appreciated. 

thanks much :) ohh, and I'm on Hardy 8.04

---

### Post by alfredovera on 2008-05-24
This is how I did it. Hope it helps.

1) I downloaded the file "Gnome_Buuf_Deuce_1_0_r8_by_djany.zip"
2) I unzipped it => unzip Gnome_Buuf_Deuce_1_0_r8_by_djany.zip
3) Then => bunzip2 Buuf-Deuce-1.0-r8.tar.bz2
4) Then => tar xvf Buuf-Deuce-1.0-r8.tar
5) Then => mv Buuf-Deuce to => /usr/share/icons/
6) Then => chmod 755 Buff-Deuce
7) Then go to => System => Preferences => Appearence => Select any Theme => Click "Customize" => Click "Icons" =>  Select "Buuf-Deuce 1.0-r8"

---

### Post by todd_freeride on 2008-05-24
okay, so I did what I thought was right, I dont understand 

"tar xvf Buuf-Deuce-1.0-r8.tar"
or
Then => chmod 755 Buff-Deuce 

But I did get the folder with all the icons and such, when I tried to move it to the location of usr/share/icons I got this message

[IMG]http://i128.photobucket.com/albums/p193/todd_freeride/willnotallow.png[/IMG]

---

### Post by |{urse on 2008-05-24
all you need to do is drag the .bz2 package you originally downloaded and drop it in the system > preferences > appearances window

if you really wanted to do it the way you are trying to youd need to open a root nautilus window

sudo nautilus /path/you/want

*be real careful, you can screw up your system badly with this method*

---

### Post by savageman on 2008-09-05
I found this snag before and found out how to fix it. In the terminal type in ```
sudo nautilus
``` It will bring up your root folders. Go to usr/share/icons and drag in your icons folder you want (not the tarball but the extracted) Then go to appearances customize, icons and you should see your icon set there choose it an enjoy

EDIT: did not see the guy above me. explained the same thing.

---

