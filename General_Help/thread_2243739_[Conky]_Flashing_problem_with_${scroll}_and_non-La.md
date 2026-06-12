---
title: "[Conky] Flashing problem with ${scroll} and non-Latin characters"
date: 2014-09-10
forum: General Help
---

### Post by syntaxerror74 on 2014-09-10
Below you'll find a very short bit of my nearly 3 weeks of work on my (entire) .conkyrc, supporting both deadbeef (quasi-full support including playing position!) and mplayer (basic support via /proc; playing position would need a temp file to be read out (ugh!! no thanks)).
Deadbeef line being present and showing as not playing back anything, and mplayer being completely absent is purpose (depends on how rarely I'd use mplayer for audio :))

This snippet will even work fine as-is (i. e. standalone) **as long as** you keep to Latin characters! Once you start playing some titles in Polish, Cyrillic or even Japanese (tried them all) the problems will start.
> override_utf8_locale yes

This is the only thing you can do in conky to get UTF8 support working! However, even though the foreign text WILL be displayed correctly, the ${scroll} feature will definitely cause the scroller to either jerk around or "flash" (= cause the entire text to disappear) whenever it hits a special character during scrolling!
Is there any way out or should I file a bug?

I believe I can't be doing anything wrong from user's side.

(Note: I'm using "unusual" font WenQuanYi Micro Hei Mono, which, however, is essential for Chinese and Japanese to display correctly. Will even display Latin characters perfectly - love this font.)

```

double_buffer yes
own_window yes
own_window_class Conky
own_window_hints undecorated,sticky # ,skip_taskbar  (note: commented out; got to be able to restore conky window after showing desktop)
own_window_transparent yes

background yes
short_units yes
max_user_text 24576
no_buffers yes
text_buffer_size 3072

total_run_times 0 
update_interval 0.55

use_xft yes
xftfont Bitstream Vera Sans:size=7
xftalpha 0.85
override_utf8_locale yes 

minimum_size 225

TEXT
Audio ${hr 1}${color fbf790}
${if_running deadbeef-gtkui}\
${if_match "${texeci 1 /usr/bin/deadbeef --nowplaying "%a - %t" 2>/dev/null | sed 's/\!//g'}" == "nothing"}\
${voffset +6}deadbeef: ${color0}not playing back anything${color}\
${else}\
${voffset +5}${offset +7}${font WenQuanYi Micro Hei Mono:size=7}\
${if_match "${texeci 5 /usr/bin/deadbeef --nowplaying "%y" 2>/dev/null}" == ""}\
${scroll 20 1 ${execi 16 /usr/bin/deadbeef --nowplaying "%a - %t" 2>/dev/null}}\
$else ${if_match "${texeci 5 /usr/bin/deadbeef --nowplaying "%y" 2>/dev/null}" == "0"}\
${scroll 20 1 ${execi 16 /usr/bin/deadbeef --nowplaying "%a - %t" 2>/dev/null}}\
$else ${scroll 20 1 ${execi 16 /usr/bin/deadbeef --nowplaying "%a - %t (%y)" 2>/dev/null}}${endif}\
${endif}\
${font WenQuanYi Micro Hei Mono:size=7:style:bold}$alignr\
${texeci 0.75 /usr/bin/deadbeef --nowplaying "%e / %l" 2>/dev/null}${endif}${font}
${else}${voffset +6}deadbeef: ${color}not launched\
${endif}
${voffset -2}${color fbf790}\
${if_running mplayer}\
mplayer: ${color} ${scroll 20 1 playing back file ${font WenQuanYi Micro Hei Mono:size=7}\
'${execp basename "$(readlink /proc/$(pidof mplayer)/fd/* | grep -v '\(dev\|pipe\|socket\)')"}'}\
${font}${endif}

```

---

### Post by syntaxerror74 on 2014-09-18
Anybody out there to help me with this issue?

---

