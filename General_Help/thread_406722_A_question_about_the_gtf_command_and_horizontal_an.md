---
title: "A question about the gtf command and horizontal and vertical refresh rates"
date: 2007-04-11
forum: General Help
---

### Post by Onion_Knight on 2007-04-11
Hello. I am trying to tweak the xorg.conf file to hopefully have Xubuntu display the 1024x768 resolution of my 15" AOC 5En CRT monitor. I, of course, need to determine its horizontal and vertical refresh rates and yet, from the technical information on the AOC website, only the horizontal refresh rate is shown, and from a different monitor too (a 5Elr) since I can't find any of the required info on my monitor model. I then learned of the *gtf *command but I still have a problem in that I can't recognize any data on the vertical refresh rate. Here is its output:

 1: [H PIXELS RND]             :     1024.000000
 2: [V LINES RND]              :      768.000000
 3: [V FIELD RATE RQD]         :       60.000000
 4: [TOP MARGIN (LINES)]       :        0.000000
 5: [BOT MARGIN (LINES)]       :        0.000000
 6: [INTERLACE]                :        0.000000
 7: [H PERIOD EST]             :       20.957954
 8: [V SYNC+BP]                :       26.000000
 9: [V BACK PORCH]             :       23.000000
10: [TOTAL V LINES]            :      795.000000
11: [V FIELD RATE EST]         :       60.018341
12: [H PERIOD]                 :       20.964361
13: [V FIELD RATE]             :       60.000000
14: [V FRAME RATE]             :       60.000000
15: [LEFT MARGIN (PIXELS)]     :        0.000000
16: [RIGHT MARGIN (PIXELS)]    :        0.000000
17: [TOTAL ACTIVE PIXELS]      :     1024.000000
18: [IDEAL DUTY CYCLE]         :       23.710691
19: [H BLANK (PIXELS)]         :      320.000000
20: [TOTAL PIXELS]             :     1344.000000
21: [PIXEL FREQ]               :       64.108795
22: [H FREQ]                   :       47.699997
17: [H SYNC (PIXELS)]          :      104.000000
18: [H FRONT PORCH (PIXELS)]   :       56.000000
36: [V ODD FRONT PORCH(LINES)] :        1.000000

  # 1024x768 @ 60.00 Hz (GTF) hsync: 47.70 kHz; pclk: 64.11 MHz
  Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync

---

