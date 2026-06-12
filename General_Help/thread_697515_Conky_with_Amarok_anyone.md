---
title: "Conky with Amarok anyone?"
date: 2008-02-15
forum: General Help
---

### Post by uberlube on 2008-02-15
As you guest, I have been trying to get Conky to show song info from amarok. I found this and threw it into the bottom of my .conkyrc and it shows up well enough:

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
${color blue}SYSTEM ${hr 1}${color}

Hostname: $alignr$nodename
Kernel: $alignr$kernel
Uptime: $alignr$uptime
Temp: ${alignr}${acpitemp}C

${color blue}CPU ${hr 1}${color}
${freq} MHz
Load: ${loadavg}   ${alignr}Temp: ${acpitemp}
$cpubar
Ram ${alignr}$mem / $memmax ($memperc%)
${membar 4}
swap ${alignr}$swap / $swapmax ($swapperc%)
${swapbar 4}

Highest CPU $alignr CPU% MEM%
${top name 1}$alignr${top cpu 1}${top mem 1}
${top name 2}$alignr${top cpu 2}${top mem 2}
${top name 3}$alignr${top cpu 3}${top mem 3}

Highest MEM $alignr CPU% MEM%
${top_mem name 1}$alignr${top_mem cpu 1}${top_mem mem 1}
${top_mem name 2}$alignr${top_mem cpu 2}${top_mem mem 2}
${top_mem name 3}$alignr${top_mem cpu 3}${top_mem mem 3}

${color blue}FILESYSTEM ${hr 1}${color}

Root: ${alignr}${fs_used /} / ${fs_size /}
${fs_bar 4 /}
Windows: ${alignr}${fs_used /media/sda3} / ${fs_size /media/sda3}
${fs_bar 4 /}


${color blue}NETWORK ${addr eth0} ${hr 1}$color

Down ${downspeed eth0} k/s ${alignr}Up ${upspeed eth0} k/s
${downspeedgraph eth0 25,107 000000 ff0000} ${alignr}${upspeedgraph eth0 25,107 000000 ff0000}
Total ${totaldown eth0} ${alignr}Total ${totalup eth0}

${color blue}AMAROK ${hr 1}$color

$color$stippled_hr${if_running amarokapp}
${color}${alignc}Now Playing${color white}
${alignc}${execi 10 ~/.conky/amarok artist}
${alignc}${execi 10 ~/.conky/amarok title}
${execibar 1 ~/.conky/amarok progress}
${alignc}"${execi 10 ~/.conky/amarok album}"
${alignc}${execi 10 ~/.conky/amarok year} - ${color white}${alignc}${execi 10 ~/.conky/amarok genre}
$color$stippled_hr
${alignc}Collection Information
Artists: ${color white}${execi 10 ~/.conky/amarok totalArtists} $color${alignr}Compilations: ${color white}${execi 10 ~/.conky/amarok totalCompilations}$color
Albums:  ${color white}${execi 10 ~/.conky/amarok totalAlbums} $color${alignr}Genres: ${color white}${execi 10 ~/.conky/amarok totalGenres}$color
Tracks:  ${color white}${execi 10 ~/.conky/amarok totalTracks}
$color$stippled_hr
${alignc}Collection Statisctics
Most songs by ${color white}${execi 10 ~/.conky/amarok most_songs_by_artist} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_songs_by_artist_n}${color})
Most songs are ${color white}${execi 10 ~/.conky/amarok most_songs_are_genre} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_songs_are_genre_n}${color})
Most songs during ${color white}${execi 10 ~/.conky/amarok most_songs_during_year} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_songs_during_year_n}${color})
Most albums by ${color white}${execi 10 ~/.conky/amarok most_albums_by_artist} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_albums_by_artist_n}${color})
Most albums are ${color white}${execi 10 ~/.conky/amarok most_albums_are_genre} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_albums_are_genre_n}${color})
Most albums during ${color white}${execi 10 ~/.conky/amarok most_albums_during_year} $alignr${color}(${color white}${execi 10 ~/.conky/amarok most_albums_during_year_n}${color})$endif 
```

It shows all of the proper fields but doesn't produce any song info. I did some looking around and what I have come up with is that Amarok somehow needs to use mySQL to share database info and I have to have a script placed in ~/.conky/amarok. Here is the script:

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

Herein lies the problem. From all the searching I did, all I found out is that the amarock script has to be in ~./conky/amarok  .... now I dont know if this is misinformation or if im just looking in the wrong place, but i have no directory called that. If anyone can give me detailed instructions on how to accomplish this, it would be much appreciated.

---

### Post by logos34 on 2008-02-15
>amarok>settings>configure>general options>show tray icon

run your cursor over the icon on your panel and the album, song and cover art popup.

Isn't that easier?

---

### Post by p_quarles on 2008-02-15
You can put the Amarok script wherever you want, you just have to make sure the path matches the path that conky calls. You also need to make sure the Amarok script itself is executed -- it needs its own entry in the startup sequence. It also needs to be made executable before it can run.

The script works fine -- I use it myself.

---

### Post by uberlube on 2008-02-15
Ya but why do that when I can needlessly use up my system resources to have another program tell me as well. :lolflag:

---

### Post by uberlube on 2008-02-15
Thanks P_Quarles ill give it a show and let u know if it works out.

---

### Post by p_quarles on 2008-02-15
Heh, just looked up the resource usage of the script (which is running currently) and it is dead last among everything on my system.

---

### Post by uberlube on 2008-02-15
Thanks again dude worked like a charm.

---

