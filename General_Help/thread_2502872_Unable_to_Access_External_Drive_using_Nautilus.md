---
title: "Unable to Access External Drive using Nautilus"
date: 2024-12-03
forum: General Help
---

### Post by Brian_Daniels on 2024-12-03
[COLOR=#0E101A][COLOR=#0E101A]Hello,

[/COLOR]
[/COLOR]
[COLOR=#0E101A][COLOR=#0E101A]Whenever I try to access files on an external hard drive using Nautilus, I get this error message (see attached image):
[/COLOR]
[/COLOR]
[COLOR=#0E101A]**[COLOR=#0E101A]Unable to access "1000 GB Encrypted"[/COLOR]**[/COLOR]
[COLOR=#0E101A][COLOR=#0E101A]No .Filesystem or .Encrypted interface on D-Bus object
[/COLOR]
[/COLOR]
[COLOR=#0E101A][COLOR=#0E101A]As far as the drive is concerned, it is formatted APFS. I currently use it as a Time Machine backup drive containing other important files. I've heard using a Time Machine drive to store files isn't good, but it has not caused me any issues working with them in my MacOS partition. I desire to access these files using my  Ubuntu partition. As stated, I get the above error message when trying to use Nautilus (as the drive shows up in the left-hand selection menu) to access the drive. The OS is reading the drive, but I cannot access its contents. It is also an Encrypted drive, but I know the password to access the folders.
[/COLOR]
[/COLOR]
[COLOR=#0E101A][COLOR=#0E101A]I even went into purchasing this software: [https://www.paragon-software.com/home/apfs-linux/#how_it_works](https://www.paragon-software.com/home/apfs-linux/#how_it_works) and still was unsuccessful. After running the installation, I could not produce anything significant using the terminal and the user manual. I feel like I installed it correctly, but no luck when I attempted to use it in the terminal. Can anyone with experience using this software guide me through it? It could be my mistake, and I did it wrong last time. I may already have what I need to access the files, but I don't know how to use the tool I purchased.
[/COLOR]
[/COLOR]
[COLOR=#0E101A][COLOR=#0E101A]For now, I can restart the computer and access the files on the drive with no problem from MacOS,  but I want to try to be able to access them through Ubuntu so I don't have to restart the computer every time I want to access the files on the external drive.
[/COLOR]
[/COLOR]
[COLOR=#0E101A][COLOR=#0E101A]Thank you so much for your attention and participation. [/COLOR][/COLOR]:o:KS
[COLOR=#0E101A][COLOR=#0E101A] 

[/COLOR]
[/COLOR]
[COLOR=#0E101A][COLOR=#0E101A]Brian J Daniels[/COLOR]
[/COLOR]

---

### Post by dragonfly41 on 2024-12-04
I have zero knowledge of APFS (although I have an old Mac box in my goodies collected over the years).

I found this which might be relevant.

[https://superuser.com/questions/1267291/how-to-mount-apfs-on-linux-or-windows](https://superuser.com/questions/1267291/how-to-mount-apfs-on-linux-or-windows)

Also a thought is to try Thunar and editors such as Krusader (dual window) for mounting via GUI. I am a long term user of Krusader. Hit Home button at top of panel and at bottom of list is Removeable Devices. You can also write your custom UserActions. Scripts.

---

### Post by yancek on 2024-12-04
>  [COLOR=#0E101A][COLOR=#0E101A]For now, I can restart the computer and access the files on the drive with no problem from MacOS[/COLOR][/COLOR]

Why would you not be able to access your Apple filesystem from your Apple computer.  Apple is extremely proprietary and you will likely need to do a lot of research to get an encrypted drive with a foreign (APFS) filesystem to work on any Linux.  The link below discusses the situation and indicates what additional software you will likely need to install to get this to work.

 [https://www.baeldung.com/linux/apfs-partition-mount](https://www.baeldung.com/linux/apfs-partition-mount)

With regard to Paragon, have you read through the FAQ on the site you linked to or downloaded their user Manual?  I expect you would get better information from those sources than from this Ubuntu Linux forum.  If you paid them, they should have support.

Your problem isn't accessing an external drive, it is related to using a drive with a proprietary filesystem that is also encrypted.

---

