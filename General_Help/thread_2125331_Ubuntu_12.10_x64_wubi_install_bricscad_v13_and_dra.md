---
title: "Ubuntu 12.10 x64 wubi install bricscad v13 and draftsight install"
date: 2013-03-13
forum: General Help
---

### Post by mjharold on 2013-03-13
[COLOR=#000000][COLOR=#000000][FONT=Courier New][SIZE=2]I am a linux novice but enjoy ubuntu and all it offers and the community. Prior till end of last year I had bricscad v11 and 12 running on ubuntu 11.04. That laptop motherboard died. I got anew laptop. I installed ubuntu 12.10 x64 aside the windows 7via ubuntu website wubi. All software I needed ran well except could not get an install of bricscad to install, died during install with default ubuntu software center. Weeks went by. Finally got it. I also got Draftsight to install and run also.[/SIZE][/FONT][/COLOR][/COLOR]


[COLOR=#000000][COLOR=#000000][FONT=Courier New][SIZE=2]Bricscad-v13.1.19on Ubuntu 12.10 x64 wubi install:[/SIZE][/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Courier New][SIZE=2]
sudo dpkg--add-architecturei386[/SIZE][/FONT][/COLOR][/COLOR]


[COLOR=#000000][COLOR=#000000][FONT=Courier New][SIZE=2]sudo apt-get update[/SIZE][/FONT][/COLOR][/COLOR]


[COLOR=#000000][COLOR=#000000][FONT=Courier New][SIZE=2]This installs the ia32-libs and ia32-libs-multiarch needed. As I read, the wubi install of ubuntu 12.10 does not include the i386 and does not allow the single packages, you have to have all to get all dependencies as I understand.[/SIZE][/FONT][/COLOR][/COLOR]


[COLOR=#000000][COLOR=#000000][FONT=Courier New][SIZE=2]I then installed gdebi installer rather than the default ubuntu software center package installer.[/SIZE][/FONT][/COLOR][/COLOR]


[COLOR=#000000][COLOR=#000000][FONT=Courier New][SIZE=2]after that I right mouse clicked over the downloaded BricsCAD-V13.1.19-2-en_US-amd64.deb file and selected install with gdebi installer.[/SIZE][/FONT][/COLOR][/COLOR]


[COLOR=#000000][COLOR=#000000][FONT=Courier New][SIZE=2]It installed complete with no dependency errors or any comments. Found the icon and added to sidebar. launched and it came up with no errors and did not die during exercising bricscad. I seem to have true type fonts also. [/SIZE][/FONT][/COLOR][/COLOR]


[COLOR=#000000][COLOR=#000000][FONT=Courier New][SIZE=2]Draftsight Install next:[/SIZE][/FONT][/COLOR][/COLOR]


[COLOR=#000000][COLOR=#000000][FONT=Courier New][SIZE=2]After above I did the following:[/SIZE][/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Courier New][SIZE=2]download 32 bit .deb file to install from [/SIZE][/FONT][/COLOR][/COLOR][http://www.3ds.com/products/draftsig...ad-draftsight/]("http://www.3ds.com/products/draftsight/download-draftsight/")
[COLOR=#000000][COLOR=#000000][FONT=Courier New][SIZE=2]after install launch terminal and provide root or su (superuser) password[/SIZE][/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Courier New][SIZE=2]then type or paste following and enter after each to execute.[/SIZE][/FONT][/COLOR][/COLOR]

[COLOR=#000000][COLOR=#000000][FONT=Courier New][SIZE=2]sudo apt-get install ia32-libs libdirectfb-extra libxcb-render-util0
[/SIZE][/FONT][/COLOR][/COLOR][COLOR=#000000][COLOR=#000000][FONT=Courier New][SIZE=2]sudo dpkg --force-all -i ~/Downloads/draftSight.deb
[/SIZE][/FONT][/COLOR][/COLOR][COLOR=#000000][COLOR=#000000][FONT=Courier New][SIZE=2]sudo apt-get -f
installed, f[/SIZE][/FONT][/COLOR][/COLOR][COLOR=#000000][COLOR=#000000][FONT=Courier New][SIZE=2]ound icon, added icon to sidebar, launched....it worked. This version is pre-release of commercial and may not be free later (read the license) but cool to play with until they charge. [/SIZE][/FONT][/COLOR][/COLOR]
[COLOR=#000000][COLOR=#000000][FONT=Courier New][SIZE=2]Good luck[/SIZE][/FONT][/COLOR][/COLOR]

---

