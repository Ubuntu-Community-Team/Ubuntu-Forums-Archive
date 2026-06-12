---
title: "ncmpcpp terminal colors problems"
date: 2017-01-09
forum: General Help
---

### Post by munchlax on 2017-01-09
Hi first time posting here ! [IMG]http://forums.debian.net/images/smilies/icon_smile.gif[/IMG]
well , i updated my kernel , and after that ,the progress bar color is stuck to that flash green color , instead of red 
and i couldnt find any solution on google 

heres my config,thx [IMG]http://forums.debian.net/images/smilies/icon_smile.gif[/IMG]

```
visualizer_fifo_path = "/tmp/mpd.fifo"
visualizer_output_name = "my_fifo"
#visualizer_sync_internal = "30"
visualizer_in_stereo = "yes"
visualizer_type = "spectrum"
visualizer_look = "&#9679;&#9679;"
mpd_music_dir = "/home/muchlax/Music/"
colors_enabled = "yes"
playlist_display_mode = "classic" (classic/columns)
autocenter_mode = "yes"
centered_cursor = "yes"
cyclic_scrolling = "yes"
mouse_list_scroll_whole_page = "no"
song_list_format = "$8%a$9 &#10006; $2%t$9 "
song_library_format = "{%n > }{%t}|{%f}"
progressbar_look = "»» "
now_playing_suffix = " $7&#9835;$9 "
selected_item_prefix = " &#8730; "
titles_visibility = "no"
header_visibility = "no"
statusbar_visibility = "no" 
browser_playlist_prefix = "$2plist »$9 "
browser_display_mode = "classic" (classic/columns)
discard_colors_if_item_is_selected = "no"
header_window_color = "black"
volume_color = "black"
state_line_color = "cyan"
state_flags_color = "cyan"
main_window_color = "white"
main_window_highlight_color = "white"
progressbar_color = "red"
statusbar_color = "white"
song_status_format = "$8%a$9 &#10006; $2%t$9"
active_column_color = "red"
visualizer_color = "red"
song_window_title_format = "%a - %t"
#song_window_title_format = ""
search_engine_display_mode = "columns" (classic/columns)
follow_now_playing_lyrics = "yes"
#display_screens_numbers_on_start = "no"
mpd_host = "127.0.0.1"
mpd_port = "6601"
```

---

