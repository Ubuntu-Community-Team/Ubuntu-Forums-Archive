---
title: "Nero 6 under Wine"
date: 2007-04-25
forum: General Help
---

### Post by RealG187 on 2007-04-25
In windows lets say on Drive X I have a path X:\cd burning\data cd

I use Nero in Windows to burn, lets say I add file.xyz

Next time I start Nero and have that same disc in it will check X:\cd burning cata cd\ and add file.xyz.

However in Nero Linux it won't and if I add file.xyz it will overwrite the other files and just leave the one file.

Nero Linux isn't good for multisession disks, so I wanna use the Windows version in Linux media/volumenameofmyusbharddrive is mounted to drive X:\ in wine, so they drive letters are the same, so all is good.

Exceot for the fact that Nero Burning ROM/Nero Express wont start!

[IMG]http://xs314.xs.to/xs314/07173/NeroWineLinux.png[/IMG]

does wine have olethk32.dll? Or is that a legal issue, can I copy that file from my Windows over into wine and would i work? I tired switching the Wine OS to Win 98 and had a similar message, I have ran Nero in XP and 98 with no issues, any ideas?

---

### Post by mrpaco on 2007-04-26
Try copying that dll from a windows box into ~/.wine/drive_c/windows/system32.  Wine can use Windows dlls if necessary.

---

### Post by RealG187 on 2007-04-26
I did that and Nero says to run Burn Rights, now come it doesnt pick me up as an admin?

To run burn rights I think I need another DLL, I will copy that one too! Yikes :confused:

---

### Post by panzer77 on 2007-04-26
You may just want to try the native Nero bata 3 for linux and run without Wine...  I just loaded it yesterday and it works great.

[http://www.nero.com/eng/nerolinux-prog.php?pak=16](http://www.nero.com/eng/nerolinux-prog.php?pak=16)

---

### Post by RealG187 on 2007-04-27
I just confirmed, whe I added files to my CD, the new files are there but my old ones aren't!!

Also, can I mount CD NRG/ISO?? And work with NRGs without converting?

I will try Nero 3, my I have to reinstall anyways, I had to reinstall Windoze too, dunno why BOTH my OSes F***ed up!! [Soory about that, I am mad! REALLY MAD!]

---

### Post by orb9220 on 2007-04-27
> Nero 6 under Wine

No way,nada,negative,can't be done,wasting your time,isn't possible.

---

