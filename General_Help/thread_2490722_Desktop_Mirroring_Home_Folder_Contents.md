---
title: "Desktop Mirroring Home Folder Contents"
date: 2023-09-13
forum: General Help
---

### Post by iancompetent2 on 2023-09-13
I have attempted a few fixes for this, including creating a new Desktop folder and using the "xdg-user-dirs-update --set DESKTOP $HOME/Desktop" command. I've also tried manually changing the file in the user-dirs.dirs file from XDG_DESKTOP_DIR="$HOME/" to XDG_DESKTOP_DIR="$HOME/desktop" and rebooting. It sometimes works temporarily but eventually goes back to mirroring the files on startup. I've even done a clean install and an OS upgrade and am still having the same issue.

Does anybody know a permanent fix for this problem?

Thanks.

Edit: I was using 22.04 and am now using 23.04

---

### Post by MAFoElffen on 2023-09-13
Trying to understand the problem you are describing. Show us the data...
```

ls $HOME
tree $HOME

```

---

### Post by iancompetent2 on 2023-09-13
Here's what I get when I run those commands. It is - literally - every file in my Home folder:

```
ian@ian-HP-Laptop-15-db0xxx:~$ ls $HOME
 Desktop     Music                                 ProMash   Templates
 Documents  'NCA 74 Leics Notts Wolds RY v2.pdf'   Public    Videos
 Downloads   Pictures                              snap
ian@ian-HP-Laptop-15-db0xxx:~$ tree $HOME
/home/ian
&#9500;&#9472;&#9472; Desktop
&#9500;&#9472;&#9472; Documents
&#9474;   &#9500;&#9472;&#9472; Annapolis Royal.docx
&#9474;   &#9500;&#9472;&#9472; Annapolis Royal.odt
&#9474;   &#9500;&#9472;&#9472; Cumbria-Lake District
&#9474;   &#9500;&#9472;&#9472; Days.odt
&#9474;   &#9500;&#9472;&#9472; Dorset-Devon
&#9474;   &#9500;&#9472;&#9472; East Midlands
&#9474;   &#9474;   &#9492;&#9472;&#9472; WessexDowns.odt
&#9474;   &#9500;&#9472;&#9472; Great West Way.odt
&#9474;   &#9500;&#9472;&#9472; Hops.odt
&#9474;   &#9500;&#9472;&#9472; Lincolnshire-Peak District
&#9474;   &#9474;   &#9492;&#9472;&#9472; Midlands.odt
&#9474;   &#9500;&#9472;&#9472; Overview.odt
&#9474;   &#9500;&#9472;&#9472; Shropshire-Cheshire
&#9474;   &#9474;   &#9500;&#9472;&#9472; Shropshire & Cheshire.odt
&#9474;   &#9474;   &#9492;&#9472;&#9472; Untitled 1.odt
&#9474;   &#9500;&#9472;&#9472; Trips
&#9474;   &#9500;&#9472;&#9472; Wessex Downs-Northamptonshire
&#9474;   &#9474;   &#9500;&#9472;&#9472; WessexDowns (Cotswolds Version).odt
&#9474;   &#9474;   &#9500;&#9472;&#9472; WessexDowns (Essex Version).odt
&#9474;   &#9474;   &#9492;&#9472;&#9472; WessexDowns.odt
&#9474;   &#9500;&#9472;&#9472; WII.odt
&#9474;   &#9500;&#9472;&#9472; Ye Olde Englande II.odt
&#9474;   &#9500;&#9472;&#9472; Ye Olde Englande.odt
&#9474;   &#9500;&#9472;&#9472; Yorkshire
&#9474;   &#9492;&#9472;&#9472; Zoom
&#9474;       &#9500;&#9472;&#9472; 2021-10-31 13.01.55 ian competent's Zoom Meeting
&#9474;       &#9474;   &#9500;&#9472;&#9472; audio1839448448.m4a
&#9474;       &#9474;   &#9500;&#9472;&#9472; recording.conf
&#9474;       &#9474;   &#9492;&#9472;&#9472; video1839448448.mp4
&#9474;       &#9500;&#9472;&#9472; 2021-11-01 17.52.15 ian competent's Zoom Meeting
&#9474;       &#9474;   &#9500;&#9472;&#9472; audio1340180696.m4a
&#9474;       &#9474;   &#9500;&#9472;&#9472; recording.conf
&#9474;       &#9474;   &#9492;&#9472;&#9472; video1340180696.mp4
&#9474;       &#9500;&#9472;&#9472; 2021-11-01 17.53.24 ian competent's Zoom Meeting
&#9474;       &#9474;   &#9500;&#9472;&#9472; audio1865248629.m4a
&#9474;       &#9474;   &#9500;&#9472;&#9472; recording.conf
&#9474;       &#9474;   &#9492;&#9472;&#9472; video1865248629.mp4
&#9474;       &#9492;&#9472;&#9472; 2021-11-01 17.54.11 ian competent's Zoom Meeting
&#9474;           &#9500;&#9472;&#9472; audio1867217458.m4a
&#9474;           &#9500;&#9472;&#9472; recording.conf
&#9474;           &#9492;&#9472;&#9472; video1867217458.mp4
&#9500;&#9472;&#9472; Downloads
&#9474;   &#9500;&#9472;&#9472; 1043905_10151687479047180_1812984160_n.jpg
&#9474;   &#9500;&#9472;&#9472; 1146-High-Street,-Braunston-in-Rutland.jpg
&#9474;   &#9500;&#9472;&#9472; 20230619_161854.mp4
&#9474;   &#9500;&#9472;&#9472; 20230627_101132_001.mp4
&#9474;   &#9500;&#9472;&#9472; 5269.avif
&#9474;   &#9500;&#9472;&#9472; Admiral-Of-the-Humber-menu.jpg
&#9474;   &#9500;&#9472;&#9472; Barnwell.jpg
&#9474;   &#9500;&#9472;&#9472; belper-town-centre-derbyshire-england-uk-gb-DYNTGW.jpg
&#9474;   &#9500;&#9472;&#9472; BraunstonInRutland.jpeg
&#9474;   &#9500;&#9472;&#9472; Brockenhurst-village-walk-85-1024x683.jpg
&#9474;   &#9500;&#9472;&#9472; claires edit barge july.jpg
&#9474;   &#9500;&#9472;&#9472; come-and-meet-the-woolly.jpg
&#9474;   &#9500;&#9472;&#9472; Discover Map May 2023 V2.pdf
&#9474;   &#9500;&#9472;&#9472; D train times 21 May to 9 December 2023 v3.pdf
&#9474;   &#9500;&#9472;&#9472; dukeriestrail (1)_42752439.pdf
&#9474;   &#9500;&#9472;&#9472; flitch-map-panel-2013-felsted-1png-edited_orig.png
&#9474;   &#9500;&#9472;&#9472; form_to_email.php
&#9474;   &#9500;&#9472;&#9472; Gritstone_Trail_Guide_651651353-1.pdf
&#9474;   &#9500;&#9472;&#9472; Gritstone_Trail_Guide_651651353.pdf
&#9474;   &#9500;&#9472;&#9472; Gritstone Trail Leaflet_555363690.pdf
&#9474;   &#9500;&#9472;&#9472; GWW Discoverer.pdf
&#9474;   &#9500;&#9472;&#9472; HB_1.01_Race_robot.webp
&#9474;   &#9500;&#9472;&#9472; high-street-egham-surrey-england-vereinigtes-konigreich-e04fa3.jpg
&#9474;   &#9500;&#9472;&#9472; image000007.jpg
&#9474;   &#9500;&#9472;&#9472; NR_Easements_November2022.pdf
&#9474;   &#9500;&#9472;&#9472; Oxford day ranger 032020.pdf
&#9474;   &#9500;&#9472;&#9472; receipt_IAN-DARES.pdf
&#9474;   &#9500;&#9472;&#9472; Sadie.JPG
&#9474;   &#9500;&#9472;&#9472; Sadie.mp4
&#9474;   &#9500;&#9472;&#9472; Seaton.jpg
&#9474;   &#9500;&#9472;&#9472; Seaton.webp
&#9474;   &#9500;&#9472;&#9472; shutterstock_1427772974-scaled.jpg
&#9474;   &#9500;&#9472;&#9472; South-Downs-Leaflet-Meon-Valley_2042404894.pdf
&#9474;   &#9500;&#9472;&#9472; Stour-Valley-Planning-Route.pdf
&#9474;   &#9500;&#9472;&#9472; T7 train times 21 May to 9 December 2023 v3.pdf
&#9474;   &#9500;&#9472;&#9472; Thames branches 032020.pdf
&#9474;   &#9500;&#9472;&#9472; Thurston.jpg
&#9474;   &#9500;&#9472;&#9472; TOCs AS v53 Dec 2022.pdf
&#9474;   &#9500;&#9472;&#9472; town-centre-thirsk-yorkshire-GDR6EB.jpg
&#9474;   &#9500;&#9472;&#9472; TS train times 21 May to 9 December 2023 v3.pdf
&#9474;   &#9500;&#9472;&#9472; VIDEO-2022-03-20-21-48-32.mp4
&#9474;   &#9500;&#9472;&#9472; Walks-And-Walking-Essex-Walks-Epping-Forest-Walking-Routes-Map-2012.jpg
&#9474;   &#9500;&#9472;&#9472; yost-1-1-1941883-1680791386506.png
&#9474;   &#9492;&#9472;&#9472; yt1s.com - Wheels On The Bus More Nursery Rhymes Kids Songs Songs for Littles.mp4
&#9500;&#9472;&#9472; Music -> /home/ian/Music
&#9500;&#9472;&#9472; NCA 74 Leics Notts Wolds RY v2.pdf
&#9500;&#9472;&#9472; Pictures
&#9474;   &#9500;&#9472;&#9472; 20220214_131136.jpg
&#9474;   &#9500;&#9472;&#9472; 20220214_131140.jpg
&#9474;   &#9500;&#9472;&#9472; 20220214_131142.jpg
&#9474;   &#9500;&#9472;&#9472; 20220214_131144.jpg
&#9474;   &#9500;&#9472;&#9472; Race
&#9474;   &#9474;   &#9500;&#9472;&#9472; 2df97de9c17d68c2.jpg
&#9474;   &#9474;   &#9492;&#9472;&#9472; HB_1.01_Race_robot.jpg
&#9474;   &#9500;&#9472;&#9472; Screenshot from 2021-12-07 20-01-00.png
&#9474;   &#9500;&#9472;&#9472; Screenshot from 2021-12-25 09-28-15.png
&#9474;   &#9500;&#9472;&#9472; Screenshot from 2022-02-18 19-07-27.png
&#9474;   &#9500;&#9472;&#9472; Screenshots
&#9474;   &#9474;   &#9500;&#9472;&#9472; Screenshot from 2023-05-02 14-10-18.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; Screenshot from 2023-05-27 15-32-12.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; Screenshot from 2023-05-27 15-48-24.png
&#9474;   &#9474;   &#9500;&#9472;&#9472; Screenshot from 2023-05-27 15-48-25.png
&#9474;   &#9474;   &#9492;&#9472;&#9472; Screenshot from 2023-06-13 20-02-07.png
&#9474;   &#9500;&#9472;&#9472; Tires
&#9474;   &#9474;   &#9500;&#9472;&#9472; TireRim.jpg
&#9474;   &#9474;   &#9500;&#9472;&#9472; TireSize.jpg
&#9474;   &#9474;   &#9500;&#9472;&#9472; TireTread.jpg
&#9474;   &#9474;   &#9492;&#9472;&#9472; TireType.jpg
&#9474;   &#9492;&#9472;&#9472; Wallpapers
&#9474;       &#9500;&#9472;&#9472; Barnwell.jpg
&#9474;       &#9500;&#9472;&#9472; Brockenhurst-village-walk-85-1024x683.jpg
&#9474;       &#9492;&#9472;&#9472; herefordshire.webp
&#9500;&#9472;&#9472; ProMash
&#9474;   &#9492;&#9472;&#9472; ProMashReal
&#9474;       &#9500;&#9472;&#9472; art
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb01_2.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb01_3.BMP
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb01.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb02_2.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb02_3.BMP
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb02.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb03_2.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb03.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb04_2.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb04_3.BMP
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb04.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb05_2.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb05_3.BMP
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb05.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb06_2.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb06_3.BMP
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb06.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb07_2.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb07_3.BMP
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb07.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb08_2.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb08_3.BMP
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb08.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb09_2.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb09_3.BMP
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb09.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb10_2.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb10_3.BMP
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb10.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb11_2.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb11_3.BMP
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb11.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb12_2.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb12_3.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb12.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb13_2.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb13_3.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; cb13.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; db01_2.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; db01_3.BMP
&#9474;       &#9474;   &#9500;&#9472;&#9472; db01.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; db02_2.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; db02_3.BMP
&#9474;       &#9474;   &#9500;&#9472;&#9472; db02.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; db03_2.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; db03_3.BMP
&#9474;       &#9474;   &#9500;&#9472;&#9472; db03.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; db04_2.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; db04_3.BMP
&#9474;       &#9474;   &#9500;&#9472;&#9472; db04.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; db05_2.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; db05_3.BMP
&#9474;       &#9474;   &#9500;&#9472;&#9472; db05.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; db06_2.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; db06_3.BMP
&#9474;       &#9474;   &#9500;&#9472;&#9472; db06.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; MASHPRO.BMP
&#9474;       &#9474;   &#9500;&#9472;&#9472; pmback2.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; pmback3.BMP
&#9474;       &#9474;   &#9500;&#9472;&#9472; PMBack.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; rb01_2.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; rb01_3.BMP
&#9474;       &#9474;   &#9500;&#9472;&#9472; rb01.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; rb02_2.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; rb02_3.BMP
&#9474;       &#9474;   &#9500;&#9472;&#9472; rb02.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; rb03_2.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; rb03_3.BMP
&#9474;       &#9474;   &#9500;&#9472;&#9472; rb03.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; rb04_2.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; rb04_3.BMP
&#9474;       &#9474;   &#9500;&#9472;&#9472; rb04.bmp
&#9474;       &#9474;   &#9500;&#9472;&#9472; REF2.BMP
&#9474;       &#9474;   &#9492;&#9472;&#9472; Thumbs.db
&#9474;       &#9500;&#9472;&#9472; BPSys.DAT
&#9474;       &#9500;&#9472;&#9472; EXTRA.DAT
&#9474;       &#9500;&#9472;&#9472; hop_repository
&#9474;       &#9500;&#9472;&#9472; HOPS.DAT
&#9474;       &#9500;&#9472;&#9472; hsort1.srt
&#9474;       &#9500;&#9472;&#9472; hsort2.srt
&#9474;       &#9500;&#9472;&#9472; html_exports
&#9474;       &#9474;   &#9500;&#9472;&#9472; 01-03-1998_Company_1_Red_Ale.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 01-03-1998_Company_1_Red_Ale_mash.jpg
&#9474;       &#9474;   &#9500;&#9472;&#9472; 01-03-1998_Company_1_Red_Ale_water.jpg
&#9474;       &#9474;   &#9500;&#9472;&#9472; 11-15-1997_Jeffreys_Winter_White.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 11-15-1997_Jeffreys_Winter_White_mash.jpg
&#9474;       &#9474;   &#9500;&#9472;&#9472; 12-15-1997_Victory_IPA.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; 12-15-1997_Victory_IPA_mash.jpg
&#9474;       &#9474;   &#9500;&#9472;&#9472; 12-15-1997_Victory_IPA_water.jpg
&#9474;       &#9474;   &#9500;&#9472;&#9472; Company_1_Red_Ale.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; Company_1_Red_Ale_mash.jpg
&#9474;       &#9474;   &#9500;&#9472;&#9472; Jeffreys_Winter_White.html
&#9474;       &#9474;   &#9500;&#9472;&#9472; Jeffreys_Winter_White_mash.jpg
&#9474;       &#9474;   &#9500;&#9472;&#9472; Victory_IPA.html
&#9474;       &#9474;   &#9492;&#9472;&#9472; Victory_IPA_mash.jpg
&#9474;       &#9500;&#9472;&#9472; html_themes
&#9474;       &#9500;&#9472;&#9472; jpg_exports
&#9474;       &#9474;   &#9500;&#9472;&#9472; BurtonMarin2.jpg
&#9474;       &#9474;   &#9500;&#9472;&#9472; Fix_40_50_60_70.jpg
&#9474;       &#9474;   &#9500;&#9472;&#9472; German_Mash_Double_Decoc.jpg
&#9474;       &#9474;   &#9492;&#9472;&#9472; HopDegradation.jpg
&#9474;       &#9500;&#9472;&#9472; Malt.dat
&#9474;       &#9500;&#9472;&#9472; mashschedules
&#9474;       &#9474;   &#9500;&#9472;&#9472; Dave_BelgianWhite.msh
&#9474;       &#9474;   &#9500;&#9472;&#9472; Dave_OatmealStout.msh
&#9474;       &#9474;   &#9500;&#9472;&#9472; Fix_40_50_60_70.msh
&#9474;       &#9474;   &#9500;&#9472;&#9472; Fix_40_60_70.msh
&#9474;       &#9474;   &#9492;&#9472;&#9472; German Mash Double Decoction.msh
&#9474;       &#9500;&#9472;&#9472; msort1.srt
&#9474;       &#9500;&#9472;&#9472; msort2.srt
&#9474;       &#9500;&#9472;&#9472; pm_lovrgb.dat
&#9474;       &#9500;&#9472;&#9472; pm_lovrgb.ldt
&#9474;       &#9500;&#9472;&#9472; ProCSys.DAT
&#9474;       &#9500;&#9472;&#9472; ProDir.dir
&#9474;       &#9500;&#9472;&#9472; ProGlobalWin.pos
&#9474;       &#9500;&#9472;&#9472; Promash.cnt
&#9474;       &#9500;&#9472;&#9472; ProMash.exe
&#9474;       &#9500;&#9472;&#9472; PROMASH.HLP
&#9474;       &#9500;&#9472;&#9472; ProMSys.DAT
&#9474;       &#9500;&#9472;&#9472; ProWin.pos
&#9474;       &#9500;&#9472;&#9472; recipes
&#9474;       &#9474;   &#9500;&#9472;&#9472; 01-22-2018_The Gaffer's Home Brew .brw
&#9474;       &#9474;   &#9500;&#9472;&#9472; 01-30-2018_Judy's Big Gamble American-Hopped Best Bitter.brw
&#9474;       &#9474;   &#9500;&#9472;&#9472; 03-13-2017_Porter.brw
&#9474;       &#9474;   &#9500;&#9472;&#9472; 03-17-2017_Best Bitter II.brw
&#9474;       &#9474;   &#9500;&#9472;&#9472; 03-24-2017_Mild.brw
&#9474;       &#9474;   &#9500;&#9472;&#9472; 04-01-2017_Centennial IPA.brw
&#9474;       &#9474;   &#9500;&#9472;&#9472; Ahtanum Bitter.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Amarillo IPA.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; American IPA.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; American Pale Ale.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Autumn Ale.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Ben's Pale.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Best Bitter II.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Best Bitter.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Bitter.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Burton Ale.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Cascade IPA.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Centennial Pale Ale.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Common.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Continental Bitter.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Cornish Pale.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Dark Bitter.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; EKG Golden Ale.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; EKG Pale Ale.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Endeavour Pale.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; English Blonde Ale.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; English Export Ale.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; English Imperial IPA.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; English IPA.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; English Pale.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; English Session IPA.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; English Wheat.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Extra Bitter.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Extra Pale.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Fuggle IPA.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Golden Ale.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Golden Bitter.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Golden Mild II.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Golden Mild.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; IPA.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Irish Stout.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Kentish Ale.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Light Ale.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Margaret's Tipple
&#9474;       &#9474;   &#9500;&#9472;&#9472; Margaret's Tipple.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Mild.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Nelson Sauvin Blonde Ale.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Northamptonshire Gold.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Northdown Bitter.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Northern Brown.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Oatmeal Stout.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Old Ale .rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Pale Ale II.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Pale Ale.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Pisser's Gold.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Porter.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Royal Red Bitter.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Scottish 60 .rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Seafarer's Session
&#9474;       &#9474;   &#9500;&#9472;&#9472; Session Ale.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Simcoe Pale Ale.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Simcoe Session IPA.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Southern Brown.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Sovereign Ale.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Special Bitter.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Strangeways Ale.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Summer Ale.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Summer Pale.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; The Gaffer's Home Brew .rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Trad English Pale.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Transatlantic Pale Ale.rec
&#9474;       &#9474;   &#9492;&#9472;&#9472; Young Dimwitted Pheasant.rec
&#9474;       &#9500;&#9472;&#9472; recipesII
&#9474;       &#9500;&#9472;&#9472; RPSys.DAT
&#9474;       &#9500;&#9472;&#9472; sessions
&#9474;       &#9474;   &#9500;&#9472;&#9472; 010398_Company1Red.brw
&#9474;       &#9474;   &#9500;&#9472;&#9472; 111597_WinterWhite.brw
&#9474;       &#9474;   &#9500;&#9472;&#9472; 121597_VictoryIPA.brw
&#9474;       &#9474;   &#9500;&#9472;&#9472; American Old Ale.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; American Table Beer.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; ANZAC IPA.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Basic Bitter.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Best Bitter.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Bitter.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Burton Ale.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Cascade Gold.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Cask Lager.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; East Coast IPA.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; English IPA.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; English Pale.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; First Gold.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Grease Monkey's Skunk ****.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Mild.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Northern Brown.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Oatmeal Stout.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Old Ale .rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Porter.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Seafarer's Pale Ale.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Seafarer's Session
&#9474;       &#9474;   &#9500;&#9472;&#9472; Session IPA.rec
&#9474;       &#9474;   &#9500;&#9472;&#9472; Table Beer.rec
&#9474;       &#9474;   &#9492;&#9472;&#9472; West Coast IPA.rec
&#9474;       &#9500;&#9472;&#9472; ssort1.srt
&#9474;       &#9500;&#9472;&#9472; ssort2.srt
&#9474;       &#9500;&#9472;&#9472; STYLES.BJCP
&#9474;       &#9500;&#9472;&#9472; STYLES.DAT
&#9474;       &#9500;&#9472;&#9472; text_exports
&#9474;       &#9500;&#9472;&#9472; WATER.DAT
&#9474;       &#9500;&#9472;&#9472; waterprofiles
&#9474;       &#9474;   &#9500;&#9472;&#9472; Burton_Marin1.wtr
&#9474;       &#9474;   &#9492;&#9472;&#9472; Burton_Marin2.wtr
&#9474;       &#9500;&#9472;&#9472; WATER_USAGE.DAT
&#9474;       &#9500;&#9472;&#9472; wsort2.srt
&#9474;       &#9500;&#9472;&#9472; YEAST.DAT
&#9474;       &#9500;&#9472;&#9472; ysort1.srt
&#9474;       &#9492;&#9472;&#9472; ysort2.srt
&#9500;&#9472;&#9472; Public -> /home/ian/Public
&#9500;&#9472;&#9472; snap
&#9474;   &#9500;&#9472;&#9472; firefox
&#9474;   &#9474;   &#9500;&#9472;&#9472; 3068
&#9474;   &#9474;   &#9500;&#9472;&#9472; common
&#9474;   &#9474;   &#9492;&#9472;&#9472; current -> 3068
&#9474;   &#9500;&#9472;&#9472; okular
&#9474;   &#9474;   &#9500;&#9472;&#9472; 142
&#9474;   &#9474;   &#9500;&#9472;&#9472; common
&#9474;   &#9474;   &#9492;&#9472;&#9472; current -> 142
&#9474;   &#9500;&#9472;&#9472; snapd-desktop-integration
&#9474;   &#9474;   &#9500;&#9472;&#9472; 83
&#9474;   &#9474;   &#9500;&#9472;&#9472; common
&#9474;   &#9474;   &#9492;&#9472;&#9472; current -> 83
&#9474;   &#9492;&#9472;&#9472; snap-store
&#9474;       &#9500;&#9472;&#9472; 959
&#9474;       &#9500;&#9472;&#9472; common
&#9474;       &#9492;&#9472;&#9472; current -> 959
&#9500;&#9472;&#9472; Templates
```

---

### Post by MAFoElffen on 2023-09-14
Could you please go back to your last post, edit it and put the output within CODE Tags? (Advance Replay > Select the output with your mouse to highlight. Swlwct the "#" icon to wrap the selected text with CODE tags...

The way you worded things, I expected the output to show mirrored duplicates of files. I don't see that. Could you please explain what is the problem is in more detail?

---

### Post by iancompetent2 on 2023-09-14
> **MAFoElffen said:**
> Could you please go back to your last post, edit it and put the output within CODE Tags? (Advance Replay > Select the output with your mouse to highlight. Swlwct the "#" icon to wrap the selected text with CODE tags...

The way you worded things, I expected the output to show mirrored duplicates of files. I don't see that. Could you please explain what is the problem is in more detail?

Fair enough, I'm no expert so I'm kind of hacking my way through here. While I very much appreciate your efforts to help me, I'm not really understanding what you are asking for, either. 

Part of the problem is that my output was given after I had fixed my issue. Let's go back to the start:

Some of the time, I will start up my laptop and it will be fine.

Other times, it puts all of the contents from my Home, Public, Music and Desktop folders on the actual desktop.

Something seems to be altering my user-dirs.dirs file in the Home's .config folder. 

When it works, the file reads like this:

XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"

When it doesn't, it reads like this:

XDG_DESKTOP_DIR="$HOME/"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/"

I have no idea why it eliminates the qualifiers on those four folders. If I fix them manually and restart, it corrects the problem. Unfortunately, it seems to eventually come back.

---

### Post by MAFoElffen on 2023-09-14
Wait...

I've seen this before. Recently. Where someone was asking how to move the home folder from inside the Desktop to repair their Home folder...

Was that you with another Forum ID or another user?

I remember seeing the thread, but I can't find it in the Forum Search...

---

### Post by #&amp;thj^% on 2023-09-14
seems somehow the XDG_DESKTOP_DIR is pointing to your $HOME directory. If that is the case then it should be pointing to $HOME/Desktop

To change this navigate to the .config directory. Ctrl+h shows hidden files/directories in the file manager.

Look for a file called user-dirs.dirs, this is the file you will be editing.

From this file you can set the default directories for various things like Downloads, Documents, Video, etc.

look for the line XDG_DESKTOP_DIR and set it to:

XDG_DESKTOP_DIR="$HOME/Desktop"
Save, exit and restart the file manager and possibly your machine.
Mine:
```
From this file you can set the default directories for various things like Downloads, Documents, Video, etc.

look for the line XDG_DESKTOP_DIR and set it to:

XDG_DESKTOP_DIR="$HOME/Desktop"
Save, exit and restart the file manager and possibly your machine.

# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run.
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```
EDIT This is why yours won't last over reboots:
> **iancompetent2 said:**
>  XDG_DESKTOP_DIR=**_"$HOME/desktop"_** and rebooting. It sometimes works temporarily but eventually goes back to mirroring the files on startup. I've even done a clean install and an OS upgrade and am still having the same issue.

Does anybody know a permanent fix for this problem?

Thanks.

Edit: I was using 22.04 and am now using 23.04
desktop needs to read Desktop

---

### Post by iancompetent2 on 2023-09-14
> **MAFoElffen said:**
> Wait...  I've seen this before. Recently. Where someone was asking how to move the home folder from inside the Desktop to repair their Home folder...  Was that you with another Forum ID or another user?  I remember seeing the thread, but I can't find it in the Forum Search...  That's either not me or it's my recent thread on Ask Ubuntu and I've not explained my issue very well.

---

### Post by iancompetent2 on 2023-09-14
> **1fallen said:**
> seems somehow the XDG_DESKTOP_DIR is pointing to your $HOME directory. If that is the case then it should be pointing to $HOME/Desktop

To change this navigate to the .config directory. Ctrl+h shows hidden files/directories in the file manager.

Look for a file called user-dirs.dirs, this is the file you will be editing.

From this file you can set the default directories for various things like Downloads, Documents, Video, etc.

look for the line XDG_DESKTOP_DIR and set it to:

XDG_DESKTOP_DIR="$HOME/Desktop"
Save, exit and restart the file manager and possibly your machine.
Mine:
```
From this file you can set the default directories for various things like Downloads, Documents, Video, etc.

look for the line XDG_DESKTOP_DIR and set it to:

XDG_DESKTOP_DIR="$HOME/Desktop"
Save, exit and restart the file manager and possibly your machine.

# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run.
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```
EDIT This why yours won't last over reboots:

desktop needs to read Desktop

I tried your solution and it seemed to work. That totally makes sense. Now I have to see if it lasts. Thus far, something seems to rewrite the file upon boot up.

Thank you so much for your wisdom and patience. Much appreciated!

---

### Post by #&amp;thj^% on 2023-09-14
> **iancompetent2 said:**
> That's either not me or it's my recent thread on Ask Ubuntu and I've not explained my issue very well.
he was looking for another post here in UF, I had seen your AU post this morning as well.
> **iancompetent2 said:**
> I tried your solution and it seemed to work. That totally makes sense. Now I have to see if it lasts. Thus far, something seems to rewrite the file upon boot up.

Thank you so much for your wisdom and patience. Much appreciated!

keep us posted please.

---

### Post by angelosmal2 on 2023-11-24
I have the same problem. I tried this solution but when I restart the machine the user-dirs.dirs file is back to this read:

[COLOR=#000000]XDG_DESKTOP_DIR="$HOME/"[/COLOR]
[COLOR=#000000]XDG_DOWNLOAD_DIR="$HOME/Downloads"[/COLOR]
[COLOR=#000000]XDG_TEMPLATES_DIR="$HOME/Templates"[/COLOR]
[COLOR=#000000]XDG_PUBLICSHARE_DIR="$HOME/"[/COLOR]
[COLOR=#000000]XDG_DOCUMENTS_DIR="$HOME/Documents"[/COLOR]
[COLOR=#000000]XDG_MUSIC_DIR="$HOME/"[/COLOR]
[COLOR=#000000]XDG_PICTURES_DIR="$HOME/Pictures"[/COLOR]
[COLOR=#000000]XDG_VIDEOS_DIR="$HOME/"

[/COLOR]Any help?

---

### Post by #&amp;thj^% on 2023-11-24
> **angelosmal2 said:**
> I have the same problem. I tried this solution but when I restart the machine the user-dirs.dirs file is back to this read:

[COLOR=#000000]XDG_DESKTOP_DIR="$HOME/"[/COLOR]
[COLOR=#000000]XDG_DOWNLOAD_DIR="$HOME/Downloads"[/COLOR]
[COLOR=#000000]XDG_TEMPLATES_DIR="$HOME/Templates"[/COLOR]
[COLOR=#000000]XDG_PUBLICSHARE_DIR="$HOME/"[/COLOR]
[COLOR=#000000]XDG_DOCUMENTS_DIR="$HOME/Documents"[/COLOR]
[COLOR=#000000]XDG_MUSIC_DIR="$HOME/"[/COLOR]
[COLOR=#000000]XDG_PICTURES_DIR="$HOME/Pictures"[/COLOR]
[COLOR=#000000]XDG_VIDEOS_DIR="$HOME/"

[/COLOR]Any help?

Lets use nano this time OK?
OK 
```
nano '/home/me/.config/user-dirs.dirs' 
```
Now be sure to change "/me/" to your real users name, and make the change to:
This is the only line you need to change leave the rest as is.
```
XDG_DESKTOP_DIR="$HOME/Desktop"

```
To save if you don't know press {Ctrl + o} then Enter to write the change, then use {Ctrl + x} to leave.
Now Logout and back in, is it any better now?
EDIT Wait i just noticed this in your post "XDG_MUSIC_DIR="$HOME/ " that also needs a change:
```
XDG_MUSIC_DIR="$HOME/Music"
```
and this one as well "XDG_VIDEOS_DIR="$HOME/"

need to read as
```
XDG_VIDEOS_DIR="$HOME/Videos"

```
Now that should work.

---

### Post by angelosmal2 on 2023-11-26
It works! Thank you a lot!

---

### Post by #&amp;thj^% on 2023-11-26
Your Welcome, thanks for the confirmation as well.

---

### Post by angelosmal2 on 2023-11-26
I just noticed that my personal folder is missing from the desktop. I also can't access the desktop, music, or video folders from the file manager. Any idea of what is happening?

---

### Post by #&amp;thj^% on 2023-11-26
> **angelosmal2 said:**
> I just noticed that my personal folder is missing from the desktop. I also can't access the desktop, music, or video folders from the file manager. Any idea of what is happening?

Will you show me what it reads like now please
```
.config/user-dirs.dirs
```

---

### Post by angelosmal2 on 2023-11-26
> **1fallen said:**
> Will you show me what it reads like now please
```
.config/user-dirs.dirs
```

This is the read:

# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run.
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/Downloads"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"

---

### Post by #&amp;thj^% on 2023-11-26
Have you rebooted yet, " All local changes will be retained on the next run."

---

### Post by angelosmal2 on 2023-11-29
> **1fallen said:**
> Have you rebooted yet, " All local changes will be retained on the next run."

I rebooted the system, but the problem came back. The desktop is still showing the same error, mirroring all the files from the home folder. 
user-dirs.dirs file shows the wrong read again:

XDG_DESKTOP_DIR="$HOME/"
XDG_DOWNLOAD_DIR="$HOME/"
XDG_TEMPLATES_DIR="$HOME/"
XDG_PUBLICSHARE_DIR="$HOME/"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/"
XDG_PICTURES_DIR="$HOME/"
XDG_VIDEOS_DIR="$HOME/"

---

### Post by #&amp;thj^% on 2023-11-29
Ok then you have a gremlin, :)  re-create your home desktop folder from a terminal window by running (If the folder exists it will not create a new one):
```
mkdir -p $HOME/Desktop
```
Lets try to run the following to set the XDG_DESKTOP_DIR to the correct setting:
```
xdg-user-dirs-update --set DESKTOP $HOME/Desktop
```

Log out and back in for changes to take effect.
let me know please.

---

### Post by TheFu on 2023-11-30
> **iancompetent2 said:**
>  
Edit: I was using 22.04 and am now using 23.04

Support for 23.04 ends next month. I wouldn't try to fix anything before moving to 23.10. Especially with GUI stuff, things change.  Support for 23.10 ends in June, so you'll need to move to 24.04 sometime between April and June.  I'd lean towards early June so early release issues are found by others, not me. ;)  I want a stable system more than almost anything else. "New" doesn't really appeal to me.  YMMV.

---

### Post by angelosmal2 on 2023-11-30
> **1fallen said:**
> Ok then you have a gremlin, :)  re-create your home desktop folder from a terminal window by running (If the folder exists it will not create a new one):
```
mkdir -p $HOME/Desktop
```
Lets try to run the following to set the XDG_DESKTOP_DIR to the correct setting:
```
xdg-user-dirs-update --set DESKTOP $HOME/Desktop
```

Log out and back in for changes to take effect.
let me know please.

It doesn't seem to be working. The first command produces the following error:
mkdir: no se puede efectuar `stat' sobre «/home/angel/Desktop»: Demasiados niveles de enlaces simbólicos (cannot stat «/home/angel/Desktop»: too many symbolic links)

---

### Post by TheFu on 2023-11-30
> **angelosmal2 said:**
> It doesn't seem to be working. The first command produces the following error:
mkdir: no se puede efectuar `stat' sobre «/home/angel/Desktop»: Demasiados niveles de enlaces simbólicos (cannot stat «/home/angel/Desktop»: too many symbolic links)

Did you happen to create circular symlinks?

---

### Post by energie-fan on 2023-12-08
In my case the re-mirroring stops after deinstalling Okular.

---

