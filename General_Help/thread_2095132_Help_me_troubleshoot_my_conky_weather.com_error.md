---
title: "Help me troubleshoot my conky weather.com error"
date: 2012-12-15
forum: General Help
---

### Post by hotwax on 2012-12-15
im using TeoBigusGeekus conkyforecast script [http://crunchbang.org/forums/viewtopic.php?id=19235](http://crunchbang.org/forums/viewtopic.php?id=19235)

this is the terminal output error

> sed: can't read High: No such file or directory
sed: can't read was: No such file or directory
sed: can't read 47: No such file or directory
cp: omitting directory `/home/manuel/Conky_WeatherCom/weather_com_images/Today\'s'


i checked for the /Today\'s' directory and it isnt there. i created these folders 
/home/manuel/Conky_WeatherCom/weather_com_images/Today\'s
/home/manuel/Conky_WeatherCom/weather_com_images/Today\'s'
/home/manuel/Conky_WeatherCom/weather_com_images/Today
/home/manuel/Conky_WeatherCom/weather_com_images/Today\

and it stll outputs the same error

EDIT:
now theres an additional error 

> rm: cannot remove `/home/manuel/Conky_WeatherCom/10days/10days_OK': Is a directory
cp: cannot stat `/home/manuel/Conky_WeatherCom/weather_com_images/29': No such file or directory


---

### Post by iamfbi on 2012-12-15
post .conkyrc, can't know what happen without .conkyrc file.

---

### Post by hotwax on 2012-12-16
/home/manuel/.conkyrc_weather_com
```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar,skip_pager
own_window_colour brown

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
use_xft yes

# Update interval in seconds
update_interval 3

# Minimum size of text area
minimum_size 355 500
maximum_width 355

override_utf8_locale yes

# Draw shades?
draw_shades yes

# Text stuff
draw_outline yes # amplifies text if yes
draw_borders no
#font freesans -12
xftfont Arial:size=9
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_inner_margin 9
border_outer_margin 0

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color cbcbcb


# Text alignment, other possible values are commented
#alignment top_left
alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 30

imlib_cache_size 0
text_buffer_size 2048
# stuff after 'TEXT' will be formatted on screen

TEXT
${texeci 600 bash /home/manuel/Conky_WeatherCom/weath_com}
```

shell script
/home/manuel/Conky_WeatherCom/weath_com   
```
#!/bin/bash

#put your 10 day weather.com address here
address10="http://www.weather.com/weather/tenday/New+York+NY+USNY0996:1:US"
#address10="http://www.weather.com/weather/tenday/Ojmjakon+RSXX0138:1:RS"
#address10="http://www.weather.com/weather/tenday/Kastoria+GRXX0292:1:GR"

addr_now=$(echo $address10|sed 's/tenday/right-now/')
addr_today=$(echo $address10|sed 's/tenday/today/')

kill -STOP $(pidof conky)
killall wget

wget --user-agent="Firefox" -O $HOME/Conky_WeatherCom/RightNow/raw_rn $addr_now
wget --user-agent="Firefox" -O $HOME/Conky_WeatherCom/Today/raw_td $addr_today
wget --user-agent="Firefox" -O $HOME/Conky_WeatherCom/10days/raw_10 $address10

rm $HOME/Conky_WeatherCom/10days/10days_OK

if [[ -s $HOME/Conky_WeatherCom/RightNow/raw_rn ]]; then
	#############
	# Right now #
	#############
	sed -i '/wx-weather-icon wx-hide/,/<div class="wx-next6hr-details ">/!d' $HOME/Conky_WeatherCom/RightNow/raw_rn
	sed -i -e '/^[ \t]*$/d' -e 's/\r//g' $HOME/Conky_WeatherCom/RightNow/raw_rn
	sed -i '/\.png\|&deg;\|weather-phrase\|feels-like\|"wx-temp"\|"wx-value"\|arrow wind-dir-/!d' $HOME/Conky_WeatherCom/RightNow/raw_rn
	sed -i -e 's/^.*wxicon\/120\///g' -e s'/png.*$/png/g' -e 's/^.*"wx-temp">//g' $HOME/Conky_WeatherCom/RightNow/raw_rn
	sed -i -e 's/^.*wx-dir-arrow wind-dir-//g' -e 's/"><\/div>.*$//g' -e 's/<\/span>.*$//g' -e 's/^.*">//g' -e 's/&deg;//g' $HOME/Conky_WeatherCom/RightNow/raw_rn
	image=$(sed -n 1p $HOME/Conky_WeatherCom/RightNow/raw_rn)
	if [[ $(sed -n 6p $HOME/Conky_WeatherCom/RightNow/raw_rn) == "Calm" ]]; then
		sed -i '6s/$/\n/' $HOME/Conky_WeatherCom/RightNow/raw_rn
	fi
    cp $HOME/Conky_WeatherCom/weather_com_images/$image $HOME/Conky_WeatherCom/now.png
fi

if [[ -s $HOME/Conky_WeatherCom/Today/raw_td ]]; then
	#############
	#   Today   #   
	#############
    sed -i '/<div class="wx-daypart/,/<div class="wx-tempgraph wx-module wx-grid3of6/!d' $HOME/Conky_WeatherCom/Today/raw_td
    sed -i -e '/^[ \t]*$/d' -e 's/^[ \t]*//g' -e 's/\r//g' $HOME/Conky_WeatherCom/Today/raw_td
    sed -i -e 's/^.*wx-observed">//g' -e 's/&deg;.*$//g' $HOME/Conky_WeatherCom/Today/raw_td
    sed -i -e 's/^.*wxicon\/120\///g' -e 's/\.png.*$/\.png/g' -e 's/^.*"wx-temp"> //g' $HOME/Conky_WeatherCom/Today/raw_td
    sed -i -e 's/^.*<h3>//g' -e 's/^.*"wx-phrase ">//g' -e 's/^.*<dt>//g' -e 's/^.*<dd>//g' $HOME/Conky_WeatherCom/Today/raw_td
    sed -i -e 's/^.*snowfall-value">//g' -e "s/<span class='wx-firstletter'>//g" -e 's/^.*<strong>//g' $HOME/Conky_WeatherCom/Today/raw_td
    sed -i -e 's/^.*<p class="wx-narrative">//g' -e 's/<sup>//g' -e 's/<\/sup>//g' -e 's/<span class=.*<\/span>//g' $HOME/Conky_WeatherCom/Today/raw_td
    sed -i -e 's/<.*$//g' -e '/^[ \t]*$/d' -e 's/Chance of rain/Chance of rain:/g' $HOME/Conky_WeatherCom/Today/raw_td
    sed -i -e :a -e '/:$/N; s/:\n/: /; ta' $HOME/Conky_WeatherCom/Today/raw_td
    sed -n '1,/Night/p' $HOME/Conky_WeatherCom/Today/raw_td > $HOME/Conky_WeatherCom/Today/day
    sed -n '/Night/,$p' $HOME/Conky_WeatherCom/Today/raw_td > $HOME/Conky_WeatherCom/Today/night
    sed -i '/Day\|Night/d' $HOME/Conky_WeatherCom/Today/{day,night}

    if (( $(cat $HOME/Conky_WeatherCom/Today/day|wc -l)==3 )); then
        line2=$(sed -n 2p $HOME/Conky_WeatherCom/Today/day)
        sed -i '2d' $HOME/Conky_WeatherCom/Today/day
        sed -i 1i$line2 $HOME/Conky_WeatherCom/Today/day
    fi

	day=$(sed -n 1p $HOME/Conky_WeatherCom/Today/day)
    cp $HOME/Conky_WeatherCom/weather_com_images/$day $HOME/Conky_WeatherCom/TD.png
    night=$(sed -n 1p $HOME/Conky_WeatherCom/Today/night)
    cp $HOME/Conky_WeatherCom/weather_com_images/$night $HOME/Conky_WeatherCom/TN.png

    fold -s30 $HOME/Conky_WeatherCom/Today/day > $HOME/Conky_WeatherCom/Today/day1
    sed -i 's/\(^.*: \)\(.*$\)/\$\{color ffe595\}\1\$\{color\}\2/g' $HOME/Conky_WeatherCom/Today/day1
    fold -s30 $HOME/Conky_WeatherCom/Today/night > $HOME/Conky_WeatherCom/Today/night1 
    sed -i 's/\(^.*: \)\(.*$\)/\$\{color ffe595\}\1\$\{color\}\2/g' $HOME/Conky_WeatherCom/Today/night1

    for (( i=1; i<=$(cat $HOME/Conky_WeatherCom/Today/night1|wc -l); i++ ))
        do
             sed -i "${i}s/^/\$\{goto 195\}/" $HOME/Conky_WeatherCom/Today/night1
        done
    paste -d'*' $HOME/Conky_WeatherCom/Today/{day1,night1} > $HOME/Conky_WeatherCom/Today/final_today
    sed -i 's/\*//g' $HOME/Conky_WeatherCom/Today/final_today
    
    j=$(cat $HOME/Conky_WeatherCom/Today/final_today|wc -l)
    if (( $j<16 )); then
		for (( i=1; i<=$(( 16-$j )); i++ ))
			do
				echo '' >> $HOME/Conky_WeatherCom/Today/final_today
			done
	fi
fi

if [[ -s $HOME/Conky_WeatherCom/10days/raw_10 ]]; then
	#############
	#  10 days  #
	#############
	observed_high=$(grep "Observed High" $HOME/Conky_WeatherCom/10days/raw_10|wc -l)
	sed -i '/"wx-daypart"/,/wx-planmyday10 wx-plan-day/!d' $HOME/Conky_WeatherCom/10days/raw_10
	sed -i -e '/^[ \t]*$/d' -e 's/\r//g' -e '/^$/d' -e 's/^[ \t]*//g' $HOME/Conky_WeatherCom/10days/raw_10
	sed -i -e 's/^.*wxicon\/70\///g' -e 's/\.png.*$/\.png/g' $HOME/Conky_WeatherCom/10days/raw_10
	sed -i -e 's/^.*"wx-temp"> \|"wx-temp-alt"> \|"wx-phrase">\|<dt>\|<dd>\|<h3>\|<p class=//g' $HOME/Conky_WeatherCom/10days/raw_10
	sed -i -e 's/<sup>&deg;.*$//g' -e 's/<\/p>\|<\/dd>.*$//g' -e '/<\|>\|^$/d' -e 's/ at / /g' $HOME/Conky_WeatherCom/10days/raw_10
	sed -i 's/ mph/mph/g' $HOME/Conky_WeatherCom/10days/raw_10
	
	line1=$(sed -n 1p $HOME/Conky_WeatherCom/10days/raw_10|sed 's/ *$//')
	if [[ $line1 == Tonight && $observed_high == 0 ]]; then
		sed -i '3s/$/\n-/' $HOME/Conky_WeatherCom/10days/raw_10
	fi
	
	for (( i=2; i<=65; i+=7 ))
	    do
	        image=$(sed -n ${i}p $HOME/Conky_WeatherCom/10days/raw_10)
	        cp $HOME/Conky_WeatherCom/weather_com_images/$image $HOME/Conky_WeatherCom/10_${i}.png
	    done
fi

line_count=$(cat $HOME/Conky_WeatherCom/10days/raw_10|wc -l)
if [[ $line_count == 70 ]]; then
	touch $HOME/Conky_WeatherCom/10days/10days_OK
fi

kill -CONT $(pidof conky)

```

do i replace $HOME/Conky_WeatherCom in the shell script with /home/manuel/ConkyWeatherCom     ?

---

### Post by hotwax on 2012-12-16
i got it to work by using a .conkyrc_weather instead of directing it to an executable but the alignment is really off. how can i fix this? 
my resolution is 1680x1050

im guessing i have to play with the config on the ${goto} alignment configs?

```
# Create own window instead of using desktop (required in nautilus)
own_window yes
own_window_type override
own_window_transparent yes
own_window_hints undecorated,below,skip_taskbar,skip_pager
own_window_colour brown

# Use double buffering (reduces flicker, may not work for everyone)
double_buffer yes

# fiddle with window
use_spacer right
use_xft yes

# Update interval in seconds
update_interval 3

# Minimum size of text area
minimum_size 355 500 #1680x1050
maximum_width 355

override_utf8_locale yes

# Draw shades?
draw_shades yes

# Text stuff
draw_outline no # amplifies text if yes
draw_borders no
#font freesans -12
xftfont Arial:size=9
uppercase no # set to yes if you want all text to be in uppercase

# Stippled borders?
stippled_borders 3

# border margins
border_inner_margin 9
border_outer_margin 0

# border width
border_width 10

# Default colors and also border colors, grey90 == #e5e5e5
default_color cbcbcb


# Text alignment, other possible values are commented
alignment top_left
#alignment top_right
#alignment bottom_left
#alignment bottom_right

# Gap between borders of screen and text
gap_x 10
gap_y 30

imlib_cache_size 0
text_buffer_size 2048
# stuff after 'TEXT' will be formatted on screen

TEXT
${font Arial:size=10}${color ffe595}RIGHT NOW ${font}${hr 2}${texeci 600 bash /home/manuel/Conky_WeatherCom/weath_com}
${font Arial:size=8}${execpi 600 sed -n '4p' /home/manuel/Conky_WeatherCom/RightNow/raw_rn}${font}

${goto 200}${color ffe595}TEMP: $color${alignr}${execpi 600 sed -n '3p' /home/manuel/Conky_WeatherCom/RightNow/raw_rn}°F (${execpi 600 sed -n '5p' /home/manuel/Conky_WeatherCom/RightNow/raw_rn}°F)${image /home/manuel/Conky_WeatherCom/now.png -p 0,30 -s 120x120}
${goto 200}${color ffe595}WIND: $color${alignr}${execpi 600 sed -n '6p' /home/manuel/Conky_WeatherCom/RightNow/raw_rn} ${execpi 600 sed -n '7p' /home/manuel/Conky_WeatherCom/RightNow/raw_rn}mph
${goto 200}${color ffe595}HUMIDITY: $color${alignr}${execpi 600 sed -n '8p' /home/manuel/Conky_WeatherCom/RightNow/raw_rn}
${goto 200}${color ffe595}DEW POINT: $color${alignr}${execpi 600 sed -n '9p' /home/manuel/Conky_WeatherCom/RightNow/raw_rn}°F
${goto 200}${color ffe595}VISIBILITY: $color${alignr}${execpi 600 sed -n '10p' /home/manuel/Conky_WeatherCom/RightNow/raw_rn}
${goto 200}${color ffe595}PRESSURE: $color${alignr}${execpi 600 sed -n '11p' /home/manuel/Conky_WeatherCom/RightNow/raw_rn}
${goto 200}${color ffe595}UV INDEX: $color${alignr}${execpi 600 sed -n '12p' /home/manuel/Conky_WeatherCom/RightNow/raw_rn}
######################
### TODAY - TONIGHT
######################
${font Arial:size=10}${color ffe595}TODAY - TONIGHT ${font}${hr 2}
${font Arial:size=8}${color ffe595}${goto 75}Today${goto 240}Tonight${image /home/manuel/Conky_WeatherCom/TD.png -p 35,170 -s 100x100}${image /home/manuel/Conky_WeatherCom/TN.png -p 200,170 -s 100x100}${font}${color}






${color ffe595}TEMP: ${color}${execpi 600 sed -n '2p' /home/manuel/Conky_WeatherCom/Today/day}°F${goto 195}${color ffe595}TEMP: ${color}${execpi 600 sed -n '2p' /home/manuel/Conky_WeatherCom/Today/night}°F
${execpi 600 sed -n '3,16p' /home/manuel/Conky_WeatherCom/Today/final_today}
${font Arial:size=12}${color ffe595}10 DAYS FORECAST ${font}${hr 2}
${font Arial:size=11}${color ffe595}${goto 65}${execpi 600 sed -n '1p' /home/manuel/Conky_WeatherCom/10days/raw_10}${goto 175}${execpi 600 sed -n '8p' /home/manuel/Conky_WeatherCom/10days/raw_10}${goto 285}${execpi 600 sed -n '15p' /home/manuel/Conky_WeatherCom/10days/raw_10}${color}${image /home/manuel/Conky_WeatherCom/10_2.png -p 20,500 -s 70x70}${image /home/manuel/Conky_WeatherCom/10_9.png -p 130,500 -s 70x70}${image /home/manuel/Conky_WeatherCom/10_16.png -p 240,500 -s 70x70}

${goto 115}${execpi 600 sed -n '3p' /home/manuel/Conky_WeatherCom/10days/raw_10}${goto 225}${execpi 600 sed -n '10p' /home/manuel/Conky_WeatherCom/10days/raw_10}${goto 335}${execpi 600 sed -n '17p' /home/manuel/Conky_WeatherCom/10days/raw_10}${font}
${goto 116}${execpi 600 sed -n '4p' /home/manuel/Conky_WeatherCom/10days/raw_10}${goto 226}${execpi 600 sed -n '11p' /home/manuel/Conky_WeatherCom/10days/raw_10}${goto 336}${execpi 600 sed -n '18p' /home/manuel/Conky_WeatherCom/10days/raw_10}

${execpi 600 sed -n '5p' /home/manuel/Conky_WeatherCom/10days/raw_10|cut -c1-18}${goto 135}${execpi 600 sed -n '12p' /home/manuel/Conky_WeatherCom/10days/raw_10|cut -c1-18}${goto 260}${execpi 600 sed -n '19p' /home/manuel/Conky_WeatherCom/10days/raw_10|cut -c1-18}
${color ffe595}PRECIP:${color}${execpi 600 sed -n '6p' /home/manuel/Conky_WeatherCom/10days/raw_10}${goto 135}${color ffe595}PRECIP:${color}${execpi 600 sed -n '13p' /home/manuel/Conky_WeatherCom/10days/raw_10}${goto 260}${color ffe595}PRECIP:${color}${execpi 600 sed -n '20p' /home/manuel/Conky_WeatherCom/10days/raw_10}
${color ffe595}WIND:${color}${execpi 600 sed -n '7p' /home/manuel/Conky_WeatherCom/10days/raw_10}${goto 135}${color ffe595}WIND:${color}${execpi 600 sed -n '14p' /home/manuel/Conky_WeatherCom/10days/raw_10}${goto 260}${color ffe595}WIND:${color}${execpi 600 sed -n '21p' /home/manuel/Conky_WeatherCom/10days/raw_10}
${color ffe595}${hr 1}
${font Arial:size=11}${goto 65}${execpi 600 sed -n '22p' /home/manuel/Conky_WeatherCom/10days/raw_10}${goto 175}${execpi 600 sed -n '29p' /home/manuel/Conky_WeatherCom/10days/raw_10}${goto 285}${execpi 600 sed -n '36p' /home/manuel/Conky_WeatherCom/10days/raw_10}${color}${image /home/manuel/Conky_WeatherCom/10_23.png -p 20,640 -s 70x70}${image /home/manuel/Conky_WeatherCom/10_30.png -p 130,640 -s 70x70}${image /home/manuel/Conky_WeatherCom/10_37.png -p 240,640 -s 70x70}

${goto 115}${execpi 600 sed -n '24p' /home/manuel/Conky_WeatherCom/10days/raw_10}${goto 225}${execpi 600 sed -n '31p' /home/manuel/Conky_WeatherCom/10days/raw_10}${goto 335}${execpi 600 sed -n '38p' /home/manuel/Conky_WeatherCom/10days/raw_10}${font}
${goto 116}${execpi 600 sed -n '25p' /home/manuel/Conky_WeatherCom/10days/raw_10}${goto 226}${execpi 600 sed -n '32p' /home/manuel/Conky_WeatherCom/10days/raw_10}${goto 336}${execpi 600 sed -n '39p' /home/manuel/Conky_WeatherCom/10days/raw_10}

${execpi 600 sed -n '26p' /home/manuel/Conky_WeatherCom/10days/raw_10|cut -c1-18}${goto 135}${execpi 600 sed -n '33p' /home/manuel/Conky_WeatherCom/10days/raw_10|cut -c1-18}${goto 260}${execpi 600 sed -n '40p' /home/manuel/Conky_WeatherCom/10days/raw_10|cut -c1-18}
${color ffe595}PRECIP:${color}${execpi 600 sed -n '27p' /home/manuel/Conky_WeatherCom/10days/raw_10}${goto 135}${color ffe595}PRECIP:${color}${execpi 600 sed -n '34p' /home/manuel/Conky_WeatherCom/10days/raw_10}${goto 260}${color ffe595}PRECIP:${color}${execpi 600 sed -n '41p' /home/manuel/Conky_WeatherCom/10days/raw_10}
${color ffe595}WIND:${color}${execpi 600 sed -n '28p' /home/manuel/Conky_WeatherCom/10days/raw_10}${goto 135}${color ffe595}WIND:${color}${execpi 600 sed -n '35p' /home/manuel/Conky_WeatherCom/10days/raw_10}${goto 260}${color ffe595}WIND:${color}${execpi 600 sed -n '42p' /home/manuel/Conky_WeatherCom/10days/raw_10}
${color ffe595}${hr 1}
${font Arial:size=11}${goto 50}${execpi 600 sed -n '43p' /home/manuel/Conky_WeatherCom/10days/raw_10}${goto 135}${execpi 600 sed -n '50p' /home/manuel/Conky_WeatherCom/10days/raw_10}${goto 220}${execpi 600 sed -n '57p' /home/manuel/Conky_WeatherCom/10days/raw_10}${if_existing /home/teo/Conky_WeatherCom/10days/10days_OK}${goto 305}${execpi 600 sed -n '64p' /home/manuel/Conky_WeatherCom/10days/raw_10}${endif}${color}${image /home/manuel/Conky_WeatherCom/10_44.png -p 0,780 -s 55x55}${image /home/manuel/Conky_WeatherCom/10_51.png -p 85,780 -s 55x55}${image /home/manuel/Conky_WeatherCom/10_58.png -p 170,780 -s 55x55}${if_existing /home/teo/Conky_WeatherCom/10days/10days_OK}${image /home/manuel/Conky_WeatherCom/10_58.png -p 255,780 -s 55x55}${endif}${font}

${goto 75}${execpi 600 sed -n '45p' /home/manuel/Conky_WeatherCom/10days/raw_10}${goto 160}${execpi 600 sed -n '52p' /home/manuel/Conky_WeatherCom/10days/raw_10}${goto 245}${execpi 600 sed -n '59p' /home/manuel/Conky_WeatherCom/10days/raw_10}${if_existing /home/teo/Conky_WeatherCom/10days/10days_OK}${goto 330}${execpi 600 sed -n '66p' /home/manuel/Conky_WeatherCom/10days/raw_10}${endif}
${goto 76}${execpi 600 sed -n '45p' /home/manuel/Conky_WeatherCom/10days/raw_10}${goto 160}${execpi 600 sed -n '53p' /home/manuel/Conky_WeatherCom/10days/raw_10}${goto 245}${execpi 600 sed -n '60p' /home/manuel/Conky_WeatherCom/10days/raw_10}${if_existing /home/teo/Conky_WeatherCom/10days/10days_OK}${goto 330}${execpi 600 sed -n '67p' /home/manuel/Conky_WeatherCom/10days/raw_10}${endif}

${execpi 600 sed -n '47p' /home/manuel/Conky_WeatherCom/10days/raw_10|cut -c1-12}${goto 95}${execpi 600 sed -n '54p' /home/manuel/Conky_WeatherCom/10days/raw_10|cut -c1-12}${goto 180}${execpi 600 sed -n '61p' /home/manuel/Conky_WeatherCom/10days/raw_10|cut -c1-12}${if_existing /home/teo/Conky_WeatherCom/10days/10days_OK}${goto 265}${execpi 600 sed -n '68p' /home/manuel/Conky_WeatherCom/10days/raw_10|cut -c1-12}${endif}
${execpi 600 sed -n '47p' /home/manuel/Conky_WeatherCom/10days/raw_10|cut -c13-24}${goto 95}${execpi 600 sed -n '54p' /home/manuel/Conky_WeatherCom/10days/raw_10|cut -c13-24}${goto 180}${execpi 600 sed -n '61p' /home/manuel/Conky_WeatherCom/10days/raw_10|cut -c13-24}${if_existing /home/teo/Conky_WeatherCom/10days/10days_OK}${goto 265}${execpi 600 sed -n '68p' /home/manuel/Conky_WeatherCom/10days/raw_10|cut -c13-24}${endif}
${color ffe595}PR:${color}${execpi 600 sed -n '48p' /home/manuel/Conky_WeatherCom/10days/raw_10}${goto 95}${color ffe595}PR:${color}${execpi 600 sed -n '55p' /home/manuel/Conky_WeatherCom/10days/raw_10}${goto 180}${color ffe595}PR:${color}${execpi 600 sed -n '62p' /home/manuel/Conky_WeatherCom/10days/raw_10}${if_existing /home/teo/Conky_WeatherCom/10days/10days_OK}${goto 265}${color ffe595}PR:${color}${execpi 600 sed -n '69p' /home/manuel/Conky_WeatherCom/10days/raw_10}${endif}
${color ffe595}W:${color}${execpi 600 sed -n '49p' /home/manuel/Conky_WeatherCom/10days/raw_10}${goto 95}${color ffe595}W:${color}${execpi 600 sed -n '56p' /home/manuel/Conky_WeatherCom/10days/raw_10}${goto 180}${color ffe595}W:${color}${execpi 600 sed -n '63p' /home/manuel/Conky_WeatherCom/10days/raw_10}${if_existing /home/teo/Conky_WeatherCom/10days/10days_OK}${goto 265}${color ffe595}W:${color}${execpi 600 sed -n '70p' /home/manuel/Conky_WeatherCom/10days/raw_10}${endif}

```

---

