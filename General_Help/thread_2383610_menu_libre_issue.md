---
title: "menu libre issue"
date: 2018-01-27
forum: General Help
---

### Post by cmcanulty on 2018-01-27
I have been trying for hours to add an item to menu libre and no luck. I successfully added it to desktop but the command I use for that won't work in menu libre. Here is the command for the desktop launcher that works. I have checked that the the file is executable also.

```
/home/cmcanulty/Documents/Chess/arenalinux_64bit_1.1/Arena_x86_64_linux
```

---

### Post by Dennis N on 2018-01-27
I was intrigued, since Arena Chess used to require Wine.  To check it out, I downloaded and installed it in Mint XFCE 18.2 (based on Xubuntu 16.04, so I would expect the same outcome in Xubuntu 16.04). I used menulibre to add an entry in Whisker menu under games. That worked, and the program launches and seems to runs fine. So, is your problem that you don't get an entry in the menu, or that the program won't start? 

For reference, here is the Desktop file created by menulibre in ~/.local/share/applications:
```
[Desktop Entry]
Version=1.0
Type=Application
Name=Arena Chess
Icon=/opt/arena-chess/Arena.bmp
Exec=/opt/arena-chess/Arena_x86_64_linux
Path=/opt/arena-chess
NoDisplay=false
Categories=Game;X-XFCE;X-Xfce-Toplevel;
StartupNotify=false
Terminal=false
```

---

### Post by cmcanulty on 2018-01-28
Maybe my issue is that the program isn't in opt but in my documents. I love that they have linux now but they need to explain how to install it properly. If you have time would you like to discuss some linux chess issues? My thing I have been working on it getting chessbase to work or a workaround. I have hundreds of chessbase files. I have chessbase reader under wine but it always freezes and crashes. I know I can convert the files and read them under scid vs pc or arena. The issue is I don't get the written commentary with those, just the games. I really like to read the tutorial part that comes up when using chessbase itself. But it seems with (x)ubuntu 16.04 chessbase no longer works. I have old versions of it. I have chessbase 8 and 9.Thank you.

---

### Post by Dennis N on 2018-01-28
> Maybe my issue is that the program isn't in opt but in my documents. I love that they have linux now but they need to explain how to install it properly.

On /opt folder, It's just my habit to use it as the standard location for any games or programs that come ready to run and have no .deb file to control where it belongs. Two things I might note: On some programs, it's necessary to include the Path= when creating the menu entry to have it work. Menulibre has a box to enter it. I also ran the chown -R command on the /opt/arena-chess/ folder so that I owned all the folders and files.  

I've not seen the Chessbase program. Sorry. And I'm just an infrequent recreational player here so I'm probably not the one to discuss linux chess issues. My dad was the student of chess, as he had a shelf full of chess books and only played on a real chess board back in the pre-personal-computer days. 

I do thank you for the tip on the program being available for Linux!

---

