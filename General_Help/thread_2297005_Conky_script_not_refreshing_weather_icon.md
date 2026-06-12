---
title: "Conky script not refreshing weather icon"
date: 2015-09-30
forum: General Help
---

### Post by alain.roger on 2015-09-30
Hi,

i have the following conky script:
```

\
# --- Weather --- #
###################
# --- WOEID (Location id) --- #
${execi 300 curl -s "http://weather.yahooapis.com/forecastrss?w=820323&u=c" -o ~/.cache/weather.xml}
\
# --- Temperature --- #
#######################
\
${font ADELE :size=30}${voffset 0}\
${execi 300 grep "yweather:condition" ~/.cache/weather.xml | grep -o "temp=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}°${font ADELE :size=15}C\

# --- Weather icon --- #
########################
${execi 300 cp -f ~/.conky/outlineW/$(grep "yweather:condition" ~/.cache/weather.xml | grep -o "code=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*").png ~/.cache/weather-1.png}${image ~/.cache/weather-1.png -p 180,200 -s 80x80}
\
# --- Textual condition (e.g. Partly cloudy) --- #
##################################################
${font Roboto Light:size=14}${voffset -20}${offset 5}${execi 300 grep "yweather:condition" ~/.cache/weather.xml | grep -o "text=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}
\
# --- Icon - high temperature --- #
###################################
${image ~/.conky/arrow-up.png -p 175,300 -s 12x12}

# --- High temperature --- #
############################
${font Roboto Light :size=12}${offset 188}${voffset -32}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "high=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==1'}°

# --- Icon - low temperature icon --- #
#######################################
${image ~/.conky/arrow-down.png -p 232,300 -s 12x12}

# --- Low temperature --- #
###########################
${font Roboto Light :size=12}${offset 248}${voffset -76}${execi 300 grep "yweather:forecast" ~/.cache/weather.xml | grep -o "low=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*" | awk 'NR==1'}°

# --- Icon - map marker --- #
#############################
${image ~/.conky/map-marker.png -p 0,297 -s 20x16}

# --- Location name (city and country) --- #
############################################
${font Roboto Light :size=12}${offset 20}${voffset -75}${execi 300 grep "yweather:location" ~/.cache/weather.xml | grep -o "city=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}, ${execi 300 grep "yweather:location" ~/.cache/weather.xml | grep -o "country=\"[^\"]*\"" | grep -o "\"[^\"]*\"" | grep -o "[^\"]*"}
#${goto 285}${voffset -35}${font adele:bold:size=25}${time %p}
```

that is refreshed each second.

however the weather icon (even if it changes in weather.xml file / code value changing) is not refreshing to display the correct weather icon.
for example since this morning i have the night icon as following, while it's 4:30PM

[ATTACH=CONFIG]264752[/ATTACH]

If i type in console:
```
sudo killall conky
```
and next run my conky script, weather icon is refreshed correctly... but if weather changes, weather icon still displays the same icon...not refreshing.

why ?

thx.

---

