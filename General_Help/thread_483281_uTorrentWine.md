---
title: "uTorrent/Wine"
date: 2007-06-24
forum: General Help
---

### Post by iota on 2007-06-24
Heya, I just switched to ubuntu a little while back and finally got round to installing utorrent last night. At first it was all working fine, except for that minimise to tray bug which is annoying but harmless.

Unfortunately now whenever I open utorrent it will run in tray, but will not open the window. I've tried getting wine to emulate a windows desktop and tried reinstalling wine to no avail. The program seems to run fine, apparently it's downloading/uploading happily, it just won't open the window.

The uTorrent executable is stored in /home/nihil/winprogs/utorrent.exe and the desktop launcher runs it with "Wine /home/nihil/wineprogs/utorrent.exe" and was working fine.

If anyone has any ideas that'd be grand :P Chars guys

---

### Post by s_h_a_d_o_w_s on 2007-06-24
Why don't you just run a linux torrent client? Thereare plenty that are supported, like Bittorrent, Azureus, Bittornado, Qtorrent, Ktorrent

:D

in terminal: (Applications -> Accesories -> Terminal

```
sudo apt-get install (package name)
```

example:

```
sudo apt-get install bittornado
```

then enter your password.

Bittorrent is installed by default

---

### Post by Can0n on 2007-06-24
Dont know if this is the "problem" I had but I just double-clicks on the icon in the tray everytime I want to maximize/minimize.

---

### Post by juanvicfer on 2007-06-24
I recommend the KTorrent client, i works fine with Ubuntu, although it's made for KDE.

---

### Post by iota on 2007-06-24
Yeah that's the minimise to tray bug, which isn't too bad. Cheers for the suggestion though :)

I will resort to a linux client if I can't get utorrent working, at least until the 1.7 beta works properly using wine. But to be honest most of the just don't seem to be as good :( For one thing I quite like the interface, and it has more features.

Just wondering if anyone else has had the same problem with it? If so in the meantime you can always try using it through the webui :P

---

### Post by s_h_a_d_o_w_s on 2007-06-24
[http://appdb.winehq.org/appview.php?iVersionId=7622](http://appdb.winehq.org/appview.php?iVersionId=7622)

It says everything is working fine :D Not sure about the beta check taht link :D

---

### Post by HoMe_CaNiBaL on 2007-06-24
[http://ubuntuforums.org/showthread.php?t=295134&highlight=howto+utorrent+wine](http://ubuntuforums.org/showthread.php?t=295134&highlight=howto+utorrent+wine)

read the first post at the end.

---

### Post by AriciU on 2007-07-05
Same thing here. Today it just won't maximise from the tray anymore. It used to work fine but now i can't get it to show no matter what i try. So god damn frustrating :mad:

---

### Post by Steveway on 2007-07-05
Nobody mentioned Deluge?
That is one of the most awesome Clients for Linux.
It looks a bit like Utorrent but in GTK!

---

### Post by AriciU on 2007-07-05
Nevermind.

I had to delete "settings.dat" and "settings.dat.old" from /username/.wine/drive_c/windows/Application Data/uTorrent and reconfigure the whole thing leaving all the Tray related options unchecked.

---

### Post by Beatbreaker on 2007-07-06
> **AriciU said:**
> Nevermind.

I had to delete "settings.dat" and "settings.dat.old" from /username/.wine/drive_c/windows/Application Data/uTorrent and reconfigure the whole thing leaving all the Tray related options unchecked.

actually i think it's located here:

/home/USERNAME/.wine/drive_c/windows/profiles/USERNAME/Application Data/uTorrent/

i found that deleting my uTorrent directory did the trick

---

### Post by isecore on 2007-07-06
I'm just curious and I don't mean to bash (no pun intended) your wish to run uTorrent through wine, but what exactly are you missing from the plethora of GNOME/Linux-native bittorrent clients? 

If there's something specific I'm pretty sure you could make a wish at some of the developers websites and they might consider implementing these functions in the future. Free software and open source is after all about evolution, and without user input it's difficult to guess what the users expect from the software. If you're handy with a compiler you could also grab the source and contribute, although this isn't the most straight-forward option unless you're a programmer.

(Disclaimer: I'm not a developer nor a programmer nor am in any way affiliated with any of the Linux-based torrent clients out there)

---

### Post by oomingmak on 2007-07-06
> **Steveway said:**
> Nobody mentioned [**Deluge**]("http://dev.deluge-torrent.org/wiki/Screenshots")?

OT: Thank you for mentioning this program (I am new to Linux and I had never even heard of it before).

I've not tried it out yet, but I have to say that it does look really great from the screenshots (and I am one fussy b****** when it comes to UIs).

I look forward to trying it out. (Hopefully the performance / speed lives up to the looks).

---

### Post by iota on 2007-07-07
Tbh it's not really the features, it's just the design. The interface in utorrent kicks *** :) Plus the encryption on it actually seems to beat my isp's attempts at traffic shaping (something that doesn't seem to work with any of the other bittorrent clients, in windows or linux).

Having said that though, deluge does look very nice. But, truth be told, I've just been using utorrent for too long :)

---

### Post by Wiebelhaus on 2007-07-07
> **s_h_a_d_o_w_s said:**
> Why don't you just run a linux torrent client? Thereare plenty that are supported, like Bittorrent, Azureus, Bittornado, Qtorrent, Ktorrent

:D

in terminal: (Applications -> Accesories -> Terminal

```
sudo apt-get install (package name)
```

example:

```
sudo apt-get install bittornado
```

then enter your password.

Bittorrent is installed by default


For an ex-utorrent user , I find Ktorrent the best , IMO.

---

### Post by mytwobears on 2007-07-07
Yes, Ktorrent is a really great client.  It also has an Encryption feature and a block iplist function like utorrent and many other features.  Gives you all the information you want and if you needed more I guess you could ask for it or check to see if there is already a plugin available for that function.

I am intrigued by Deluge and will also give it a try, thanks for the suggestion :).

---

### Post by TechZilla on 2007-09-09
i was also a bittornado guy, for years.]

the thing about bitornado is that it is never updated....

it just is too detectable by ISP's these days as well.  and to be honest the linux verison needs considrable work (actually not a bad project to think about for myself....considering it is python)

as of now i use Ktorrent, and i hate most clients so this means a lot.    i also previously used qtorrent, which is not bad (has less depecndancy's)

but still i prefer Ktorrent and i'm usualy more into the Q's then then the 
K;s.... its just a damn good client (better then utorrent if u ask me)
]

---

### Post by mwolfe on 2007-09-09
I run uTorrent through wine in ubuntu feisty and i love it. I've tried deluge, ktorrent, azureus, and pretty much every bittorent client offered in linux and i find utorrent the best. I've tested some torrent files and utorrent seems to download faster than the others (by far) when i've tested.. Maybe the problem lied somehwere else, but deluge was much slower. I had good success for a long time with azureus but then one time it started messing up my interent connection when i opened it (probably a java issue) and so i stopped using that (plus it uses a lot of memory). 

Utorrent does act strange though, to minimize/maximize don't use the normal minimize/maximize buttons, just double click on the tray icon. Using minimize/maximize will make it look like its locked on your screen.

---

### Post by mwolfe on 2007-09-09
Also, you can drag and drop torrent files into utorrent (download them to your desktop first)
this saves time over manually browsing.. I'm not sure if there is a way you can get firefox or whatever to open the torrent file directly into utorrent though.. I find dragging and dropping the files to be fast enough. And utorrent uses a tiny memory footprint, even through wine. I love open source software, but in this area i think utorrent has any open source solution beat pretty easily. I'll try deluge again sometime though and see if its improved.

---

