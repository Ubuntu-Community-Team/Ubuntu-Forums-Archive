---
title: "flexget timeframe issues"
date: 2014-04-09
forum: General Help
---

### Post by JohnnyC35 on 2014-04-09
I reinstalled Xubuntu 13.10, and installed the updated flexget. I am now trying to create a new config.yml file but for some reason  it says the key timeframe is not valid here. It seems to be in the right spot. If I comment it out the config file works fine.
I removed the tasks and the reject list since that would make this even longer.:

```

templates:
  global:
    download: /home/john/.flexget/torrents/
    exists_series:
      - /home/john/.flexget/torrents/
      - /home/john/.config/transmission/torrents/
      - /home/john/torDownloads/


  tv:
    timeframe: 12 hours
    quality: <=480p <=hdtv <=divx
    accept_all: yes


  movies:
    timeframe: 24 hours
    quality: 720p+ bluray h264+
    accept_all: yes


  books:
    accept_all: yes


  anime:
    timeframe: 24 hours
    quality: <=480p <=hdtv <=divx
    accept_all: yes



```

---

