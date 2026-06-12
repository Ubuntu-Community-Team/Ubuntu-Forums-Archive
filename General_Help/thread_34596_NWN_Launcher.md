---
title: "NWN Launcher"
date: 2005-05-15
forum: General Help
---

### Post by Omnios on 2005-05-15
Hi I have installed Never Winter Nights RPG with a few problems I corrected (ownership and access rites problems). It runs real sweet under Linux so far except of a mouse delay problem but that ill address later. 

 I figured out a small script to lauch the game as it uses a shell script to lauch and will launch in termina cd file_Location; ./nwn. This works good in the main terminal but when I try to use Smeg to put in in the menu and that script run in terminal it pops open for a sec and terminates without launching the game. This also occures with run as it give a there is no associated action with this file error. 

 I also noted there are a lot of lauchers in usr/lib/menu that do not show up in the menue. I even tryed to manualy write a launcher for nwn but it would not show up in the menu. This is my second format and found that this occured regularly with the menue previosly. FOr example nvidia-settings is in the nenu file but does not show up in the gnomw menue. 

 Any help would be apreciated.

---

### Post by N'Jal on 2005-05-15
I havn't tryed putting nwn into the menu i just created this script then created a desktop icon, dragged that onto GDesklets and removed the desktop icon. I will try the menu now

Hmm worked for me.

Take the attached script edit the line where it points to the ./nwn file (default /usr/local/games/nwn) to where you file is, leave it in your home directory when the menu editor asks for the command point it to this script. And it should work

Ok so it wont let me upload the script, open your favorite text editor and type

cd /your/directory/here/nwn
./nwn

and save it as the nwn.sh script i talked about

Also make sure it's executible, that might help

---

