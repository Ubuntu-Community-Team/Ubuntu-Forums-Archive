---
title: "torrent clients"
date: 2008-06-09
forum: General Help
---

### Post by eival on 2008-06-09
ive tried every one of the ones in the Add/Remove and i dont like any of them. 99% of them dont even let you change settings or even know what port its using so you can forward it. and none of them even get above 10kbps(and i hate Azureus/Vuze so dont mention that one)

i went back to the client i used in windows, uTorrent, i run it through WINE, it works great i get well over 1MB/s if i run only 1 torrent at a time, but when i try to run multiple torrents it winds up stopping and giving me a "too many files open" error.

i never got this message with windows so i know its not the client.

so is there a way to adjust WINE's settings or could it be Ubuntu? if so what should i change.


im running the 64bit Hardy(8.04)

---

### Post by garethsimpsonuk on 2008-06-09
i use torrentflux which i think uses the default torrent client as it's backend. it has a web gui so you can log in and add torrents and stuff from n e where ( even your mobile ) which i think's pretty handy. 
You do need LAMP setup though but as my buntubox is a server n e way it's o.k.

hope this helps

---

### Post by kpkeerthi on 2008-06-09
> **eival said:**
> ive tried every one of the ones in the Add/Remove and i dont like any of them. 99% of them dont even let you change settings or even know what port its using so you can forward it. and none of them even get above 10kbps(and i hate Azureus/Vuze so dont mention that one)



Ubuntu comes with Transmission. It does let you see and change the port #. 

Deluge is much popular among Ubuntu users. It does let you see and change the port# too.

Which ones did you try, specifically?

---

### Post by eival on 2008-06-10
> **kpkeerthi said:**
> Ubuntu comes with Transmission. It does let you see and change the port #. 

Deluge is much popular among Ubuntu users. It does let you see and change the port# too.

Which ones did you try, specifically?

i downloaded all the ones through Add/Remove and tried them, i dont remember bein able to get anything above a few kbps on any of them, thats why i went back to uTorrent which works great but i have to babysit it or else i might not see the "too many files error"

i looked on the uTorren forum an they say something about adding a rule to "etc/security/limits.conf"

and manually set a larger number for

- nofile - max number of open files

but after i added it, i still get the error

i wasnt sure if maybe i entered the code properly, i made a thread here asking someone to varify if it looked right, but so far noones replied


[http://i28.tinypic.com/biloz.jpg](http://i28.tinypic.com/biloz.jpg)

thats a screen cap of my Config file, the bottom 2 lines are what i manually entered. and yes i saved it while logged in as Root.

---

### Post by Bubba64 on 2008-06-10
> **kpkeerthi said:**
> Ubuntu comes with Transmission. It does let you see and change the port #. 

Deluge is much popular among Ubuntu users. It does let you see and change the port# too.

Which ones did you try, specifically?

Look in edit-preferences.

---

