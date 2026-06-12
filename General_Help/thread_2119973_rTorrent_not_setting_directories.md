---
title: "rTorrent not setting directories"
date: 2013-02-25
forum: General Help
---

### Post by AnalBeard on 2013-02-25
Ok, so I don't think this is strictly a Ubuntu problem, probably more of an rTorrent problem, however it's only occurred since I moved my server over to Ubuntu. I have rTorrent set up to watch directories and auto-add torrents based on the location. Under my previous install of kFreeBSD this worked beautifully, however this just isn't happening now. Instead of downloading it to the specified directory, they end up in ./torrent_folder_name, which is invariably my home directory. I'll post my config so someone might be able to see something I can't:

```

schedule = watch_directory_2,10,10,"load_start=/mnt/tank/downloads/rtorrent/watch/distros/*.torrent,d.set_custom1=/mnt/tank/downloads/distros/"

```

Now I'm wondering if it's a permissions issue, I run rtorrent under my own user and I've chowned the directory as simon:simon (my user).

Can anyone shed any light on why this would be happening?



edit: not that I can see why it would make a difference, but the drive mounted at /mnt/tank is a zfspool

---

### Post by andrew.46 on 2013-03-02
My own syntax which is working flawlessly is slightly different to yours. The relevant section is:

```

# Watch a directory for new torrents, and stop those that have been deleted.
schedule = watch_directory,5,5,load_start=/home/andrew/.rtorrent/*.torrent
schedule = untied_directory,5,5,stop_untied=

# Move the completed torrents to~/downloads:
system.method.set_key = event.download.finished,move_complete,"execute=mv,-u,$d.get_base_path=,~/downloads/;d.set_directory=~/downloads/"

```

Is this similar to what you are trying to accomplish? This is with:

```

andrew@skamandros~$ rtorrent -h | head -n 1
Rakshasa's BitTorrent client version 0.9.2.

```

---

