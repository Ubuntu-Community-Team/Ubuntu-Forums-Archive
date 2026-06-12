---
title: "[conky] Trouble getting battery status"
date: 2014-07-11
forum: General Help
---

### Post by Axioen on 2014-07-11
I'm not sure if this is the place to post this, so if not I apologize.

Basically I'm piping conky through my i3wm config to display information on i3's statusbar. I'd like to have it set up so it changes "icons" (really just unicode text) based on different statuses. For example, I have it set to change the battery icon depending on the percentage (70%, 30%, etc). For some reason I can't get the battery's icon to change when charging. I believe I'm supposed to use "${battery_short}" but I'm not really sure where to go from there.

Here's my config file:
```
out_to_x no
own_window no
out_to_console yes
background no
max_text_width 0
# Update interval in seconds
update_interval 1.0
total_run_times 0
override_utf8_locale yes


TEXT


# ---- MPD ----


[{ "full_text" : "&#11157; MPD" , "color" : "\#aaaaaa" } ,
 { "full_text" : "${if_mpd_playing}${mpd_smart 50} ${mpd_elapsed}/${mpd_length}${else}${mpd_status}${endif} ","color" : "\#63637a" },


# ---- WIRELESS ESSID/QUALITY  ----


 {"full_text": "${if_match ${wireless_link_qual_perc}>=70}&#11191; ${wireless_essid wlan0} ", "color": "\#aaaaaa" },
 {"full_text":"${else}"},
 {"full_text": "${if_match ${wireless_link_qual_perc}<70}&#11192; ${wireless_essid wlan0} ", "color": "\#aaaaaa" },
 {"full_text":"${else}"},
 {"full_text": "${if_match ${wireless_link_qual_perc}<30}&#11193; ${wireless_essid wlan0} ", "color": "\#aaaaaa" },
 {"full_text":"${endif}${endif}${endif}"},


# ---- BATTERY (%) ----
 
 #{"full_text":"${battery_short} ","color":"\#aaaaaa"},


 {"full_text":"${if_match ${battery_percent}<30}&#11152; ${battery_percent}%  ","color":"\#aaaaaa","separator":false,"separator_block_width":6},
 {"full_text":"${else}"},
 {"full_text":"${if_match ${battery_percent}<70}&#11153; ${battery_percent}%  ","color":"\#aaaaaa","separator":false,"separator_block_width":6},
 {"full_text":"${else}"},
 {"full_text":"${if_match ${battery_percent}>=70}&#11151; ${battery_percent}%  ","color":"\#aaaaaa","separator":false,"separator_block_width":6},
 {"full_text":"${else}"},
 {"full_text":"${if_match "${battery_short}"<"D"}&#11150; ${battery_percent}% ","color":"\#aaaaaa","separator":false,"separator_block_width":6},
 {"full_text":"${endif}${endif}${endif}${endif}"},


# ---- VOLUME (%) ----


 {"full_text":"${if_match ${exec amixer get Master -M | grep -oE  "[[:digit:]]*%"}>=70}&#11166; ${exec amixer get Master -M | grep -oE "[[:digit:]]*%"} ","color":"\#aaaaaa"},
 {"full_text":"${else}"},
 {"full_text":"${endif}"},
 


# ---- TIME/DATE ----


 {"full_text":"&#11158; ${time %b %d, %H:%M}","color" : "\#aaaaaa" }] ,



```

---

