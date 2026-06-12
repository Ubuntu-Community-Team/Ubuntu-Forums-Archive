---
title: "Utorrent on startup?"
date: 2007-11-10
forum: General Help
---

### Post by mikey12345 on 2007-11-10
Hi,

I followed the utorrent under wine guide and all works fine. I can now access the web page from a remote PC and download torrents. Great stuff. I wondered how do i get this to open on startup so should i need to reboot the PC it will just be open and running?


Next quesitons..

When i start ubuntu 7.10 my monitor shows it booting the bios etc then always says out of range till the login window. How can i stop this? It also does it on shutdown.


Thanks.
Mikey.

---

### Post by neoroses on 2007-11-10
you want utorrent to open on start up?
system ---> preferences --> sessions

then add
env WINEPREFIX="/home/howie/.wine" wine "H:\downloads\programs\utorrent\utorrent.exe"

replaceing file locations and names with your own 

or

wine /location/of/utorrent.exe

in the command box

call it what ever you want :)

i think this shud work :)

---

### Post by mikey12345 on 2007-11-10
I did the first part you suggested and worked a treat.

Thanks for that.

---

