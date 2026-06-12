---
title: "Migrating torrents from KTorrent to rTorrent"
date: 2013-04-13
forum: General Help
---

### Post by Stonecold1995 on 2013-04-13
I have many torrents that I currently run in KTorrent, but I'd like to move to rTorrent so I don't have to depend on Xorg to seed (KTorrent is currently the only reason I need to have Xorg running all the time).  Anyways, I need a way to migrate the torrent configurations (such as current ratio, downloaded, uploaded, seed time, file location, etc) and the torrents themselves to rTorrent in a way that I can just fire up the program and it'll take place exactly where KTorrent left off (i.e. it must look for the files in the correct path, check the torrents' hashes, then start seeding).

Is there a way to do this?  I understand the filesystem structure KTorrent uses for torrent info (i.e. the purpose of each file in ~/.kde/share/apps/ktorrent), but I know nothing of how rTorrent.  Is there a way I can do this using a script or something similar?  Doing it manually by editing each config file would take a LONG time.


Also, can anyone recommend a good guide to getting use to rTorrent so I can make use of its features best?

Thanks.

---

### Post by andrew.46 on 2013-04-13
Might be best to make a fresh start rather than attempt to migrate. Only one configuration file needed for rtorrent: $HOME/.rtorrent.rc.

---

### Post by Stonecold1995 on 2013-04-13
> **andrew.46 said:**
> Might be best to make a fresh start rather than attempt to migrate. Only one configuration file needed for rtorrent: $HOME/.rtorrent.rc.
But I *can't* make a fresh start, I have to keep seeding my already downloaded torrents.  I've already said that.

As far as I know, the manual solution would be to take the path of the downloaded file, and the torrent file, and set the downloaded path in rTorrent's config as the same as for KTorrent.  Then open the .torrent file in rTorrent.  rTorrent should then read the torrent, read the config (and find the already-downloaded files), check the files, and then start seeding.

Also, does rTorrent stores .torrent files like KTorrent does (KTorrent stores them as ~/.kde/share/apps/ktorrent/tor[#]/torrent)?

---

### Post by andrew.46 on 2013-04-13
> **Stonecold1995 said:**
> Also, does rTorrent stores .torrent files like KTorrent does (KTorrent stores them as ~/.kde/share/apps/ktorrent/tor[#]/torrent)?

You can set this to anywhere you wish by setting a *session* variable in $HOME/.rtorrent,rc, for me the following setting works well enough:

```

session = /home/andrew/.rtorrent

```

Not sure about all the migration stuff I'm afraid :(.

---

### Post by Stonecold1995 on 2013-04-23
So I think basically what I have to do is find a way to convert the format of files in ~/.kde/share/apps/ktorrent/tor[number] (for KTorrent) into the format used in ~/.rtorrent/[hash].torrent.rtorrent (for rTorrent).  But the format is much different.  And not even very user friendly, it's not even a delimited file, no newlines or anything.

Come one, this can't be THAT rare of a problem!  There has to be a way to do this *somewhere*...

Specifically, what I have to transfer over is:
- Download locations
- Ratio
- Amount of Uploaded/Downloaded data
- Time seeding/leeching
- Date when it was added
- Tracker list (including trackers added myself, in addition to trackers specified in the torrent file)

Here is where they are stored:

Locations of files (even files that were set not to download): ~/.kde/share/apps/ktorrent/tor[number]/file_map
```
/absoute/path/to/file1
/absolute/path/to/file2
file1
file2
```

Ratio, uploaded/downloaded data, time seeding/leeching, date torrent was added, etc:
~/.kde/share/apps/ktorrent/tor[number]/stats
```
ASSURED_DOWNLOAD_SPEED=0ASSURED_UPLOAD_SPEED=0
AUTOSTART=0
AUTO_STOPPED=0
COMPLETEDDIR=
CUSTOM_OUTPUT_NAME=1
DHT=1
DISPLAY_NAME=
DOWNLOAD_LIMIT=0
ENCODING=UTF-8
IMPORTED=43001346
MAX_RATIO=0.00
MAX_SEED_TIME=0
OUTPUTDIR=/absolute/path/to/directory
PRIORITY=95
QM_CAN_START=0
RESTART_DISK_PREALLOCATION=0
RUNNING_TIME_DL=0
RUNNING_TIME_UL=7874773
SUPERSEEDING=0
TIME_ADDED=1344662880
UPLOADED=1708465943
UPLOAD_LIMIT=0
URL=
UT_PEX=1
```

Trackers (not sure if custom, torrent only, or both): ~/.kde/share/apps/ktorrent/tor[number]/trackers
```
udp://tracker.openbittorrent.com:80/announce
udp://tracker.publicbt.com:80/announce
```




The way rTorrent stores the info is in ~/.rtorrent/[hash].torrent.rtorrent and looks something like this:
```
d27:choke_heuristics.down.leech0:26:choke_heuristics.down.seed0:25:choke_heuristics.up.leech0:24:choke_heuristics.up.seed0:11:chunks_donei0e13:chunks_wantedi1313e8:completei0e16:connection_leech0:15:connection_seed0:6:customd10:x-filename22:torrent%282%29.torrente7:custom120:**Custom%20torrent%20label**:T7:custom281:VRS24mrker**Original%20torrent%20name**:custom30:7:custom40:7:custom50:9:directory69:**/absolute/path/to/directory**:hashingi1e15:ignore_commandsi0e3:keyi451565430e11:loaded_file0:8:priorityi2e5:statei1e13:state_changedi1366706481e13:state_counteri0e13:throttle_name0:12:tied_to_file0:18:timestamp.finishedi0e17:timestamp.startedi0e14:total_uploadedi0e5:viewslee
```

I really don't understand it at all.  Or very little at least.

---

### Post by Vaphell on 2013-04-23
> **Stonecold1995 said:**
> Come one, this can't be THAT rare of a problem!  There has to be a way to do this *somewhere*...

imho it is ;-)
usually people simply change their client and that's it, having to preserve up/down ratios or whatever is rare.

If initializing the download, quitting the client, putting all finished files in place (can be done via hardlinks to avoid data duplication), restarting client is not enough to solve the migration problem (so the client thinks it already completed the download and starts seeding), then bad luck.

---

### Post by Vaphell on 2013-04-23
can you post the other format too? I don't feel like installing different clients to check :-)

---

### Post by Stonecold1995 on 2013-04-23
> **Vaphell said:**
> If initializing the download, quitting the client, putting all finished files in place (can be done via hardlinks to avoid data duplication), restarting client is not enough to solve the migration problem (so the client thinks it already completed the download and starts seeding), then bad luck.
That will only migrate the torrent but no ratio, etc.

> **Vaphell said:**
> can you post the other format too? I don't feel like installing different clients to check :-)
I edited my above post already.

---

