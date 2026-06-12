---
title: "Help needed optimizing 12.04"
date: 2013-03-05
forum: General Help
---

### Post by tojvan on 2013-03-05
so, i have a Dell R5500 server, with 32 GB RAM, 2 x 6 core Xeons, 4 SATA drives in a Raid 10. i have prepared 2 sets of drives, identical raid config, one set with 10.04, the other with 12.04. the server has a Quadro 5800.

my (openGL and video heavy) application flies on 10.04, consistently hitting its rate limit of 60 fps but struggles at around 35 fps on 12.04. other comparisons:


application                   |            10.04          |       12.04
-------------------------------------------------------------------
`glxgears -fullscreen`    |       1800 fps       |      600 fps

phoronix iozone write     |      ~1300 MB/s   |      ~170 MB/s

phoronix iozone read      |         5200 MB/s   |     3900 MB/s


The difference in performance extends to everything, including running imagemagick's convert on the same machine. We've seen this performance difference on many Dell Xeon machines (T7500, r5500, amongst others). We've noted a difference with NVidia Quadro 5800 as well as ATI Firepro W9000 cards.

What could we be doing wrong?

---

