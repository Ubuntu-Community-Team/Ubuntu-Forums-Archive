---
title: "Replacing gnome-search-tool with Beagle"
date: 2007-05-31
forum: General Help
---

### Post by syko21 on 2007-05-31
I found beagle does a better job of indexing pictures and gaim/pidgin conversations than the default gnome-search-tool. So here's how to replace it so that ubuntu uses beagle by default. (this is after you install beagle of course, [http://ubuntuforums.org/showthread.php?t=78810](http://ubuntuforums.org/showthread.php?t=78810))

```

sudo cp /usr/bin/gnome-search-tool /usr/bin/gnome-search-tool.bak
sudo rm /usr/bin/gnome-search-tool
sudo ln -s /usr/bin/beagle-search /usr/bin/gnome-search-tool

```

---

