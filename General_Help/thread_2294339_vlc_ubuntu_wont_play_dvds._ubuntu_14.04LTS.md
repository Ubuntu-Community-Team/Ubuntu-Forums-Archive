---
title: "vlc ubuntu wont play dvds. ubuntu 14.04LTS"
date: 2015-09-10
forum: General Help
---

### Post by irongolem0982 on 2015-09-10
heres my vlc log: 
 

 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]processing request item: 17 Miracles, node: Playlist, skip: 0
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]resyncing on 17 Miracles
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]17 Miracles is at 0
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]starting playback of the new playlist item
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]resyncing on 17 Miracles
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]17 Miracles is at 0
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]creating new input thread
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Creating an input for '17 Miracles'
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using timeshift granularity of 50 MiB, in path '/tmp'
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]`dvd:///dev/sr0' gives access `dvd' demux `' path `/dev/sr0'
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]creating demux: access='dvd' demux='' location='/dev/sr0' file='/dev/sr0'
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for access_demux module matching "dvd": 20 candidates
 [COLOR=#00008b]*qt4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]IM: Setting an input
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]trying to go to dvd menu
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using access_demux module "dvdnav"
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for meta reader module matching "any": 2 candidates
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /home/rebecca/.local/share/vlc/lua/meta/reader
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/lib/vlc/lua/meta/reader
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua playlist script /usr/lib/vlc/lua/meta/reader/filename.luac
 [COLOR=#00008b]*lua*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Trying Lua scripts in /usr/share/vlc/lua/meta/reader
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]no meta reader modules matched
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]`dvd:///dev/sr0' successfully opened
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]DVDNAV_HOP_CHANNEL
 [COLOR=#00008b]*main*[/COLOR][COLOR=#ff0000]* error: *[/COLOR]ES_OUT_RESET_PCR called
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]DVDNAV_VTS_CHANGE
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]- vtsN=1
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]- domain=8
 [COLOR=#00008b]*main*[/COLOR][COLOR=#ff0000]* error: *[/COLOR]ES_OUT_RESET_PCR called
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]DVDNAV_CELL_CHANGE
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]- cellN=1
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]- pgN=1
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]- cell_length=10236000
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]- pg_length=10236000
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]- pgc_length=10236000
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]- cell_start=0
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]- pg_start=0
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]DVDNAV_SPU_CLUT_CHANGE
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]DVDNAV_SPU_STREAM_CHANGE
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]- physical_wide=0
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]- physical_letterbox=0
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]- physical_pan_scan=1
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]buttonUpdate not done b=1 t=0
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]selecting program id=0
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]looking for decoder module matching "any": 39 candidates
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]using decoder module "spudec"
 [COLOR=#00008b]*spudec*[/COLOR][COLOR=#808080]* debug: *[/COLOR]invalid starting packet (size 
 [COLOR=#00008b]*spudec*[/COLOR][COLOR=#808080]* debug: *[/COLOR]spu size: 0, i_pts: 0 i_buffer: 128
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]DVDNAV_AUDIO_STREAM_CHANGE
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]- physical=0
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Buffering 0%
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]buttonUpdate 1
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#008000]* warning: *[/COLOR]cannot get next block (Error reading from DVD.)
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]jumping to first title
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]DVDNAV_HOP_CHANNEL
 [COLOR=#00008b]*main*[/COLOR][COLOR=#ff0000]* error: *[/COLOR]ES_OUT_RESET_PCR called
 [COLOR=#00008b]*spudec*[/COLOR][COLOR=#808080]* debug: *[/COLOR]invalid starting packet (size 
 [COLOR=#00008b]*spudec*[/COLOR][COLOR=#808080]* debug: *[/COLOR]spu size: 0, i_pts: 0 i_buffer: 128
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]DVDNAV_VTS_CHANGE
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]- vtsN=1
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]- domain=2
 [COLOR=#00008b]*main*[/COLOR][COLOR=#ff0000]* error: *[/COLOR]ES_OUT_RESET_PCR called
 [COLOR=#00008b]*spudec*[/COLOR][COLOR=#808080]* debug: *[/COLOR]invalid starting packet (size 
 [COLOR=#00008b]*spudec*[/COLOR][COLOR=#808080]* debug: *[/COLOR]spu size: 0, i_pts: 0 i_buffer: 128
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]removing module "spudec"
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]killing decoder fourcc `spu ', 0 PES in FIFO
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Program doesn't contain anymore ES
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]DVDNAV_CELL_CHANGE
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]- cellN=1
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]- pgN=1
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]- cell_length=32541000
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]- pg_length=32541000
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]- pgc_length=553923000
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]- cell_start=0
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]- pg_start=0
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]DVDNAV_SPU_CLUT_CHANGE
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]DVDNAV_SPU_STREAM_CHANGE
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]- physical_wide=128
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]- physical_letterbox=128
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]- physical_pan_scan=128
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]buttonUpdate not done b=1 t=1
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]DVDNAV_AUDIO_STREAM_CHANGE
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#808080]* debug: *[/COLOR]- physical=0
 [COLOR=#00008b]*dvdnav*[/COLOR][COLOR=#008000]* warning: *[/COLOR]cannot get next block (Error reading NAV packet.)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]finished input
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]control: stopping input
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]finished input
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]removing module "dvdnav"
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]Program doesn't contain anymore ES
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]dead input
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]changing item without a request (current 0/1)
 [COLOR=#00008b]*main*[/COLOR][COLOR=#808080]* debug: *[/COLOR]nothing to play
 [COLOR=#00008b]*qt4*[/COLOR][COLOR=#808080]* debug: *[/COLOR]IM: Deleting the input


have tried sudo apt-get install ubuntu-restricted-extras then sudo reboot. still wont play. have tried multiple dvds.
ubuntu 14.04 lts

---

### Post by QDR06VV9 on 2015-09-10
You might be missing.
 [COLOR=#0000cc][B]libdvdcss
```
[/B][/COLOR]sudo apt-get install libdvdread4

 sudo /usr/share/doc/libdvdread4/install-css.sh
[COLOR=#0000cc][B]
```
[/B][/COLOR]

---

