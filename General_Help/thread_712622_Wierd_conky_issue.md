---
title: "Wierd conky issue"
date: 2008-03-01
forum: General Help
---

### Post by uberlube on 2008-03-01
I had a cataclysmic power failue in my house 2wice yesterday while my CPU was running. Before that I configured conky with new colours for my desktop and it was working fine. Now when I launch it, it appears as a small black rectangle in the upper right of my desktop. Heres the output:

```
manaburn@manaburn-desktop:~$ conky -a top_right
Conky: one or more $endif's are missing
Conky: desktop window (c000bd) is subwindow of root window (1a5)
Conky: window type - normal
Conky: drawing to created window (3200001)
Conky: drawing to double buffer
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: Couldn't attach to DCOP server!
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: Couldn't attach to DCOP server!
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: Couldn't attach to DCOP server!
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: Couldn't attach to DCOP server!
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: Couldn't attach to DCOP server!
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: Couldn't attach to DCOP server!
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: Couldn't attach to DCOP server!
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: Couldn't attach to DCOP server!
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: Couldn't attach to DCOP server!
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: Couldn't attach to DCOP server!
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
ERROR: Couldn't attach to DCOP server!
DCOPClient::attachInternal. Attach failed Could not open network socket

```

Anyone ever had this happen to them?

---

### Post by uberlube on 2008-03-02
Bump

---

### Post by kerry_s on 2008-03-02
it says " one or more $endif's are missing " so your conkyrc is boned. rename it and see if the stock one works.

---

### Post by uberlube on 2008-03-02
Tried that, dint work. I also deleted and reinstalled conky then added my .conkyrc back into the home folder but I keep getting the same error msg.

---

### Post by uberlube on 2008-03-02
although the stock one did work when I tried it. But adding .conkyrc to the equation messes it up again.

---

### Post by seventhc on 2008-03-02
maybe post your .conkyrc.
I don't see how a power failure would effect conky.
Thats weird :confused:

---

### Post by uberlube on 2008-03-02
Ya tell me about it:confused: Here it is:

```
background no
font Sans:size=8
#xftfont Sans:size=10
use_xft yes
xftalpha 0.9
update_interval 3.0
total_run_times 0
own_window yes
own_window_type normal
own_window_transparent yes
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 220 5
maximum_width 220
draw_shades yes
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color black
default_outline_color green
alignment top_right
gap_x 12
gap_y 35
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale no
uppercase yes # set to yes if you want all text to be in uppercase

# Update interval in seconds
update_interval 1.0

TEXT
${color orange}SYSTEM ${hr 1}${color}

${color green}Hostname: $alignr$nodename
Kernel: $alignr$kernel
Uptime: $alignr$uptime
Temp: ${alignr}${acpitemp}C${color}

${color orange}CPU ${hr 1}${color}
${color green}${freq} MHz
Load: ${loadavg}   ${alignr}Temp: ${acpitemp}${color}
${color orange}$cpubar${color}
${color green}Ram ${alignr}$mem / $memmax ($memperc%)${color}
${color orange}${membar 4}${color}
${color green}swap ${alignr}$swap / $swapmax ($swapperc%)${color}
${color orange}${swapbar 4}${color}

${color orange}Highest CPU $alignr CPU% MEM%${color}
${color green}${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}${color}

${color orange}Highest MEM $alignr CPU% MEM%${color}
${color green}${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}${color}

${color orange}FILESYSTEM ${hr 1}${color}

${color green}Root: ${alignr}${fs_used /} / ${fs_size /}${color}
${color orange}${fs_bar 4 /}${color}
${color green}Home: ${alignr}${fs_used /home} / ${fs_size /home}${color}
${color orange}${fs_bar 4 /home}${color}
${color green}Backup: ${alignr}${fs_used /media/Backup} / ${fs_size /media/Backup}${color}
${color orange}${fs_bar 4 /media/Backup}${color}


${color orange}NETWORK ${addr eth0} ${hr 1}$color

${color green}Down ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s${color}
${color orange}${downspeedgraph eth0 25,107 000000 ff0000} ${alignr}${upspeedgraph eth0 25,107 000000 ff0000}${color}
${color green}Total ${totaldown eth0} ${alignr}Total ${totalup eth0}${color}

${color orange}AMAROK ${hr 1}$color

$color$stippled_hr${if_running amarokapp}
${color green}${alignc}Now Playing
${alignc}${execi 10 ~/.conkyamarok artist}
${alignc}${execi 10 ~/.conkyamarok title}${color}
${color orange}${execibar 1 ~/.conkyamarok progress}${color}
${color green}${alignc}"${execi 10 ~/.conkyamarok album}"
${alignc}${execi 10 ~/.conkyamarok year} - ${alignc}${execi 10 ~/.conkyamarok genre}${color}
$color$stippled_hr
${color green}${alignc}Collection Information
Artists: ${execi 10 ~/.conkyamarok totalArtists} ${alignr}Compilations: ${execi 10 ~/.conkyamarok totalCompilations}
Albums:  ${execi 10 ~/.conkyamarok totalAlbums} ${alignr}Genres: ${execi 10 ~/.conkyamarok totalGenres}
Tracks:  ${execi 10 ~/.conkyamarok totalTracks}${color}
```

And here is the Amarok script:

```
#!/bin/bash
# amaroK info display script by eirc <eirc.eirc@gmail.com>
#
# requirements: amaroK (!)
# for Collection stats to work amarok must be using
# mySQL to store it's collection

case "$1" in

# Now Playing Info
artist) dcop amarok player artist ;;
title)  dcop amarok player title ;;
album)  dcop amarok player album ;;
year)   dcop amarok player year ;;
genre)  dcop amarok player genre ;;
progress)
    curr=`dcop amarok player trackCurrentTime`
    tot=`dcop amarok player trackTotalTime`
    if (( $tot )); then
        expr $curr \* 100  / $tot
    fi
    ;;

# Collection Info
totalArtists)      dcop amarok collection totalArtists ;;
totalAlbums)       dcop amarok collection totalAlbums ;;
totalTracks)       dcop amarok collection totalTracks ;;
totalGenres)       dcop amarok collection totalGenres ;;
totalCompilations) dcop amarok collection totalCompilations ;;

# Collection Stats
most_songs_by_artist) dcop amarok collection query 'SELECT t1.name FROM artist t1 INNER JOIN tags t2 ON t1.id = t2.artist GROUP BY t2.artist ORDER BY COUNT(t2.artist) DESC LIMIT 1;' ;;
most_songs_by_artist_n) dcop amarok collection query 'SELECT count(t2.artist) FROM artist t1 INNER JOIN tags t2 ON t1.id = t2.artist GROUP BY t2.artist ORDER BY COUNT(t2.artist) DESC LIMIT 1;' ;;
most_songs_are_genre) dcop amarok collection query 'SELECT t1.name FROM genre t1 INNER JOIN tags t2 ON t1.id = t2.genre GROUP BY t2.genre ORDER BY COUNT(t2.genre) DESC LIMIT 1;' ;;
most_songs_are_genre_n) dcop amarok collection query 'SELECT count(t2.genre) FROM genre t1 INNER JOIN tags t2 ON t1.id = t2.genre GROUP BY t2.genre ORDER BY COUNT(t2.genre) DESC LIMIT 1;' ;;
most_songs_during_year) dcop amarok collection query 'SELECT t1.name FROM year t1 INNER JOIN tags t2 ON t1.id = t2.year GROUP BY t2.year ORDER BY COUNT(t2.year) DESC LIMIT 1;' ;;
most_songs_during_year_n) dcop amarok collection query 'SELECT count(t2.year) FROM year t1 INNER JOIN tags t2 ON t1.id = t2.year GROUP BY t2.year ORDER BY COUNT(t2.year) DESC LIMIT 1;' ;;
most_albums_by_artist) dcop amarok collection query 'SELECT name FROM artist WHERE id=(SELECT t1.artist from (SELECT artist FROM tags GROUP BY album) AS t1 GROUP BY t1.artist ORDER BY count(artist) DESC LIMIT 1);' ;;
most_albums_by_artist_n) dcop amarok collection query 'SELECT count(artist) from (SELECT artist FROM tags GROUP BY album) AS t1 GROUP BY t1.artist ORDER BY count(artist) DESC LIMIT 1;' ;;
most_albums_are_genre) dcop amarok collection query 'SELECT name FROM genre WHERE id=(SELECT t1.genre from (SELECT genre FROM tags GROUP BY album) AS t1 GROUP BY t1.genre ORDER BY count(genre) DESC LIMIT 1);' ;;
most_albums_are_genre_n) dcop amarok collection query 'SELECT count(genre) from (SELECT genre FROM tags GROUP BY album) AS t1 GROUP BY t1.genre ORDER BY count(genre) DESC LIMIT 1;' ;;
most_albums_during_year) dcop amarok collection query 'SELECT name FROM year WHERE id=(SELECT t1.year from (SELECT year FROM tags GROUP BY album) AS t1 GROUP BY t1.year ORDER BY count(year) DESC LIMIT 1);' ;;
most_albums_during_year_n) dcop amarok collection query 'SELECT count(year) from (SELECT year FROM tags GROUP BY album) AS t1 GROUP BY t1.year ORDER BY count(year) DESC LIMIT 1;' ;;

esac
```

---

### Post by uberlube on 2008-03-02
Heres what my situation looks like:

---

### Post by seventhc on 2008-03-02
your conkyrc is fine, I ran it on my machine. I don't use amorak so can't test that script. but I think the error might be coming from that script.

---

### Post by uberlube on 2008-03-02
Nah, Ive already ruled that out. Perhaps some system file was corrupted during the blackout. Is there a terminal command to check system integrity and all that?

---

### Post by Del Piero on 2008-04-21
Exact same story!!!! :confused:

---

### Post by Del Piero on 2008-04-21
working fine after removing the amarok script!

---

