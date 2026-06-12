---
title: "Move a file to another disk"
date: 2007-07-09
forum: General Help
---

### Post by lukanikos on 2007-07-09
I am trying to move an avi movie from the desktop to another disk and i get this messege:

```

Error while copying to "/media/disk-2/movies".
You do not have permissions to write to this folder.
```

I have unzipped the file from a hard drive into the desktop of ubuntu different disk drive.
When I try to send it back by drag and drop I get the message above.

Also when I try to delete the .rar files from where  I have unzipped the .avi  file ...the move to trash option does not exist so I drag an drop and I get this message:

```
Cannot move items to trash, do you want to delete them immediately?
None of the 1 selected items can be moved to trash


```

I click on delete and then I get this message:
```

Unable to move to trash:
Read only file system
```

Why is this happening?

The .rar files are in a defferent  hard disk and the .avi  file on my desktop and I have also to tell you that I have another drive with windows xp on...

Please help

---

### Post by stchman on 2007-07-09
> **lukanikos said:**
> I am trying to move an avi movie from the desktop to another disk and i get this messege:

```

Error while copying to "/media/disk-2/movies".
You do not have permissions to write to this folder.
```

I have unzipped the file from a hard drive into the desktop of ubuntu different disk drive.
When I try to send it back by drag and drop I get the message above.

Also when I try to delete the .rar files from where  I have unzipped the .avi  file ...the move to trash option does not exist so I drag an drop and I get this message:

```
Cannot move items to trash, do you want to delete them immediately?
None of the 1 selected items can be moved to trash


```

I click on delete and then I get this message:
```

Unable to move to trash:
Read only file system
```

Why is this happening?

The .rar files are in a defferent  hard disk and the .avi  file on my desktop and I have also to tell you that I have another drive with windows xp on...

Please help

Try this

sudo chown -R <your_name>:<your_name> /media/disk-2
sudo chmod -R 755 /media/disk-2

This will allow you to now own the drive and allow you to write to the drive.

---

### Post by lukanikos on 2007-07-09
THAT'S WHAT i GET

```
lukanikos@lukanikos-desktop:~$ sudo chown -R lukanikos:lukanikos /media/disk-2
Password:
chown: cannot access `/media/disk-2': No such file or directory
lukanikos@lukanikos-desktop:~$ sudo chown -R <lukanikos>:<lukanikos> /media/disk-2
bash: lukanikos: No such file or directory

```

Maybe is just  disk   and not disk-2

---

### Post by lukanikos on 2007-07-09
Worked with just "disk"   I think??

```
ivx.hebsub.kobiko/goal.2.Living.the.Dream.tvrip.divx.hebsub.kobiko.avi': Read-only file system
chown: changing ownership of `/media/disk/movies/goal.2.living.the.dream.tvrip.divx.hebsub.kobiko': Read-only file system
chown: changing ownership of `/media/disk/movies/jumpin/sph-jumpin.avi': Read-only file system
chown: changing ownership of `/media/disk/movies/jumpin': Read-only file system
chown: changing ownership of `/media/disk/movies/the_long_weekend_uploaded_by_iliasb00-liakos/g3twarez.com.URL': Read-only file system
chown: changing ownership of `/media/disk/movies/the_long_weekend_uploaded_by_iliasb00-liakos/READ THIS CAREFULLY!!!.txt': Read-only file system
chown: changing ownership of `/media/disk/movies/the_long_weekend_uploaded_by_iliasb00-liakos/the long weekend.avi': Read-only file system
chown: changing ownership of `/media/disk/movies/the_long_weekend_uploaded_by_iliasb00-liakos': Read-only file system
chown: changing ownership of `/media/disk/movies/thothf-01/THE_OTHER_HALF-01.avi': Read-only file system
chown: changing ownership of `/media/disk/movies/thothf-01': Read-only file system
chown: changing ownership of `/media/disk/movies/yokboylebisey-pandion/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY.avi': Read-only file system
chown: changing ownership of `/media/disk/movies/yokboylebisey-pandion/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY.Eng.srt': Read-only file system
chown: changing ownership of `/media/disk/movies/yokboylebisey-pandion/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY.Nl.srt': Read-only file system
chown: changing ownership of `/media/disk/movies/yokboylebisey-pandion/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY.Tr.srt': Read-only file system
chown: changing ownership of `/media/disk/movies/yokboylebisey-pandion/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY/Posters/affiche.jpg': Read-only file system
chown: changing ownership of `/media/disk/movies/yokboylebisey-pandion/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY/Posters/KaenaLaProphetie.jpg': Read-only file system
chown: changing ownership of `/media/disk/movies/yokboylebisey-pandion/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY/Posters/kaena_affiche_02.jpg': Read-only file system
chown: changing ownership of `/media/disk/movies/yokboylebisey-pandion/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY/Posters/Kaena_the_prophecy-fr-kamui.jpg': Read-only file system
chown: changing ownership of `/media/disk/movies/yokboylebisey-pandion/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY/Posters/Thumbs.db': Read-only file system
chown: changing ownership of `/media/disk/movies/yokboylebisey-pandion/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY/Posters/Wallpaper_01.jpg': Read-only file system
chown: changing ownership of `/media/disk/movies/yokboylebisey-pandion/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY/Posters/Wallpaper_04.jpg': Read-only file system
chown: changing ownership of `/media/disk/movies/yokboylebisey-pandion/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY/Posters': Read-only file system
chown: changing ownership of `/media/disk/movies/yokboylebisey-pandion/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY': Read-only file system
chown: changing ownership of `/media/disk/movies/yokboylebisey-pandion': Read-only file system
chown: changing ownership of `/media/disk/movies': Read-only file system
chown: changing ownership of `/media/disk/pagefile.sys': Read-only file system
chown: changing ownership of `/media/disk/RECYCLER/S-1-5-21-1343024091-527237240-725345543-1003/desktop.ini': Read-only file system
chown: changing ownership of `/media/disk/RECYCLER/S-1-5-21-1343024091-527237240-725345543-1003/INFO2': Read-only file system
chown: changing ownership of `/media/disk/RECYCLER/S-1-5-21-1343024091-527237240-725345543-1003': Read-only file system
chown: changing ownership of `/media/disk/RECYCLER/S-1-5-21-1343024091-527237240-725345543-500/desktop.ini': Read-only file system
chown: changing ownership of `/media/disk/RECYCLER/S-1-5-21-1343024091-527237240-725345543-500/INFO2': Read-only file system
chown: changing ownership of `/media/disk/RECYCLER/S-1-5-21-1343024091-527237240-725345543-500': Read-only file system
chown: changing ownership of `/media/disk/RECYCLER': Read-only file system
chown: changing ownership of `/media/disk/software/09.12/05042008.key': Read-only file system
chown: changing ownership of `/media/disk/software/09.12': Read-only file system
chown: changing ownership of `/media/disk/software/09.12.rar': Read-only file system
chown: changing ownership of `/media/disk/software/FlashGet_v1.80_Final___New_Tweaker/FlashGet v1.80 Final + New Tweaker/AppzstocK.NFO': Read-only file system
chown: changing ownership of `/media/disk/software/FlashGet_v1.80_Final___New_Tweaker/FlashGet v1.80 Final + New Tweaker/fg180en.exe': Read-only file system
chown: changing ownership of `/media/disk/software/FlashGet_v1.80_Final___New_Tweaker/FlashGet v1.80 Final + New Tweaker/Universal_Tweaker_1.1_by_MaRKuS_TH-DJM/AppzstocK.NFO': Read-only file system
chown: changing ownership of `/media/disk/software/FlashGet_v1.80_Final___New_Tweaker/FlashGet v1.80 Final + New Tweaker/Universal_Tweaker_1.1_by_MaRKuS_TH-DJM/FlashGet Patch.exe': Read-only file system
chown: changing ownership of `/media/disk/software/FlashGet_v1.80_Final___New_Tweaker/FlashGet v1.80 Final + New Tweaker/Universal_Tweaker_1.1_by_MaRKuS_TH-DJM/snd.nfo': Read-only file system
chown: changing ownership of `/media/disk/software/FlashGet_v1.80_Final___New_Tweaker/FlashGet v1.80 Final + New Tweaker/Universal_Tweaker_1.1_by_MaRKuS_TH-DJM/www.appzstock.com.url': Read-only file system
chown: changing ownership of `/media/disk/software/FlashGet_v1.80_Final___New_Tweaker/FlashGet v1.80 Final + New Tweaker/Universal_Tweaker_1.1_by_MaRKuS_TH-DJM': Read-only file system
chown: changing ownership of `/media/disk/software/FlashGet_v1.80_Final___New_Tweaker/FlashGet v1.80 Final + New Tweaker/www.appzstock.com.url': Read-only file system
chown: changing ownership of `/media/disk/software/FlashGet_v1.80_Final___New_Tweaker/FlashGet v1.80 Final + New Tweaker': Read-only file system
chown: changing ownership of `/media/disk/software/FlashGet_v1.80_Final___New_Tweaker': Read-only file system
chown: changing ownership of `/media/disk/software/FlashGet_v1.80_Final___New_Tweaker.rar': Read-only file system
chown: changing ownership of `/media/disk/software/gardens_ruz/data1.cab': Read-only file system
chown: changing ownership of `/media/disk/software/gardens_ruz/data1.hdr': Read-only file system
chown: changing ownership of `/media/disk/software/gardens_ruz/data2.cab': Read-only file system
chown: changing ownership of `/media/disk/software/gardens_ruz/engine32.cab': Read-only file system
chown: changing ownership of `/media/disk/software/gardens_ruz/layout.bin': Read-only file system
chown: changing ownership of `/media/disk/software/gardens_ruz/Profile.plan': Read-only file system
chown: changing ownership of `/media/disk/software/gardens_ruz/readme.nfo': Read-only file system
chown: changing ownership of `/media/disk/software/gardens_ruz/setup.exe': Read-only file system
chown: changing ownership of `/media/disk/software/gardens_ruz/setup.ibt': Read-only file system
chown: changing ownership of `/media/disk/software/gardens_ruz/setup.ini': Read-only file system
chown: changing ownership of `/media/disk/software/gardens_ruz/setup.inx': Read-only file system
chown: changing ownership of `/media/disk/software/gardens_ruz/setup.isn': Read-only file system
chown: changing ownership of `/media/disk/software/gardens_ruz/shock.nfo': Read-only file system
chown: changing ownership of `/media/disk/software/gardens_ruz': Read-only file system
chown: changing ownership of `/media/disk/software/KG/file_id.diz': Read-only file system
chown: changing ownership of `/media/disk/software/KG/keygen.exe': Read-only file system
chown: changing ownership of `/media/disk/software/KG/virility.nfo': Read-only file system
chown: changing ownership of `/media/disk/software/KG': Read-only file system
chown: changing ownership of `/media/disk/software/KG.zip': Read-only file system
chown: changing ownership of `/media/disk/software/mx_2.0.0.8042.exe': Read-only file system
chown: changing ownership of `/media/disk/software/mx_2.0.1.1276.exe': Read-only file system
chown: changing ownership of `/media/disk/software/NeroDigitalPro-3.1.0.16.exe': Read-only file system
chown: changing ownership of `/media/disk/software/NeroHacked.txt': Read-only file system
chown: changing ownership of `/media/disk/software/NeroNET-1.2.0.2.exe': Read-only file system
chown: changing ownership of `/media/disk/software/panic__at_the_disco_-_a_fever_you_can_t_sweat_out.zip': Read-only file system
chown: changing ownership of `/media/disk/software/rapget126.rar': Read-only file system
chown: changing ownership of `/media/disk/software/RapidShare-Killer-AIO.exe': Read-only file system
chown: changing ownership of `/media/disk/software/SageTV v5.0.4.92/Crack/digerati.nfo': Read-only file system
chown: changing ownership of `/media/disk/software/SageTV v5.0.4.92/Crack/SageTV.exe': Read-only file system
chown: changing ownership of `/media/disk/software/SageTV v5.0.4.92/Crack/SageTVService.exe': Read-only file system
chown: changing ownership of `/media/disk/software/SageTV v5.0.4.92/Crack': Read-only file system
chown: changing ownership of `/media/disk/software/SageTV v5.0.4.92/SageTVClient_V5_0_4Setup.exe': Read-only file system
chown: changing ownership of `/media/disk/software/SageTV v5.0.4.92': Read-only file system
chown: changing ownership of `/media/disk/software/SageTV_v5.0.4.92.rar': Read-only file system
chown: changing ownership of `/media/disk/software/TM/crack/FFF.NFO': Read-only file system
chown: changing ownership of `/media/disk/software/TM/crack/FILE_ID.DIZ': Read-only file system
chown: changing ownership of `/media/disk/software/TM/crack/TransMac.exe': Read-only file system
chown: changing ownership of `/media/disk/software/TM/crack': Read-only file system
chown: changing ownership of `/media/disk/software/TM/tmsetup.exe': Read-only file system
chown: changing ownership of `/media/disk/software/TM': Read-only file system
chown: changing ownership of `/media/disk/software/transmac_7.5__k__ed.zip': Read-only file system
chown: changing ownership of `/media/disk/software/Typing Master Pro 7.0 EN/Latest_Downloads.html': Read-only file system
chown: changing ownership of `/media/disk/software/Typing Master Pro 7.0 EN/Read_Me.txt': Read-only file system
chown: changing ownership of `/media/disk/software/Typing Master Pro 7.0 EN/TypingMasterENG.exe': Read-only file system
chown: changing ownership of `/media/disk/software/Typing Master Pro 7.0 EN/XshareX.info.nfo': Read-only file system
chown: changing ownership of `/media/disk/software/Typing Master Pro 7.0 EN': Read-only file system
chown: changing ownership of `/media/disk/software/typing_master_pro_7.0_en.rar': Read-only file system
chown: changing ownership of `/media/disk/software/USDv134b7.rar': Read-only file system
chown: changing ownership of `/media/disk/software/winzip110.exe': Read-only file system
chown: changing ownership of `/media/disk/software/WinZip_Pro_v11.0.7313_inc.KG.zip': Read-only file system
chown: changing ownership of `/media/disk/software': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/MountPointManagerRemoteDatabase': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/tracking.log': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032705.ini': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032706.nfo': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032737.ini': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032844.ini': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032894.ini': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032895.ini': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032896.ini': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032897.ini': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032898.nfo': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032899.ini': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032900.nfo': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032901.ini': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032902.ini': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032903.nfo': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032904.ini': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032905.nfo': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032906.ini': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032907.nfo': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032908.nfo': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032909.ini': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032910.nfo': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032911.ini': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/change.log.1': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/RestorePointSize': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032934.ini': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032940.nfo': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032941.srt': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032942.srt': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032943.srt': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032944.nfo': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032945.srt': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032946.srt': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032947.srt': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032948.srt': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032949.srt': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032950.srt': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032951.srt': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032952.srt': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032953.srt': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032954.srt': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032955.srt': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032956.srt': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032957.srt': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032958.srt': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032959.srt': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032960.srt': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032961.nfo': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032967.srt': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032968.srt': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/change.log.1': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/RestorePointSize': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP314/A0033059.ini': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP314/change.log.1': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP314/RestorePointSize': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP314': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP316/A0033091.ini': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP316/change.log.1': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP316/RestorePointSize': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP316': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP317/A0033116.ini': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP317/change.log.1': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP317/RestorePointSize': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP317': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP321/A0033146.ini': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP321/change.log.1': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP321/RestorePointSize': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP321': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP322/A0033212.ini': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP322/change.log.1': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP322/RestorePointSize': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP322': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP324/change.log.1': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP324/RestorePointSize': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP324': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP327/change.log.1': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP327/RestorePointSize': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP327': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP328/A0035425.ini': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP328/change.log.1': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP328/RestorePointSize': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP328': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP329/A0035614.ini': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP329/change.log.1': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP329/RestorePointSize': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP329': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP330/A0035730.ini': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP330/change.log.1': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP330/RestorePointSize': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP330': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP331/A0035941.ini': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP331/change.log.1': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP331/RestorePointSize': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP331': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP334/A0039660.ini': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP334/change.log.1': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP334/RestorePointSize': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP334': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP335/A0043070.ini': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP335/change.log.1': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP335/change.log.2': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP335/RestorePointSize': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP335': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP336/change.log.1': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP336/RestorePointSize': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP336': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP337/change.log.1': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP337/RestorePointSize': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP337': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP338/change.log.1': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP338/RestorePointSize': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP338': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP339/change.log.1': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP339/RestorePointSize': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP339': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP340/change.log.1': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP340/RestorePointSize': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP340': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP341/change.log.1': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP341/RestorePointSize': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP341': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP342/change.log.1': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP342/RestorePointSize': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP342': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP343/change.log.1': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP343/RestorePointSize': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP343': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP345/A0045138.ini': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP345/change.log': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP345': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}': Read-only file system
chown: changing ownership of `/media/disk/System Volume Information': Read-only file system
chown: changing ownership of `/media/disk': Read-only file system
lukanikos@lukanikos-desktop:~$ 
```

---

### Post by lukanikos on 2007-07-09
that's what came up Re: Move a file to another disk
Code:

---

### Post by lukanikos on 2007-07-09
```
chmod: changing permissions of `/media/disk/movies/bib_dhoodle/Latest Downloads.html': Read-only file system
chmod: changing permissions of `/media/disk/movies/bib_dhoodle/Read Me.txt': Read-only file system
chmod: changing permissions of `/media/disk/movies/over_the_hedge': Read-only file system
chmod: changing permissions of `/media/disk/movies/over_the_hedge/OVER_THE_HEDGE.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/pethainontas_sthn_athina': Read-only file system
chmod: changing permissions of `/media/disk/movies/pethainontas_sthn_athina/Pethainontas sthn athina': Read-only file system
chmod: changing permissions of `/media/disk/movies/pethainontas_sthn_athina/Pethainontas sthn athina/Pethainontas sthn athina.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/r.e.d.d': Read-only file system
chmod: changing permissions of `/media/disk/movies/r.e.d.d/Return.In.Red.2007.DVDRip.XviD-NEPTUNE.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/red.mercury.2005.dvdscr.xvid-nascent': Read-only file system
chmod: changing permissions of `/media/disk/movies/red.mercury.2005.dvdscr.xvid-nascent/Red.Mercury.2005.DVDSCR.XviD-NascenT': Read-only file system
chmod: changing permissions of `/media/disk/movies/red.mercury.2005.dvdscr.xvid-nascent/Red.Mercury.2005.DVDSCR.XviD-NascenT/!!! READ ME !!!!.txt': Read-only file system
chmod: changing permissions of `/media/disk/movies/red.mercury.2005.dvdscr.xvid-nascent/Red.Mercury.2005.DVDSCR.XviD-NascenT/nas-mercury.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/red.mercury.2005.dvdscr.xvid-nascent/Red.Mercury.2005.DVDSCR.XviD-NascenT/WarezTurka.NET.url': Read-only file system
chmod: changing permissions of `/media/disk/movies/drw.207': Read-only file system
chmod: changing permissions of `/media/disk/movies/drw.207/Doctor Who 2006 2x07 The Idiot\'s Lantern.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0312': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0312/lost.312.hdtv-caph.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0312/lost.312.hdtv-caph.srt': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/a_tale_of_survival': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/a_tale_of_survival/A_Tale_of_Survival.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/destination_lost': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/destination_lost/Destination_lost.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/dharma_initiative_film': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/dharma_initiative_film/Dharma_Initiative_Film.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/dharma_initiative_film/Dharma_Initiative_Film.srt': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0307': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0307/L0307.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0308': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0308/Lost - 3x08 - Flashes Before Your Eyes.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0308/Lost - 3x08 - Flashes Before Your Eyes.srt': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0309': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0309/lost.309.hdtv.xvid-notv.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0309/lost.309.hdtv.xvid-notv.srt': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0310': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0310/lost.310.hdtv.xvid-notv.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0310/lost.310.hdtv.xvid-notv.srt': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0311': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0311/L0311.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0311/L0311.srt': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0313': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0313/lost.313.hdtv-caph.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0313/lost.313.hdtv-caph.srt': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0314': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0314/L.0314.hdtv-caph.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0314/L.0314.hdtv-caph.srt': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0315': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0315/lost.315.hdtv.xvid-sorny.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0315/lost.315.hdtv.xvid-sorny.srt': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0316': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0316/Lost season 03 Episode 16-caph.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0316/Lost season 03 Episode 16-caph.srt': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0317': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0317/Lost season 0317.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0317/Lost season 0317.srt': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0318': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0318/Lost season 03 Episode 18-caph.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0318/Lost season 03 Episode 18-caph.srt': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0319': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0319/LOST.s03e19.HDTV.XViD-xor.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0319/LOST.s03e19.HDTV.XViD-xor.srt': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0320': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0320/Lost season 03 Episode 20 The Man Behind the Curtain-caph.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0320/Lost season 03 Episode 20 The Man Behind the Curtain-caph.srt': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0322': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0322/lost.322-caph.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost 0322/lost.322-caph.srt': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost the answers': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost the answers/lost.s03.the.answers.hdtv.xvid-xor.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost the answers/lost.s03.the.answers.hdtv.xvid-xor.srt': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost.uncovered.behind.the.scenes.video': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost.uncovered.behind.the.scenes.video/Lost.Uncovered.WS.PDTV.XviD-CaRaT.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost0321': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost0321/Lost [03x21] Greatest Hits.www.odcinki.org.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/lost0321/Lost [03x21] Greatest Hits.www.odcinki.org.srt': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/reckoning': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/reckoning/Reckoning.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/revelation': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/revelation/Revelation.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/the_journey': Read-only file system
chmod: changing permissions of `/media/disk/movies/fany/the_journey/The_Journey.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/gamerz.2005.dvdrip': Read-only file system
chmod: changing permissions of `/media/disk/movies/gamerz.2005.dvdrip/li-tt-le.gi-rls.ts.xvid': Read-only file system
chmod: changing permissions of `/media/disk/movies/gamerz.2005.dvdrip/li-tt-le.gi-rls.ts.xvid/Daddys.Little.Girls.TS.XviD-SenTeLLo.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/gamerz.2005.dvdrip/vmt-gamerz-xvid.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/gamerz.2005.dvdrip/vmt-gamerz-xvid.nfo': Read-only file system
chmod: changing permissions of `/media/disk/movies/goal.2.living.the.dream.tvrip.divx.hebsub.kobiko': Read-only file system
chmod: changing permissions of `/media/disk/movies/goal.2.living.the.dream.tvrip.divx.hebsub.kobiko/goal.2.Living.the.Dream.tvrip.divx.hebsub.kobiko.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/jumpin': Read-only file system
chmod: changing permissions of `/media/disk/movies/jumpin/sph-jumpin.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/the_long_weekend_uploaded_by_iliasb00-liakos': Read-only file system
chmod: changing permissions of `/media/disk/movies/the_long_weekend_uploaded_by_iliasb00-liakos/g3twarez.com.URL': Read-only file system
chmod: changing permissions of `/media/disk/movies/the_long_weekend_uploaded_by_iliasb00-liakos/READ THIS CAREFULLY!!!.txt': Read-only file system
chmod: changing permissions of `/media/disk/movies/the_long_weekend_uploaded_by_iliasb00-liakos/the long weekend.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/thothf-01': Read-only file system
chmod: changing permissions of `/media/disk/movies/thothf-01/THE_OTHER_HALF-01.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/yokboylebisey-pandion': Read-only file system
chmod: changing permissions of `/media/disk/movies/yokboylebisey-pandion/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY': Read-only file system
chmod: changing permissions of `/media/disk/movies/yokboylebisey-pandion/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY.avi': Read-only file system
chmod: changing permissions of `/media/disk/movies/yokboylebisey-pandion/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY.Eng.srt': Read-only file system
chmod: changing permissions of `/media/disk/movies/yokboylebisey-pandion/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY.Nl.srt': Read-only file system
chmod: changing permissions of `/media/disk/movies/yokboylebisey-pandion/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY.Tr.srt': Read-only file system
chmod: changing permissions of `/media/disk/movies/yokboylebisey-pandion/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY/Posters': Read-only file system
chmod: changing permissions of `/media/disk/movies/yokboylebisey-pandion/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY/Posters/affiche.jpg': Read-only file system
chmod: changing permissions of `/media/disk/movies/yokboylebisey-pandion/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY/Posters/KaenaLaProphetie.jpg': Read-only file system
chmod: changing permissions of `/media/disk/movies/yokboylebisey-pandion/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY/Posters/kaena_affiche_02.jpg': Read-only file system
chmod: changing permissions of `/media/disk/movies/yokboylebisey-pandion/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY/Posters/Kaena_the_prophecy-fr-kamui.jpg': Read-only file system
chmod: changing permissions of `/media/disk/movies/yokboylebisey-pandion/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY/Posters/Thumbs.db': Read-only file system
chmod: changing permissions of `/media/disk/movies/yokboylebisey-pandion/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY/Posters/Wallpaper_01.jpg': Read-only file system
chmod: changing permissions of `/media/disk/movies/yokboylebisey-pandion/Kaena.the.Prophecy.2004.LIMITED.DVRip.XviD-VERITY/Posters/Wallpaper_04.jpg': Read-only file system
chmod: changing permissions of `/media/disk/pagefile.sys': Read-only file system
chmod: changing permissions of `/media/disk/RECYCLER': Read-only file system
chmod: changing permissions of `/media/disk/RECYCLER/S-1-5-21-1343024091-527237240-725345543-1003': Read-only file system
chmod: changing permissions of `/media/disk/RECYCLER/S-1-5-21-1343024091-527237240-725345543-1003/desktop.ini': Read-only file system
chmod: changing permissions of `/media/disk/RECYCLER/S-1-5-21-1343024091-527237240-725345543-1003/INFO2': Read-only file system
chmod: changing permissions of `/media/disk/RECYCLER/S-1-5-21-1343024091-527237240-725345543-500': Read-only file system
chmod: changing permissions of `/media/disk/RECYCLER/S-1-5-21-1343024091-527237240-725345543-500/desktop.ini': Read-only file system
chmod: changing permissions of `/media/disk/RECYCLER/S-1-5-21-1343024091-527237240-725345543-500/INFO2': Read-only file system
chmod: changing permissions of `/media/disk/software': Read-only file system`/media/disk/software/FlashGet_v1.80_Final___New_Tweaker.rar': Read-only file system
chmod: changing permissions of `/media/disk/software/gardens_ruz': Read-only file system
chmod: changing permissions of `/media/disk/software/gardens_ruz/data1.cab': Read-only file system
chmod: changing permissions of `/media/disk/software/gardens_ruz/data1.hdr': Read-only file system
chmod: changing permissions of `/media/disk/software/gardens_ruz/data2.cab': Read-only file system
chmod: changing permissions of `/media/disk/software/gardens_ruz/engine32.cab': Read-only file system
chmod: changing permissions of `/media/disk/software/gardens_ruz/layout.bin': Read-only file system
chmod: changing permissions of `/media/disk/software/gardens_ruz/Profile.plan': Read-only file system
chmod: changing permissions of `/media/disk/software/gardens_ruz/readme.nfo': Read-only file system
chmod: changing permissions of `/media/disk/software/gardens_ruz/setup.exe': Read-only file system
chmod: changing permissions of `/media/disk/software/gardens_ruz/setup.ibt': Read-only file system
chmod: changing permissions of `/media/disk/software/gardens_ruz/setup.ini': Read-only file system
chmod: changing permissions of `/media/disk/software/gardens_ruz/setup.inx': Read-only file system
chmod: changing permissions of `/media/disk/software/gardens_ruz/setup.isn': Read-only file system
chmod: changing permissions of `/media/disk/software/gardens_ruz/shock.nfo': Read-only file system
chmod: changing permissions of `/media/disk/software/KG': Read-only file system
chmod: changing permissions of `/media/disk/software/KG/file_id.diz': Read-only file system
chmod: changing permissions of `/media/disk/software/KG/keygen.exe': Read-only file system
chmod: changing permissions of `/media/disk/software/KG/virility.nfo': Read-only file system
chmod: changing permissions of `/media/disk/software/KG.zip': Read-only file system
chmod: changing permissions of `/media/disk/software/mx_2.0.0.8042.exe': Read-only file system
chmod: changing permissions of `/media/disk/software/mx_2.0.1.1276.exe': Read-only file system
chmod: changing permissions of `/media/disk/software/NeroDigitalPro-3.1.0.16.exe': Read-only file system
chmod: changing permissions of `/media/disk/software/NeroHacked.txt': Read-only file system
chmod: changing permissions of `/media/disk/software/NeroNET-1.2.0.2.exe': Read-only file system
chmod: changing permissions of `/media/disk/software/panic__at_the_disco_-_a_fever_you_can_t_sweat_out.zip': Read-only file system
chmod: changing permissions of `/media/disk/software/rapget126.rar': Read-only file system
chmod: changing permissions of `/media/disk/software/RapidShare-Killer-AIO.exe': Read-only file system
chmod: changing permissions of `/media/disk/software/SageTV v5.0.4.92': Read-only file system
chmod: changing permissions of `/media/disk/software/SageTV v5.0.4.92/Crack': Read-only file system
chmod: changing permissions of `/media/disk/software/SageTV v5.0.4.92/Crack/digerati.nfo': Read-only file system
chmod: changing permissions of `/media/disk/software/SageTV v5.0.4.92/Crack/SageTV.exe': Read-only file system
chmod: changing permissions of `/media/disk/software/SageTV v5.0.4.92/Crack/SageTVService.exe': Read-only file system
chmod: changing permissions of `/media/disk/software/SageTV v5.0.4.92/SageTVClient_V5_0_4Setup.exe': Read-only file system
chmod: changing permissions of `/media/disk/software/SageTV_v5.0.4.92.rar': Read-only file system
chmod: changing permissions of `/media/disk/software/TM': Read-only file system
chmod: changing permissions of `/media/disk/software/TM/crack': Read-only file system
chmod: changing permissions of `/media/disk/software/TM/crack/FFF.NFO': Read-only file system
chmod: changing permissions of `/media/disk/software/TM/crack/FILE_ID.DIZ': Read-only file system
chmod: changing permissions of `/media/disk/software/TM/crack/TransMac.exe': Read-only file system
chmod: changing permissions of `/media/disk/software/TM/tmsetup.exe': Read-only file system
chmod: changing permissions of `/media/disk/software/transmac_7.5__k__ed.zip': Read-only file system
chmod: changing permissions of `/media/disk/software/Typing Master Pro 7.0 EN': Read-only file system
chmod: changing permissions of `/media/disk/software/Typing Master Pro 7.0 EN/Latest_Downloads.html': Read-only file system
chmod: changing permissions of `/media/disk/software/Typing Master Pro 7.0 EN/Read_Me.txt': Read-only file system
chmod: changing permissions of `/media/disk/software/Typing Master Pro 7.0 EN/TypingMasterENG.exe': Read-only file system
chmod: changing permissions of `/media/disk/software/Typing Master Pro 7.0 EN/XshareX.info.nfo': Read-only file system
chmod: changing permissions of `/media/disk/software/typing_master_pro_7.0_en.rar': Read-only file system
chmod: changing permissions of `/media/disk/software/USDv134b7.rar': Read-only file system
chmod: changing permissions of `/media/disk/software/winzip110.exe': Read-only file system
chmod: changing permissions of `/media/disk/software/WinZip_Pro_v11.0.7313_inc.KG.zip': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/MountPointManagerRemoteDatabase': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/tracking.log': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032705.ini': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032706.nfo': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032737.ini': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032844.ini': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032894.ini': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032895.ini': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032896.ini': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032897.ini': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032898.nfo': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032899.ini': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032900.nfo': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032901.ini': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032902.ini': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032903.nfo': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032904.ini': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032905.nfo': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032906.ini': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032907.nfo': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032908.nfo': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032909.ini': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032910.nfo': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/A0032911.ini': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/change.log.1': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP311/RestorePointSize': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032934.ini': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032940.nfo': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032941.srt': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032942.srt': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032943.srt': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032944.nfo': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032945.srt': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032946.srt': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032947.srt': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032948.srt': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032949.srt': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032950.srt': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032951.srt': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032952.srt': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032953.srt': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032954.srt': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032955.srt': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032956.srt': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032957.srt': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032958.srt': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032959.srt': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032960.srt': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032961.nfo': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032967.srt': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/A0032968.srt': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/change.log.1': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP312/RestorePointSize': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP314': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP314/A0033059.ini': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP314/change.log.1': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP314/RestorePointSize': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP316': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP316/A0033091.ini': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP316/change.log.1': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP316/RestorePointSize': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP317': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP317/A0033116.ini': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP317/change.log.1': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP317/RestorePointSize': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP321': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP321/A0033146.ini': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP321/change.log.1': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP321/RestorePointSize': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP322': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP322/A0033212.ini': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP322/change.log.1': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP322/RestorePointSize': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP324': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP324/change.log.1': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP324/RestorePointSize': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP327': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP327/change.log.1': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP327/RestorePointSize': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP328': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP328/A0035425.ini': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP328/change.log.1': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP328/RestorePointSize': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP329': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP329/A0035614.ini': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP329/change.log.1': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP329/RestorePointSize': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP330': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP330/A0035730.ini': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP330/change.log.1': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP330/RestorePointSize': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP331': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP331/A0035941.ini': Read-only file system
chmod: changing permissions of `/media/disk/System Volume Information/_restore{C95869CC-60B9-4BC7-A18F-D6D4018748F3}/RP345/change.log': Read-only file system
lukanikos@lukanikos-desktop:~$ 
```

Both commands

---

### Post by lukanikos on 2007-07-09
And then I get the following messege after trying to move the file

```

Error while copying to "/media/disk".

You do not have permissions to write to this folder.
```

---

### Post by iota on 2007-07-12
sudo chown lukanikos /media/disk

Try using this instead. Hope it helps.

---

### Post by lukanikos on 2007-07-14
lukanikos@lukanikos-desktop:~$ sudo chown lukanikos /media/disk
Password:
chown: changing ownership of `/media/disk': Read-only file system
lukanikos@lukanikos-desktop:~$

---

### Post by vanadium on 2007-07-14
Post the output of 

mount

here. This way, you will see the correct pathname of the drive and the file system.

My guess is that your drive is ntfs formatted. ntfs cannot be written by a Linux system, although this is about to change. Currently, to write to an ntfs drive, you need to install extra software (ntfs-config). Additionally, as indicated by the previous posters, you need the proper permissions to write to the drive as a user (root can always write if the drive is mount read/write).

---

### Post by lukanikos on 2007-07-14
Yes you are right!!!

It's NTFS

---

### Post by whpsh on 2007-07-16
I just got finished with this problem too ... try this:

If it isn't, you'll need to install ntfs-3g

Do this by:

System -> Administration -> Synaptec Package Manager

Search for:

ntfs-3g

Mark it for installation and accept its dependencies.

then, from console run

$ sudo gedit /etc/fstab

On the line that has your drive, change it to look something like this:

Old:
# /dev/your_drive, 
UUID=???????????????? /media/your_drive ntfs defaults,nls=??,umask=??,gid=?? 0 1

New:
# /dev/your_drive
UUID=??????????????? /media/your_drive ntfs-3g rw,defaults,nls=??, umask=??, gid=?? 0 0

Save, Exit, Restart your machine and see if that works.
If it doesn't, then delete the entire entry for your drive in /etc/fstab and add

/dev/your_drive /media/your_drive ntfs-3g rw,defaults 0 0

This process worked just great for me. Good luck!!

---

