---
title: "stop btrfs subvolume showing other subvolumes"
date: 2023-07-10
forum: General Help
---

### Post by lance bermudez on 2023-07-10
How do I stop a  btrfs subvolume showing other subvolumes on the same drive?
I have the movies subvolume mounted at ~/plexmedia/Movies I want to stop showing the other subvolumes on the drive in the movie subvolume

my /etc/fstab
```

UUID=55b81c34-5ca3-4ac8-a260-64c741f15b3d /home/user/plexmedia/Movies btrfs rw,exec,compress=zstd,autodefrag,subvolid=257 0 0
UUID=55b81c34-5ca3-4ac8-a260-64c741f15b3d /home/user/plexmedia/btrfs btrfs rw,exec,compress=zstd,autodefrag,subvolid=725 0 0

```

sudo btrfs subv list ~/plex/Movies/
```

ID 257 gen 15252 top level 5 path movies
ID 258 gen 8 top level 5 path tv
ID 259 gen 9 top level 5 path cartoons
ID 260 gen 10 top level 5 path comicbooks
ID 725 gen 15252 top level 257 path SnapShotsMovies
ID 726 gen 15250 top level 257 path SnapShotsComicBooks
ID 1705 gen 15252 top level 257 path movies1

```

---

