---
title: "Spotify and xdg-open"
date: 2016-08-25
forum: General Help
---

### Post by lukasz20 on 2016-08-25
I am trying to make spotify links work in Linux (e.g. lastfm is using spotify to play the music, or playlists posted on open.spotify.com - like [this one]("https://open.spotify.com/user/billboard.com/playlist/6UeSakyzhiEt4NB3UAd6NQ")).
If I click on a spotify link in a browser, new browser window is opened.
I tried to add new mime type for spotify but it is still being opened by browser:

```
$ xdg-mime default spotify.desktop x-scheme-handler/spotify
$ xdg-mime query default x-scheme-handler/spotify
spotify.desktop
$ xdg-open spotify:user:spotify:playlist:5FJXhjdILmRA2z5bvz4nzf
Created new window in existing browser session.
```

---

