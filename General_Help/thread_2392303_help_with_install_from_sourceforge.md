---
title: "help with install from sourceforge"
date: 2018-05-19
forum: General Help
---

### Post by cmcanulty on 2018-05-19
I am supposed to install scidb version r1485 from code at this web site. I know how to install normally from source but can't figure out how to get the install files from the website I was directed to. The link is below. I hope someone can explain what I am missing on this issue. Thank you,

[https://sourceforge.net/p/scidb/code/1485/#diff-1]("https://sourceforge.net/p/scidb/code/1485/#diff-1")

---

### Post by Perfect Storm on 2018-05-19
You should go here: [https://sourceforge.net/p/scidb/code/HEAD/tree/trunk/](https://sourceforge.net/p/scidb/code/HEAD/tree/trunk/)
and click 'download snapshot'.

---

### Post by cmcanulty on 2018-05-19
Thank you that link worked but no matter how I navigate around I can't see how to get from
[https://sourceforge.net/p/scidb/code](https://sourceforge.net/p/scidb/code)  to /HEAD/tree/trunk and the install file I only ask as I think finding install files on sourceforge seems so unintuitive. Thank you again.

---

### Post by SeijiSensei on 2018-05-19
For me, that link redirected to [https://sourceforge.net/p/scidb/code/HEAD/tree/](https://sourceforge.net/p/scidb/code/HEAD/tree/) where the "Download Snapshot" button appears.

---

### Post by cmcanulty on 2018-05-19
OK I got it installed OK but can't find a way to add an icon to menu or panel. I did locate and whereis commands but no luck
```

cmcanulty@ubuntu1:~$ locate scidb
/home/cmcanulty/.scidb-beta
/home/cmcanulty/scidb-beta-code-1475.tgz
/home/cmcanulty/scidb-code-1475
/home/cmcanulty/.scidb-beta/backup
/home/cmcanulty/.scidb-beta/config
/home/cmcanulty/.scidb-beta/engines
/home/cmcanulty/.scidb-beta/layout
/home/cmcanulty/.scidb-beta/log
/home/cmcanulty/.scidb-beta/photos
/home/cmcanulty/.scidb-beta/textures
/home/cmcanulty/.scidb-beta/themes
/home/cmcanulty/.scidb-beta/config/engines.dat
/home/cmcanulty/.scidb-beta/config/load.tcl
/home/cmcanulty/.scidb-beta/config/options.dat
/home/cmcanulty/.scidb-beta/engines/sjeng-scidb
/home/cmcanulty/.scidb-beta/engines/stockfish-scidb
/home/cmcanulty/.scidb-beta/engines/sjeng-scidb/bug.opn
/home/cmcanulty/.scidb-beta/engines/sjeng-scidb/crazyhouse.bin
/home/cmcanulty/.scidb-beta/engines/sjeng-scidb/losers.opn
/home/cmcanulty/.scidb-beta/engines/sjeng-scidb/suicide.opn
/home/cmcanulty/.scidb-beta/engines/sjeng-scidb/zbook.bin
/home/cmcanulty/.scidb-beta/layout/New Layout.layout
/home/cmcanulty/.scidb-beta/textures/dark
/home/cmcanulty/.scidb-beta/textures/lite
/home/cmcanulty/.scidb-beta/textures/tile
/home/cmcanulty/.scidb-beta/textures/dark/marble
/home/cmcanulty/.scidb-beta/textures/dark/misc
/home/cmcanulty/.scidb-beta/textures/dark/wood
/home/cmcanulty/.scidb-beta/textures/lite/marble
/home/cmcanulty/.scidb-beta/textures/lite/misc
/home/cmcanulty/.scidb-beta/textures/lite/wood
/home/cmcanulty/.scidb-beta/textures/tile/marble
/home/cmcanulty/.scidb-beta/textures/tile/misc
/home/cmcanulty/.scidb-beta/textures/tile/wood
/home/cmcanulty/.scidb-beta/themes/Alpha.dat
/home/cmcanulty/.scidb-beta/themes/Antique.dat
/home/cmcanulty/.scidb-beta/themes/Apollo.dat
/home/cmcanulty/.scidb-beta/themes/Arena.dat
/home/cmcanulty/.scidb-beta/themes/Black&White.dat
/home/cmcanulty/.scidb-beta/themes/Blackjack.dat
/home/cmcanulty/.scidb-beta/themes/Burly.dat
/home/cmcanulty/.scidb-beta/themes/Burnett.dat
/home/cmcanulty/.scidb-beta/themes/Burnt.dat
/home/cmcanulty/.scidb-beta/themes/Country-Style.dat
/home/cmcanulty/.scidb-beta/themes/Creepy.dat
/home/cmcanulty/.scidb-beta/themes/Fantasy.dat
/home/cmcanulty/.scidb-beta/themes/Fritz.dat
/home/cmcanulty/.scidb-beta/themes/Glass.dat
/home/cmcanulty/.scidb-beta/themes/Goldenrod.dat
/home/cmcanulty/.scidb-beta/themes/Gray.dat
/home/cmcanulty/.scidb-beta/themes/Jose.dat
/home/cmcanulty/.scidb-beta/themes/Kitsch.dat
/home/cmcanulty/.scidb-beta/themes/Kunterbunt.dat
/home/cmcanulty/.scidb-beta/themes/Magnetic.dat
/home/cmcanulty/.scidb-beta/themes/MarbleBrown.dat
/home/cmcanulty/.scidb-beta/themes/MarbleRed.dat
/home/cmcanulty/.scidb-beta/themes/Marmorate.dat
/home/cmcanulty/.scidb-beta/themes/MayanMarble.dat
/home/cmcanulty/.scidb-beta/themes/MayanWood.dat
/home/cmcanulty/.scidb-beta/themes/Melamine.dat
/home/cmcanulty/.scidb-beta/themes/Military.dat
/home/cmcanulty/.scidb-beta/themes/ModernCheq.dat
/home/cmcanulty/.scidb-beta/themes/Motif.dat
/home/cmcanulty/.scidb-beta/themes/Navajo.dat
/home/cmcanulty/.scidb-beta/themes/Ocean.dat
/home/cmcanulty/.scidb-beta/themes/Phoenix.dat
/home/cmcanulty/.scidb-beta/themes/Primus.dat
/home/cmcanulty/.scidb-beta/themes/Sand.dat
/home/cmcanulty/.scidb-beta/themes/Scidb.dat
/home/cmcanulty/.scidb-beta/themes/Staidly.dat
/home/cmcanulty/.scidb-beta/themes/Staunton.dat
/home/cmcanulty/.scidb-beta/themes/StoneFloor.dat
/home/cmcanulty/.scidb-beta/themes/VirtualBlue.dat
/home/cmcanulty/.scidb-beta/themes/VirtualBrown.dat
/home/cmcanulty/.scidb-beta/themes/Winboard.dat
/home/cmcanulty/.scidb-beta/themes/Woodgrain.dat
/home/cmcanulty/.scidb-beta/themes/piece
/home/cmcanulty/.scidb-beta/themes/square
/home/cmcanulty/.scidb-beta/themes/ttk
/home/cmcanulty/.scidb-beta/themes/piece/Arena.dat
/home/cmcanulty/.scidb-beta/themes/piece/Burly.dat
/home/cmcanulty/.scidb-beta/themes/piece/Condal.dat
/home/cmcanulty/.scidb-beta/themes/piece/Contrast.dat
/home/cmcanulty/.scidb-beta/themes/piece/Emerald.dat
/home/cmcanulty/.scidb-beta/themes/piece/Fritz.dat
/home/cmcanulty/.scidb-beta/themes/piece/Glass.dat
/home/cmcanulty/.scidb-beta/themes/piece/GoldenCreme.dat
/home/cmcanulty/.scidb-beta/themes/piece/Goldenrod.dat
/home/cmcanulty/.scidb-beta/themes/piece/Gray.dat
/home/cmcanulty/.scidb-beta/themes/piece/Green.dat
/home/cmcanulty/.scidb-beta/themes/piece/Indian.dat
/home/cmcanulty/.scidb-beta/themes/piece/Inlaid.dat
/home/cmcanulty/.scidb-beta/themes/piece/Khaki.dat
/home/cmcanulty/.scidb-beta/themes/piece/Kitsch.dat
/home/cmcanulty/.scidb-beta/themes/piece/Lemon.dat
/home/cmcanulty/.scidb-beta/themes/piece/Lemon2.dat
/home/cmcanulty/.scidb-beta/themes/piece/MayanRed.dat
/home/cmcanulty/.scidb-beta/themes/piece/Military.dat
/home/cmcanulty/.scidb-beta/themes/piece/Not-Black-and-White.dat
/home/cmcanulty/.scidb-beta/themes/piece/OrangeLemon.dat
/home/cmcanulty/.scidb-beta/themes/piece/Sand.dat
/home/cmcanulty/.scidb-beta/themes/piece/Sycomore.dat
/home/cmcanulty/.scidb-beta/themes/piece/Virtual.dat
/home/cmcanulty/.scidb-beta/themes/piece/Winboard.dat
/home/cmcanulty/.scidb-beta/themes/piece/YellowBlue.dat
/home/cmcanulty/.scidb-beta/themes/square/Apollo.dat
/home/cmcanulty/.scidb-beta/themes/square/Arena.dat
/home/cmcanulty/.scidb-beta/themes/square/Black&White.dat
/home/cmcanulty/.scidb-beta/themes/square/BlueMarble.dat
/home/cmcanulty/.scidb-beta/themes/square/BlueSky.dat
/home/cmcanulty/.scidb-beta/themes/square/Brown&Goldenrod.dat
/home/cmcanulty/.scidb-beta/themes/square/Burly.dat
/home/cmcanulty/.scidb-beta/themes/square/Burnt.dat
/home/cmcanulty/.scidb-beta/themes/square/Contrast.dat
/home/cmcanulty/.scidb-beta/themes/square/Country-Style.dat
/home/cmcanulty/.scidb-beta/themes/square/Crater.dat
/home/cmcanulty/.scidb-beta/themes/square/Fritz.dat
/home/cmcanulty/.scidb-beta/themes/square/Glass.dat
/home/cmcanulty/.scidb-beta/themes/square/Gray.dat
/home/cmcanulty/.scidb-beta/themes/square/Marble-Black&Beige.dat
/home/cmcanulty/.scidb-beta/themes/square/Marble-Black&Gray.dat
/home/cmcanulty/.scidb-beta/themes/square/Marble-Black&White.dat
/home/cmcanulty/.scidb-beta/themes/square/Marble-Blue.dat
/home/cmcanulty/.scidb-beta/themes/square/MarbleBrown.dat
/home/cmcanulty/.scidb-beta/themes/square/MarbleRed.dat
/home/cmcanulty/.scidb-beta/themes/square/Melamine.dat
/home/cmcanulty/.scidb-beta/themes/square/Navajo.dat
/home/cmcanulty/.scidb-beta/themes/square/Ocean.dat
/home/cmcanulty/.scidb-beta/themes/square/Primus.dat
/home/cmcanulty/.scidb-beta/themes/square/Sand.dat
/home/cmcanulty/.scidb-beta/themes/square/Scidb.dat
/home/cmcanulty/.scidb-beta/themes/square/Seagreen.dat
/home/cmcanulty/.scidb-beta/themes/square/Staidly.dat
/home/cmcanulty/.scidb-beta/themes/square/Stone.dat
/home/cmcanulty/.scidb-beta/themes/square/StoneFloor.dat
/home/cmcanulty/.scidb-beta/themes/square/Sycomore-Gray.dat
/home/cmcanulty/.scidb-beta/themes/square/Sycomore.dat
/home/cmcanulty/.scidb-beta/themes/square/Vinyl-2.dat
/home/cmcanulty/.scidb-beta/themes/square/Vinyl.dat
/home/cmcanulty/.scidb-beta/themes/square/Winboard.dat
/home/cmcanulty/.scidb-beta/themes/square/WoodBrown.dat
/home/cmcanulty/.scidb-beta/themes/square/WoodGreen.dat
/home/cmcanulty/.scidb-beta/themes/square/Wooden.dat
/home/cmcanulty/.scidb-beta/themes/square/Woodgrain.dat
/home/cmcanulty/.scidb-beta/themes/ttk/clearlooks.tcl
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/Board-Setup-Dialog.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/CQL-Examples.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/CQL-File-Format.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/CQL-Index.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/CQL-Match-List.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/CQL-Percentage-Specifiers.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/CQL-Piece-Designators.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/CQL-Position-List.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/CQL-Range-Specifiers.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/CQL-Relation-List.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/CQL-Square-Designators.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/CQL-Syntax.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/CQL-Tagging-2.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/CQL-Tagging.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/CQL-Technical-Description.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/CQL-Transformations.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/Chess-Variants.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/Clipbase.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/Command-Line-Options.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/Contact-Information.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/Database-Archive.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/Database-Export-Dialog.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/Database-Formats.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/Database-Switcher.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/Development-Roadmap.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/ECO-Code.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/FEN.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/File-Selection-Dialog.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/Game-Browser.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/Game-Flags.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/How-To-Set-Default-Browser.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/NAG-Comments.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/Overview.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/Pattern-Matching.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/Toolbar-Usage.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/Welcome.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/Whats-New.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/Write-Protect-Database.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/images
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/images/clipbase-menu.png
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/images/database-switcher-menu-maintenance.png
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/images/database-switcher-menu.png
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/images/database-switcher.png
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/images/file-selection-box-encoding.png
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/images/file-selection-box-info.html
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/images/file-selection-box-navigation-arrow.png
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/images/file-selection-box-navigation-folder.png
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/images/game-browser-menu.png
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/images/set-start-board-marker.png
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/images/toolbar-usage-dnd-hover.png
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/images/toolbar-usage-expanded.png
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/images/toolbar-usage-float.png
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/images/toolbar-usage-locked.png
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/images/toolbar-usage-menu-alignment.png
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/images/toolbar-usage-menu-expand.png
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/images/toolbar-usage-menu-icon-size.png
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/images/toolbar-usage-menu-orientation.png
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/images/toolbar-usage-menu-toolbar.png
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/images/toolbar-usage-minimized.png
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/images/toolbar-usage-move-float.png
/home/cmcanulty/Documents/Chess/Chess Webs/scidb.sourceforge.net/help/en/images/toolbar-usage-move-locked.png
/usr/local/bin/scidb-beta
/usr/local/bin/tclscidb-beta
/usr/local/bin/tkscidb-beta
/usr/local/bin/update-scidb-photo-files
/usr/local/games/sjeng-scidb
/usr/local/games/stockfish-scidb
/usr/local/share/scidb-beta
/usr/local/share/man/man1/scidb-beta.1.gz
/usr/local/share/scidb-beta/cursor
/usr/local/share/scidb-beta/data
/usr/local/share/scidb-beta/engines
/usr/local/share/scidb-beta/flags
/usr/local/share/scidb-beta/help
/usr/local/share/scidb-beta/hyphen
/usr/local/share/scidb-beta/images
/usr/local/share/scidb-beta/lang
/usr/local/share/scidb-beta/pdf
/usr/local/share/scidb-beta/photos
/usr/local/share/scidb-beta/pieces
/usr/local/share/scidb-beta/scripts
/usr/local/share/scidb-beta/textures
/usr/local/share/scidb-beta/themes
/usr/local/share/scidb-beta/photos/s
/usr/local/share/scidb-beta/photos/s/sjeng
/usr/local/share/scidb-beta/photos/s/stockfish
/usr/share/applications/scidb.desktop
/usr/share/icons/hicolor/128x128/apps/scidb.png
/usr/share/icons/hicolor/128x128/mimetypes/application-x-chess-scidb.png
/usr/share/icons/hicolor/128x128/mimetypes/gnome-mime-application-x-chess-scidb.png
/usr/share/icons/hicolor/16x16/apps/scidb.png
/usr/share/icons/hicolor/16x16/mimetypes/application-x-chess-scidb.png
/usr/share/icons/hicolor/16x16/mimetypes/gnome-mime-application-x-chess-scidb.png
/usr/share/icons/hicolor/22x22/apps/scidb.png
/usr/share/icons/hicolor/22x22/mimetypes/application-x-chess-scidb.png
/usr/share/icons/hicolor/22x22/mimetypes/gnome-mime-application-x-chess-scidb.png
/usr/share/icons/hicolor/32x32/apps/scidb.png
/usr/share/icons/hicolor/32x32/mimetypes/application-x-chess-scidb.png
/usr/share/icons/hicolor/32x32/mimetypes/gnome-mime-application-x-chess-scidb.png
/usr/share/icons/hicolor/48x48/apps/scidb.png
/usr/share/icons/hicolor/48x48/mimetypes/application-x-chess-scidb.png
/usr/share/icons/hicolor/48x48/mimetypes/gnome-mime-application-x-chess-scidb.png
/usr/share/icons/hicolor/64x64/apps/scidb.png
/usr/share/icons/hicolor/64x64/mimetypes/application-x-chess-scidb.png
/usr/share/icons/hicolor/64x64/mimetypes/gnome-mime-application-x-chess-scidb.png
/usr/share/mime/application/x-chess-scidb.xml
/usr/share/mime/packages/x-chess-scidb.xml
cmcanulty@ubuntu1:~$ 
```

```
cmcanulty@ubuntu1:~$ whereis scidb-beta
scidb-beta:
cmcanulty@ubuntu1:~$ 
```

---

### Post by cmcanulty on 2018-05-19
I am going to mark this as solved as I did the install again and now have it in the menu. Thank  you very much

---

