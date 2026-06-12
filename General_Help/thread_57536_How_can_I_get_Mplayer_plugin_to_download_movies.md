---
title: "How can I get Mplayer plugin to download movies?"
date: 2005-08-16
forum: General Help
---

### Post by Slicedbread on 2005-08-16
How can I get Mplayer plugin to download movies? I installed 3.05 plugin and I thought I configured it to download to a directory but it doesnt seem to work. Any help would be appreciated.

---

### Post by bob k on 2005-08-17
edit your ~/,mplayer/mplayerplug-in.conf and uncomment (remove # in col 1)  and set the following options.

download=1                   <-- Turn on download
dload-dir=$HOME/tmp   <-- directory can be any dir that                          
                                             you have write privs
keep-download=1            <-- don't erase when done

---

