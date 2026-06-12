---
title: "Mythtv - icons fetch problem.."
date: 2007-02-10
forum: General Help
---

### Post by tiger.woods on 2007-02-10
I'm trying to use the Perl script in the docs to pull in icons for Mythtv and it's not finishing or it's bombing, not sure which? 

It appears to ID the needed icons but doesn't insert them into the DB or download them.  It did retrieve some icons, 5 out of about 200... can someone explain how this process supposed to work maybe I can try to identify what happened or didn't happen.

Thanks, 

Stored       AETV in  /tmp/icons/AETV.url
Stored        AMC in   /tmp/icons/AMC.url
Stored     ANIMAL in /tmp/icons/ANIMAL.url
Stored       BBCA in  /tmp/icons/BBCA.url
Stored        BET in   /tmp/icons/BET.url
Stored      BLOOM in /tmp/icons/BLOOM.url
Stored      BRAVO in /tmp/icons/BRAVO.url
Stored       CMTV in  /tmp/icons/CMTV.url
Stored       CNBC in  /tmp/icons/CNBC.url
Stored        CNN in   /tmp/icons/CNN.url
Stored       CNNH in  /tmp/icons/CNNH.url
Stored     COMEDY in /tmp/icons/COMEDY.url
Stored      COURT in /tmp/icons/COURT.url
Stored      CSPAN in /tmp/icons/CSPAN.url
Stored     CSPAN2 in /tmp/icons/CSPAN2.url
Stored       DISN in  /tmp/icons/DISN.url
Stored      DISNP in /tmp/icons/DISNP.url
Stored        DSC in   /tmp/icons/DSC.url
Stored        DTN in   /tmp/icons/DTN.url
Stored     ENCORE in /tmp/icons/ENCORE.url
Stored    ENCOREP in /tmp/icons/ENCOREP.url
Stored       ESPN in  /tmp/icons/ESPN.url
Stored      ESPN2 in /tmp/icons/ESPN2.url
Stored     ESPNCL in /tmp/icons/ESPNCL.url
Stored    ESPNEWS in /tmp/icons/ESPNEWS.url
Stored        ETV in   /tmp/icons/ETV.url
Stored        FAM in   /tmp/icons/FAM.url
Stored        FNC in   /tmp/icons/FNC.url
Stored       FOOD in  /tmp/icons/FOOD.url
Stored         FX in    /tmp/icons/FX.url
Stored       GOLF in  /tmp/icons/GOLF.url
Stored        GSN in   /tmp/icons/GSN.url
Stored     HALMRK in /tmp/icons/HALMRK.url
Stored        HBO in   /tmp/icons/HBO.url
Stored       HBO2 in  /tmp/icons/HBO2.url
Stored       HBOF in  /tmp/icons/HBOF.url
Stored       HBOP in  /tmp/icons/HBOP.url
Stored     HBOSIG in /tmp/icons/HBOSIG.url
Stored       HGTV in  /tmp/icons/HGTV.url
Stored    HISTORY in /tmp/icons/HISTORY.url
Stored        HSN in   /tmp/icons/HSN.url
Stored      ISATE in /tmp/icons/ISATE.url
Stored       KABC in  /tmp/icons/KABC.url
Stored       KCAL in  /tmp/icons/KCAL.url
Stored       KCBS in  /tmp/icons/KCBS.url
Stored     KCBSDT in /tmp/icons/KCBSDT.url
Stored       KCET in  /tmp/icons/KCET.url
Stored       KCNC in  /tmp/icons/KCNC.url
Stored       KCOP in  /tmp/icons/KCOP.url
Stored       KDFW in  /tmp/icons/KDFW.url
Stored       KDVR in  /tmp/icons/KDVR.url
Stored        KGO in   /tmp/icons/KGO.url
Stored       KMGH in  /tmp/icons/KMGH.url
Stored       KNBC in  /tmp/icons/KNBC.url
Stored       KNTV in  /tmp/icons/KNTV.url
Stored       KPIX in  /tmp/icons/KPIX.url
Stored       KRMA in  /tmp/icons/KRMA.url
Stored       KTLA in  /tmp/icons/KTLA.url
Stored       KTTV in  /tmp/icons/KTTV.url
Stored       KTVD in  /tmp/icons/KTVD.url
Stored       KTVT in  /tmp/icons/KTVT.url
Stored       KTVU in  /tmp/icons/KTVU.url
Stored       KUSA in  /tmp/icons/KUSA.url
Stored       KWGN in  /tmp/icons/KWGN.url
Stored       KXAS in  /tmp/icons/KXAS.url
Stored       KYNE in  /tmp/icons/KYNE.url
Stored       LIFE in  /tmp/icons/LIFE.url
Stored        MAX in   /tmp/icons/MAX.url
Stored       MAXP in  /tmp/icons/MAXP.url
Stored      MSNBC in /tmp/icons/MSNBC.url
Stored        MTV in   /tmp/icons/MTV.url
Stored       MTV2 in  /tmp/icons/MTV2.url
Stored        NGC in   /tmp/icons/NGC.url
Stored        NIK in   /tmp/icons/NIK.url
Stored       NIKP in  /tmp/icons/NIKP.url
Stored    OUTDOOR in /tmp/icons/OUTDOOR.url
Stored        QVC in   /tmp/icons/QVC.url
Stored      SCIFI in /tmp/icons/SCIFI.url
Stored       SHOW in  /tmp/icons/SHOW.url
Stored      SHOWP in /tmp/icons/SHOWP.url
Stored      SPEED in /tmp/icons/SPEED.url
Stored    SPIKETV in /tmp/icons/SPIKETV.url
Stored      STARZ in /tmp/icons/STARZ.url
Stored     STARZP in /tmp/icons/STARZP.url
Stored        TBN in   /tmp/icons/TBN.url
Stored        TBS in   /tmp/icons/TBS.url
Stored        TCM in   /tmp/icons/TCM.url
Stored        TLC in   /tmp/icons/TLC.url
Stored        TMC in   /tmp/icons/TMC.url
Stored       TMCP in  /tmp/icons/TMCP.url
Stored        TNT in   /tmp/icons/TNT.url
Stored       TOON in  /tmp/icons/TOON.url
Stored       TRAV in  /tmp/icons/TRAV.url
Stored       TVGC in  /tmp/icons/TVGC.url
Stored     TVLAND in /tmp/icons/TVLAND.url
Stored        TWC in   /tmp/icons/TWC.url
Stored        UNI in   /tmp/icons/UNI.url
Stored       UNIP in  /tmp/icons/UNIP.url
Stored        USA in   /tmp/icons/USA.url
Stored     VERSUS in /tmp/icons/VERSUS.url
Stored        VH1 in   /tmp/icons/VH1.url
Stored       WABC in  /tmp/icons/WABC.url
Stored       WAGA in  /tmp/icons/WAGA.url
Stored       WBBM in  /tmp/icons/WBBM.url
Stored       WCBS in  /tmp/icons/WCBS.url
Stored     WCBSDT in /tmp/icons/WCBSDT.url
Stored         WE in    /tmp/icons/WE.url
Stored       WFAA in  /tmp/icons/WFAA.url
Stored       WFLD in  /tmp/icons/WFLD.url
Stored       WGCL in  /tmp/icons/WGCL.url
Stored        WGN in   /tmp/icons/WGN.url
Stored     WGNSAT in /tmp/icons/WGNSAT.url
Stored       WGTV in  /tmp/icons/WGTV.url
Stored        WLS in   /tmp/icons/WLS.url
Stored       WMAQ in  /tmp/icons/WMAQ.url
Stored       WNBC in  /tmp/icons/WNBC.url
Stored       WNET in  /tmp/icons/WNET.url
Stored       WNYW in  /tmp/icons/WNYW.url
Stored       WPIX in  /tmp/icons/WPIX.url
Stored        WSB in   /tmp/icons/WSB.url
Stored       WTTW in  /tmp/icons/WTTW.url
Stored       WWOR in  /tmp/icons/WWOR.url
Stored       WXIA in  /tmp/icons/WXIA.url
Generating iconmap.xml...
mythtv@myth:~$ mythfilldatabase --import-icon-map iconmap.xml --update-icon-map
2007-02-10 09:03:45.105 Using runtime prefix = /usr/local
2007-02-10 09:03:45.142 New DB connection, total: 1
2007-02-10 09:03:45.190 Connected to database 'mythconverg' at host: 192.168.1.111
2007-02-10 09:03:45.198 mythfilldatabase: Listings Download Started
Importing icon mapping from iconmap.xml...
2007-02-10 09:03:45.219 New DB connection, total: 2
2007-02-10 09:03:45.258 Connected to database 'mythconverg' at host: 192.168.1.111
2007-02-10 09:03:45.260 New DB connection, total: 3
2007-02-10 09:03:45.299 Connected to database 'mythconverg' at host: 192.168.1.111
2007-02-10 09:03:45.301 New DB connection, total: 4
2007-02-10 09:03:45.338 Connected to database 'mythconverg' at host: 192.168.1.111
2007-02-10 09:03:45.403 New DB connection, total: 5
2007-02-10 09:03:45.443 Connected to database 'mythconverg' at host: 192.168.1.111
2007-02-10 09:03:45.448 Updating icons for sourceid: 1
2007-02-10 09:03:45.451 Updating icons for sourceid: 2
2007-02-10 09:03:45.454 Marking repeats.
2007-02-10 09:03:45.710     Found 12
2007-02-10 09:03:45.711 Unmarking new episode rebroadcast repeats.
2007-02-10 09:03:45.968     Found 0
2007-02-10 09:03:46.005
===============================================================
| Attempting to contact the master backend for rescheduling.  |
| If the master is not running, rescheduling will happen when |
| the master backend is restarted.                            |
===============================================================
2007-02-10 09:03:46.009 Connecting to backend server: 192.168.1.111:6543 (try 1 of 5)
2007-02-10 09:03:46.010 Using protocol version 32
2007-02-10 09:03:46.015 mythfilldatabase run complete.

---

