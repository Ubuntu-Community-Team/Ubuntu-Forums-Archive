---
title: "deluge crash and pygame"
date: 2012-11-10
forum: General Help
---

### Post by asensio on 2012-11-10
hello everybody

there're a couple of days that I'm having a problem with Deluge (torrent client). I start it and it works up to 10 minutes then it crashes. Running from terminal I get the message:


```
Fatal Python error: (pygame parachute) Segmentation Fault
Aborted (core dump)
```

with:
deluge --loglevel=debug 

```
[DEBUG   ] 19:25:25 torrentmanager:727 Opening torrents fastresume file for load.
[DEBUG   ] 19:25:25 torrentmanager:767 Saving fastresume file: /home/asensio/.config/deluge/state/torrents.fastresume
Fatal Python error: (pygame parachute) Segmentation Fault
Abortado (imagem do núcleo gravada)
```


I've removed deluge and reinstalled it, i've clear the deluge folder in ~/.config

I think none of the packages required by deluge has been updated. I thought pygame was having some kind of problem but it's not, I removed it (it wasn't a deluge dependency).. But deluge keeps segfaulting

 

Can someone help? Thanks 
Cheers

---

