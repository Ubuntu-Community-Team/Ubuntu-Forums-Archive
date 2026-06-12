---
title: "Conky Wether stopped working"
date: 2013-12-22
forum: General Help
---

### Post by MichaelGld on 2013-12-22
I have been using the same Conkys for some time now with no problem. This past week the weather section no longer displays. When I run it from the command line, it throws up the following errors.

```
michael@michael-desktop ~ $ conky -c ~/v9000/conky_weather
Conky: desktop window (e00029) is subwindow of root window (262)
Conky: window type - normal
Conky: drawing to created window (0x4400002)
Conky: drawing to double buffer
gathering data with curl
  % Total    % Received % Xferd  Average Speed   Time    Time     Time  Current
                                 Dload  Upload   Total   Spent    Left  Speed
100 85278  100 85278    0     0  82415      0  0:00:01  0:00:01 --:--:--  177k
you have no weather alerts
Conky: llua_do_call: function conky_weather execution failed: /home/michael/v9000/v9000.lua:354: bad argument #1 to 'find' (string expected, got nil)

```

The error repeats until I press CTRL-C. Here are the files I have been using to run Conky.

conky-start1.sh
```
#!/bin/bash

sleep 20 &&
# conky -c ./.conky/.conkyrc &
conky -c ~/.conkyrc &
conky -c ~/v9000/conky_weather
```

.conkyrc
```
#own_window yes
#own_window_class Conky
#own_window_type normal 
#own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager  
#own_window_transparent yes

alignment top_right
background no
border_width 0
cpu_avg_samples 2
default_color white
default_outline_color black
default_shade_color black
double_buffer yes
draw_borders no
draw_graph_borders yes
draw_outline no
draw_shades yes
use_xft yes
# xftfont terminus:size=11
xftfont terminus:size=9.5
gap_x 10
gap_y 50
# maximum_width 320
maximum_width 420
# minimum_size 300 100
minimum_size 320 100
net_avg_samples 2
no_buffers yes
out_to_console no
out_to_stderr no
extra_newline no
own_window yes
own_window_class Conky
own_window_transparent yes
# own_window_transparent no
# own_window_type override
# own_window_type desktop
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
stippled_borders 0
update_interval 1.0
uppercase no
use_spacer none
show_graph_scale no
show_graph_range no
text_buffer_size 4096
temperature_unit fahrenheit

#lua_load ~/v9000.lua
#lua_draw_hook_pre weather
#lua_load ~/v9000/weather_script.lua

TEXT
${voffset -33}${font OpenLogos:size=90}${color2}v${font}${voffset -59}${goto 178}${font UbuntuTitleBold:size=20}${color4}Mint 14${font} 
${font DejaVu Sans Mono:bold:size=11}Time: ${time %k:%M:%S}${alignr}${time %a %b %d, %Y}${font}
# ${font Terminus:style=bold:size=11}SYSTEM $hr${font}
${font DejaVu Sans Mono:bold:size=11}SYSTEM $hr${font}
Uptime: $uptime 
#Updates: ${alignr}${color1}${execi 360 apt-get search "~U" | wc -l | tail}${color} ${color2}Packages${color}${font}
#Updates Available: ${execi 1200 aptitude search "~U" | wc -l | tail}${font}
Mint Version: Mint ${pre_exec lsb_release -r -s} Nadia
Cinnamon Version: ${execi 1200 cinnamon --version}
Conky:${conky_version} for ${conky_build_arch}
$sysname $kernel $machine
Speed ${freq}MHz   Load: ${loadavg}
#Fan state ${acpifan}
#UPS Load: ${apcupsd_load}
#UPS Load: ${apcupsd_load 127.0.0.1 3551}
#UPS Model: ${apcupsd_model}
#UPS Status: ${apcupsd_status 127.0.0.1 3551}
#UPS Time Remaining: ${apcupsd_timeleft 127.0.0.1 3551} min.
#UPS Loadgauge: ${apcupsd_loadgauge 27,92}
#UPS Load Graph: ${apcupsd_loadgraph 14,80 CE5C00}
${color light blue}
#${font Terminus:style=bold:size=11}PROCESSORS $hr
${font DejaVu Sans Mono:bold:size=11}PROCESSORS $hr
${font}CPU:$alignr AMD ${exec cat /proc/cpuinfo | grep 'model name' | sort -u | cut -c 18-59}
#$alignr ${execi 600 sensors -f |awk '/Core 0/ {cut=index($3, "F"); print(substr($3, 2, cut - 3))}'}
#${font Terminus:size=9}CPU TEMP: ${acpitemp}°C
#CPU TEMP: ${execi 8 sensors | grep -A 1 'temp1' | cut -c15-18 | sed '/^$/d'}°C  
#CPU - ${execi 60 sensors | grep -A 0 'temp2' | cut -c 15-21} ºC
#CPU Core 1 Temp: $alignr${execi 600 sensors -f | grep 'Core 0' | awk '{print $3}'}
#CPUtemp: $alignr${execi 60 sensors | grep 'CPU Temperature' | cut -c 22-28} 
#CPUTemp ${execi 8 sensors | grep -A 1 'temp2' | cut -c13-16 | sed '/^$/d'}C
#${offset 5}CPUfan: $alignr${hwmon fan 0} RPM
#${offset 5}MBtemp: $alignr${hwmon temp 2}°F
#${offset 5}CPUtemp: $alignr${hwmon temp 1}°F
${font}CPU1: ${cpu cpu0}% ${cpubar cpu0}
CPU2: ${cpu cpu1}% ${cpubar cpu1}
CPU3: ${cpu cpu2}% ${cpubar cpu2}
CPU4: ${cpu cpu3}% ${cpubar cpu3}
${color pink}
${font DejaVu Sans Mono:bold:size=11}MEMORY $hr
${font}RAM ${alignc}     $mem/$memmax  $alignr $memperc%
${membar}
Swap:  ${alignc} $swap/$swapmax $alignr $swapperc%
${swapbar 6}
${color white} 
${font DejaVu Sans Mono:bold:size=11}GRAPHICS $hr
${font}GPU TEMP: ${nvidia temp }°F${font Terminus:size=8} 
${execp ~/conkygraphics.sh}${font}
${color orange}
${font DejaVu Sans Mono:bold:size=11}DISKS $hr
${font}Root ${font}/ $alignc ${fs_used /}/ ${fs_size /} $alignr ${fs_used_perc /}%
${fs_bar /}
HOME: ${alignc }${fs_free /home} /${fs_size /home} $alignr ${fs_used_perc /home}%
${fs_bar /home}
#${diskiograph}
BOX.COM: ${alignc }${fs_free /home/michael/box.com} /${fs_size /home/michael/box.com} $alignr ${fs_used_perc /home/michael/box.com}%
${fs_bar /home/michael/box.com}
${diskiograph}
#HDD1: ${execi 10 hddtemp -n -u f /dev/sda}°F ${alignr}HDD2: ${execi 10 hddtemp -n -u f /dev/sdb}°F
#HDD1 Temp: ${execi 5 hddtemp /dev/sda | cut -c 34-38} ${alignr}HDD2 Temp: ${execi 5 hddtemp /dev/sdb | cut -c 24-28}
#HDD1 Temp: ${execi 5 hddtemp /dev/sda | cut -c 24-28} ${alignr}HDD2 Temp: ${execi 5 hddtemp /dev/sdb | cut -c 34-38}
#HDD1 Temp:{hddtemp /dev/sda 127.0.0.1 7634}${alignr}HDD2 Temp:{hddtemp /dev/sdb 127.0.0.1 7634}
#HDD1 Temp:${execi 300 nc localhost 7634 | cut -c34-36}&#7506;C
#HDD1 Temp:${execpi 300 hddtemp /dev/sda | cut -c24-27}
#HDD1 Temp:${execi 10 hddtemp --unit=F /dev/sda | cut -b11-28;}
HDD1 Temp:${execi 10 hddtemp --unit=F /dev/sda | cut -b33-38;}${alignr}HDD2 Temp:${execi 10 hddtemp --unit=F /dev/sdb | cut -b24-30;}
${font DejaVu Sans Mono:bold:size=11}DROPBOX $hr${font}
${execi 60 du -c ~/Dropbox | awk  'BEGIN{Size=3.63} /total/ {Used=$1/1048576;printf"Size: %.1f GB",Size;printf " Used: %.1f GB",Used;printf " Free: %.1fGB\n",Size-Used}'}
#${execibar 60 $HOME/dropbox.sh}
${execibar 60 du -c ~/Dropbox | awk  '/total/ {print $1/10485.76/3.63}' }
${color green}
${font DejaVu Sans Mono:bold:size=11}TOP PROCESSES $hr${font}
${top name 1}$alignc${top mem 1}$alignr${top cpu 1}%
${top name 2}$alignc${top mem 2}$alignr${top cpu 2}%
${top name 3}$alignc${top mem 3}$alignr${top cpu 3}%
${top name 4}$alignc${top mem 4}$alignr${top cpu 4}%
${color red}
${font DejaVu Sans Mono:bold:size=10}
#${execp /home/michael/gcal.sh}
#${voffset -40}${head /home/michael/gcal.txt 10 20}
${voffset -40}
${color yellow}${font DejaVu Sans Mono:bold:size=11}NETWORK $hr${font}
D/L: ${downspeed eth1}/s $alignc ${voffset -1}${downspeedgraph eth1 14,80 582D10 E08000} $alignr ${voffset -1}${totaldown eth1}
${voffset 8}U/L: ${upspeed eth1}/s $alignc${voffset 3} ${upspeedgraph eth1 14,80 582D10 E08000}$alignr${voffset -1}${totalup eth1}
#CE5C00
##WORKS
#Today:${goto 60}${execi 300 vnstat -d | grep "`date +"%D"`" | awk '{print $2 $3}'}${goto 150} Today:${goto 210}${execi 300 vnstat | grep "`date #+"D"`" | awk '{print $5 $6}'}  
#Week:${goto 60}${execi 300 vnstat -w | grep "current week" | awk '{print $3 $4}'}${goto 150} Week:${goto 210}${execi 300 vnstat -w | grep "current #week" | awk '{print $6 $7}'} 
#Month:${goto 60}${execi 300 vnstat -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${goto 150} Month:${goto 210}${execi 300 vnstat -m | grep #"`date +"%b '%y"`" | awk '{print $6 $7}'}

#NEW 3/31/2012
#${goto 90}${font DejaVu Sans Mono:bold:size=11}INTERNET USAGE
#${font DejaVu Sans Mono:bold:size=11}LAN SUMMARY $hr
${font}
${voffset -18}
Local IP: ${alignr}${addr eth1}
External IP: ${alignr}${execi 3600 wget -q -O - checkip.dyndns.org | sed -e 's/[^[:digit:]\|.]//g'}
${if_existing /proc/net/route eth1}
${font DejaVu Sans Mono:bold:size=11}INTERNET USAGE $hr${font}
#${hr 1}

Downloads${goto 170}Uploads${font DejaVu Sans Mono:size=7}
Today:${goto 60}${execi 300 vnstat -i eth1 | grep "today" | awk '{print $2 $3}'}${goto 170}Today:${goto 230}${execi 300 vnstat -i eth1 | grep "today" | awk '{print $5 $6}'}
Yesterday:${goto 60}${execi 300 vnstat -i eth1 | grep "yesterday" | awk '{print $2 $3}'}${goto 170}Yesterday:${goto 230}${execi 300 vnstat -i eth1 | grep "yesterday" | awk '{print $5 $6}'}
Week:${goto 60}${execi 300 vnstat -i eth1 -w | grep "current week" | awk '{print $3 $4}'}${goto 170}Week:${goto 230}${execi 300 vnstat -i eth1 -w | grep "current week" | awk '{print $6 $7}'} 
Month:${goto 60}${execi 300 vnstat -i eth1 -m | grep "`date +"%b '%y"`" | awk '{print $3 $4}'}${goto 170}Month:${goto 230}${execi 300 vnstat -i eth1 -m | grep "`date +"%b '%y"`" | awk '{print $6 $7}'}
${endif}
```

conky_weather
```
##############################################
#  Settings
##############################################
max_specials 10000
max_user_text 1500000
background no
use_xft yes
#xftfont Sans:size=12
#xftalpha 1
font Mono:size=8
total_run_times 0
own_window yes
own_window_argb_visual yes
own_window_transparent yes
own_window_type normal
own_window_hints undecorated,below,sticky,skip_taskbar,skip_pager
double_buffer yes
minimum_size 600 600
maximum_width 600
draw_shades no
draw_outline no
draw_borders no
draw_graph_borders yes
default_color white
default_shade_color black
default_outline_color white
#alignment top_right
alignment bottom_left
gap_x 10
gap_y 10
no_buffers yes
uppercase no
cpu_avg_samples 2
override_utf8_locale yes
color1 86acad #darker blue
color2 b1c9c9 #lighter blue
text_buffer_size 100000
top_name_width 10
update_interval 1

lua_load ~/v9000/v9000.lua
lua_draw_hook_pre weather
#lua_load ~/v9000/weather_testing.lua
#lua_load ~/v9000/weather_script.lua
lua_load ~/v9000/s11template.lua
#lua_load ~/v9000/s11template-new.lua
#lua_load ~/v9000/chronograph-mrpeachy_24.lua

TEXT
${goto 230}${cpu}
```

v9000.lua
```
--weather v9000 by mrpeachy 01/10/12; released: Feb 23, 2012
require 'cairo'
require 'imlib2'
local username = os.getenv("USERNAME")
--you can enter your username here in case of errors, 
--enter username in quotes like this username = "yourname"
local username = username  
package.path = '/home/michael/.v9000_config.lua'
require '.v9000_config'
start=1
--INITIALIZE SETTINGS-- need only be run once
settings_table=weather_settings()
--##################################
--######## main function ########### 
function conky_weather()--##########
--##################################
if conky_window == nil then return end
local cs = cairo_xlib_surface_create(conky_window.display, conky_window.drawable, conky_window.visual, conky_window.width, conky_window.height)
cr = cairo_create(cs)
local updates=tonumber(conky_parse('${updates}'))
--###UNCOMMENT THE BELOW LINE TO ENABLE CPU DELAY##########################################################
--if updates>5 then--###### YOU WILL ALSO HAVE TO UNCOMMENT THE MATCHING end ON LINE 923 ####################
--#########################################################################################################
local testing=0--this setting is for script testing, if not in testing set to 0
--#########################################################################################################
--############start of timed section#######################################################################
--#########################################################################################################
local timer=(updates %tonumber(settings_table[1]))
--################################################
if timer==0 or start==1 then--######
start=nil--#######################################
local web=settings_table[2]
local alert_check=settings_table[13]
--################################################
print ("gathering data with curl")
local f=io.popen("curl --max-time 60 '"..web.."' | sed 's/%//g'")
allweatherdata=f:read("*a")
f:close()
allweatherdata=string.gsub(allweatherdata,"[\n\r]","")
testall=string.find(allweatherdata,">10 Day Forecast&nbsp")
--CHECK FOR WEATHER ALERTS
if testall~=nil and alert_check==1 then
local alert=string.find(allweatherdata,"Severe Weather Alert!")
    if alert~=nil then
    print ("getting weather alerts")
    --get alert web
    local a,b,alertchunk=string.find(allweatherdata,">Local Information</div>(.*)>Severe Weather Alert!<")
    local a,b,alertsite=string.find(alertchunk,"><a href=%p(.*)%p><img src=")
    local f=io.popen("curl --max-time 60 'http://www.intellicast.com"..alertsite.."' | sed 's/%//g'")
    alertdata=f:read("*a")
    f:close()
    alertdata=string.gsub(alertdata,"[\n\r]","")
    alerttest=string.find(alertdata,"%a")
    else
    print ("you have no weather alerts")
    alerttest=0
    end--if alert~=nil
else
print ("not checking for alerts")
alerttest=1
end--if testall and alert check
processall=1
end--of timed data gathering section
--#########################################################################

--#########################################################################
--in case curl craps up it should retry until it works
if testall==nil or  alerttest==nil then
print ("curl attempt timed out, trying again")
local web=settings_table[2]
local alert_check=settings_table[13]
local f=io.popen("curl --max-time 60 '"..web.."' | sed 's/%//g'")
allweatherdata=f:read("*a")
f:close()
allweatherdata=string.gsub(allweatherdata,"[\n\r]","")
testall=string.find(allweatherdata,">10 Day Forecast&nbsp")
--CHECK FOR WEATHER ALERTS
if testall~=nil and alert_check==1 then
local alert=string.find(allweatherdata,"Severe Weather Alert!")
    if alert~=nil then
    print ("getting weather alerts")
    --get alert web
    local a,b,alertchunk=string.find(allweatherdata,">Local Information</div>(.*)>Severe Weather Alert!<")
    local a,b,alertsite=string.find(alertchunk,"><a href=%p(.*)%p><img src=")
    local f=io.popen("curl --max-time 60 'http://www.intellicast.com"..alertsite.."' | sed 's/%//g'")
    alertdata=f:read("*a")
    f:close()
    alertdata=string.gsub(alertdata,"[\n\r]","")
    alerttest=string.find(alertdata,"%a")
    else
    print ("you have no weather alerts")
    alerttest=0
    end--if alert~=nil
else
print ("not checking for alerts")
alerttest=1
end--if testall and alert_check
processall=1
end--if testall==nil
--end or curl reruns ######################################################

--START PROCESSING ###########################################################################
if testall~=nil and alerttest~=nil and processall==1 then
local weathericons=settings_table[3]
local con_short=settings_table[4]
local visibility_unit=settings_table[6]
local wind_mph_unit=settings_table[7]
local wind_km_unit=settings_table[8]
local wind_kts_unit=settings_table[9]
local ceiling_unit=settings_table[10]
local wind_degrees_unit=settings_table[11]
local translate=settings_table[12]
local alert_check=settings_table[13]
--#########################################################################
--LOAD TRANSLATE TABLES IF TRANSLATE SETTING = 1
    if translate==1 then
    monthshort=settings_table[21]
    monthnames=settings_table[20]
    dayhort=settings_table[19]
    daynames=settings_table[18]
    neswtext=settings_table[14]
    tsuffix=settings_table[15]
    uvindextext=settings_table[16]
    moonphases=settings_table[17]
    additional=settings_table[22]
    else--neswtext,tsuffix,uvindextext,moonphases,daynames,dayshort,monthnames,monthshort
    dayshort={Monday="Mon",Tuesday="Tue",Wednesday="Wed",Thursday="Thu",Friday="Fri",Saturday="Sat",Sunday="Sun"}
    monthshort={January="Jan",February="Feb",March="Mar",April="Apr",May="May",June="Jun",July="Jul",August="Aug",September="Sep",October="Oct",November="Nov",December="Dec"}
    end--end if translate =1
--#########################################################################
--process data tables
--intellicast to conky weather icon conversion
wimage={
wx_65="32",  -- Clear
wx_66="30",  -- Partly Cloudy
wx_67="26",  -- Cloudy
wx_68="32",  -- Clear
wx_69="28",  -- Mostly Cloudy
wx_70="20",  -- Fog
wx_71="32",  -- Clear
wx_72="21",  -- Haze
wx_73="36",  -- Hot
wx_74="14",  -- Light Snow Showers
wx_75="28",  -- Mostly Cloudy
wx_76="18",  -- Sleet
wx_77="14",  -- Light Snow Showers
wx_78="23",  -- Blustery
wx_79="05",  -- Mixed Rain and Snow
wx_80="15",  -- Drifting Snow
wx_81="15",  -- Drifting Snow
wx_82="11",  -- Light Rain
wx_83="16",  -- Snow
wx_84="00",  -- Tornado
wx_85="32",  -- Clear
wx_86="25",  -- N/A
wx_87="09",  -- Drizzle
wx_88="05",  -- Mixed Rain and Snow
wx_89="18",  -- Sleet
wx_90="18",  -- Sleet
wx_91="39",  -- Scattered Showers
wx_92="39",  -- Scattered Showers
wx_93="39",  -- Scattered Showers
wx_94="39",  -- Scattered Showers
wx_95="37",  -- Isolated Thunderstorms
wx_96="37",  -- Isolated Thunderstorms
wx_97="31",  -- Clear
wx_98="29",  -- Partly Cloudy
wx_99="27",  -- Mostly Cloudy
wx_100="47",  -- Isolated Thunderstorms
wx_101="47",  -- Isolated Thunderstorms
wx_102="33",  -- Fair
wx_103="26",  -- Cloudy
wx_104="20",  -- Fog
wx_105="45",  -- Scattered Showers
wx_106="45",  -- Scattered Showers
wx_107="11",  -- Light Rain
wx_108="46",  -- Snow Showers
wx_109="46",  -- Snow Showers
wx_110="06",  -- Mixed Rain and Sleet
wx_111="18",  -- Sleet
wx_112="06",  -- Mixed Rain and Sleet
wx_113="46",  -- Snow Showers
wx_114="46",  -- Snow Showers
wx_115="31",  -- Clear
wx_116="47",  -- Isolated Thunderstorms
}--end w image table
--convert intellicast icons to weather font
wfont={
wx_65="a",
wx_66="c",
wx_67="f",
wx_68="a",
wx_69="d",
wx_70="0",
wx_71="a",
wx_72="9",
wx_73="5",
wx_74="p",
wx_75="d",
wx_76="w",
wx_77="p",
wx_78="6",
wx_79="x",
wx_80="8",
wx_81="8",
wx_82="h",
wx_83="q",
wx_84="m",
wx_85="a",
wx_86="-",
wx_87="h",
wx_88="x",
wx_89="w",
wx_90="w",
wx_91="g",
wx_92="g",
wx_93="g",
wx_94="g",
wx_95="k",
wx_96="k",
wx_97="A",
wx_98="C",
wx_99="D",
wx_100="K",
wx_101="K",
wx_102="B",
wx_103="f",
wx_104="0",
wx_105="G",
wx_106="G",
wx_107="h",
wx_108="O",
wx_109="O",
wx_110="x",
wx_111="w",
wx_112="x",
wx_113="O",
wx_114="O",
wx_115="A",
wx_116="K",
}--end w font table
--conversion day and month tables
moonfontt={
["New"]="@",
["Full"]="=",
["First Quarter"]="T",
["Last Quarter"]="G",
["Waning Gibbous"]="D",
["Waning Crescent"]="J",
["Waxing Crescent"]="Q",
["Waxing Gibbous"]="W",
}--end of moon font table
moonicont={
["New"]=weathericons.."moon_new.png",
["Full"]=weathericons.."moon_full.png",
["First Quarter"]=weathericons.."moon_first_quarter.png",
["Last Quarter"]=weathericons.."moon_last_quarter.png",
["Waning Gibbous"]=weathericons.."moon_waning_gibbous.png",
["Waning Crescent"]=weathericons.."moon_waning_crescent.png",
["Waxing Crescent"]=weathericons.."moon_waxing_crescent.png",
["Waxing Gibbous"]=weathericons.."moon_waxing_gibbous.png",
}--end of moon icon table
windfontt={
S="9",
SSW=":",
SW=";",
WSW="<",
W="=",
WNW=">",
NW="?",
NNW="@",
N="1",
NNE="2",
NE="3",
ENE="4",
E="5",
ESE="6",
SE="7",
SSE="8"
}--end of wind direction font table
--#########################################################################

--#########################################################################
--setup tables for forecast weather
forecast_day={}
forecast_day_caps={}
forecast_day_lc={}
forecast_day_short={}
forecast_day_short_caps={}
forecast_day_short_lc={}
forecast_month={}
forecast_month_caps={}
forecast_month_lc={}
forecast_month_short={}
forecast_month_short_caps={}
forecast_month_short_lc={}
forecast_date={}
weather_icon={}
weather_font={}
high_temp={}
low_temp={}
conditions={}
conditions_caps={}
conditions_lc={}
conditions_short={}
conditions_short_caps={}
conditions_short_lc={}
sun_rise={}
sun_rise_lc={}
sun_rise_time={}
moon_rise={}
moon_rise_lc={}
moon_rise_time={}
moon_rise_ampm={}
moon_rise_ampm_lc={}
sun_set={}
sun_set_lc={}
sun_set_time={}
moon_set={}
moon_set_lc={}
moon_set_time={}
moon_set_ampm={}
moon_set_ampm_lc={}
humidity={}
precipitation={}
snow={}
cloud_cover={}
moon_phase={}
moon_phase_caps={}
moon_phase_lc={}
moon_font={}
moon_icon={}
wind_mph={}
wind_km={}
wind_kts={}
wind_font={}
wind_icon={}
wind_deg={}
wind_nesw={}
uv_index_num={}
uv_index_txt={}
uv_index_txt_caps={}
uv_index_txt_lc={}
--#########################################################################

--#########################################################################
--get forecast chunk
local a,b,allweather=string.find(allweatherdata,">10 Day Forecast&nbsp(.*)>More from Intellicast</div>")
--extract information into tables
local start=0
local f=1
while f~=nil do
--match forecast day name and date
local s,f,t=string.find(allweather,"<td colspan=\"2\"><strong>([%a,%s%d]*)</strong></td>",start)
    if t~=nil then
    --split name from month and date
    local a,b,day=string.find(t,"(%a*),%s")
    local a,b,month=string.find(t,",%s(%a*)%s")
    local a,b,date=string.find(t,"(%d*)$")
    --ser day names, regular, caps, lowercase and short
    table.insert(forecast_day_short,dayshort[day])
    table.insert(forecast_day_short_caps,string.upper(dayshort[day]))
    table.insert(forecast_day_short_lc,string.lower(dayshort[day]))
        if translate==1 then
        day=daynames[day]
        else
        day=day
        end
    table.insert(forecast_day,day)
    table.insert(forecast_day_caps,string.upper(day))
    table.insert(forecast_day_lc,string.lower(day))
    --set month types
    table.insert(forecast_month_short,monthshort[month])
    table.insert(forecast_month_short_caps,string.upper(monthshort[month]))
    table.insert(forecast_month_short_lc,string.lower(monthshort[month]))
        if translate==1 then
        month=monthnames[month]
        else
        month=month
        end
    table.insert(forecast_month,month)
    table.insert(forecast_month_caps,string.upper(month))
    table.insert(forecast_month_lc,string.lower(month))
    --set date
    table.insert(forecast_date,date)
    end--if t~= nil
--intellicast weather icon match
local s,f,t=string.find(allweather,"40_white/(wx_[%d]*).png\"",start)
--convert to conkyweather icon
    if t~=nil then
    table.insert(weather_icon,weathericons..wimage[t]..".png")
    --convert to weather font
    table.insert(weather_font,wfont[t])
    end
--match conditions
local s,f,t=string.find(allweather," /><br />([%a%s%p]*)</td>",start)
    if t~=nil then
    table.insert(conditions,t)
    table.insert(conditions_caps,string.upper(t))
    table.insert(conditions_lc,string.lower(t))
    --set short versions--------------------------------
    local cons=t
        for k,v in pairs(con_short) do
        cons=string.gsub(cons,k,v)
        end
    table.insert(conditions_short,cons)
    table.insert(conditions_short_caps,string.upper(cons))
    table.insert(conditions_short_lc,string.lower(cons))
    -----------------------------------------------------
    end
--match high temp
local s,f,t=string.find(allweather,"\"Hi\">([%p%d]*)&deg",start)
table.insert(high_temp,t)
--match low temp
local s,f,t=string.find(allweather,"\"Lo\">([%p%d]*)&deg",start)
table.insert(low_temp,t)
--match sun rise times
local s,f,t=string.find(allweather,"Rise:</strong> (%d*:%d*%s%u%u)</td>",start)
    if t~=nil then
    --get time only
    local a,b,tm=string.find(t,"([%d%p]*)")
    --get suffix only
    local a,b,suf=string.find(t,"(%u%u)")
        if translate==1 then
        suf=tsuffix[suf]
        else
        suf=suf
        end
    table.insert(sun_rise,tm.." "..suf)
    table.insert(sun_rise_lc,string.lower(tm.." "..suf))
    table.insert(sun_rise_time,tm)
    end
--match sun set times
local s,f,t=string.find(allweather,"Set:</strong> (%d*:%d*%s%u%u)</td>",f)
    if t~=nil then    
    --get time only
    local a,b,tm=string.find(t,"([%d%p]*)")
    --get suffix only
    local a,b,suf=string.find(t,"(%u%u)")
        if translate==1 then
        suf=tsuffix[suf]
        else
        suf=suf
        end
    table.insert(sun_set,tm.." "..suf)
    table.insert(sun_set_lc,string.lower(tm.." "..suf))
    table.insert(sun_set_time,tm)
    end
--moon rise
local s,f,t=string.find(allweather,"Rise:</strong> (%d*:%d*%s%u%u)</td>",f)
    if t~=nil then
    --get time only
    local a,b,tm=string.find(t,"([%d%p]*)")
    --get suffix only
    local a,b,suf=string.find(t,"(%u%u)")
        if translate==1 then
        suf=tsuffix[suf]
        else
        suf=suf
        end
    table.insert(moon_rise,tm.." "..suf)
    table.insert(moon_rise_lc,string.lower(tm.." "..suf))
    table.insert(moon_rise_time,tm)
    table.insert(moon_rise_ampm,suf)
    table.insert(moon_rise_ampm_lc,string.lower(suf))
    end
--moon set
local s,f,t=string.find(allweather,"Set:</strong> (%d*:%d*%s%u%u)</td>",f)
    if t~=nil then
    --get time only
    local a,b,tm=string.find(t,"([%d%p]*)")
    --get suffix only
    local a,b,suf=string.find(t,"(%u%u)")
        if translate==1 then
        suf=tsuffix[suf]
        else
        suf=suf
        end
    table.insert(moon_set,tm.." "..suf)
    table.insert(moon_set_lc,string.lower(tm.." "..suf))
    table.insert(moon_set_time,tm)
    table.insert(moon_set_ampm,suf)
    table.insert(moon_set_ampm_lc,string.lower(suf))
    end
--match uv index
local s,f,tuv=string.find(allweather,"UV Index:</strong>%s*(%d*%s*%([%a%s]*%))%s*<br />",start)
if tuv~=nil then
    --get just number
    local a,b,unm=string.find(tuv,"(%d*)%s*%([%a%s]*%)")
    --get just text
    local a,b,utx=string.find(tuv,"%d*%s*%(([%a%s]*)%)")
    table.insert(uv_index_num,unm)
        if translate==1 then
        utx=uvindextext[utx]
        else
        utx=utx
        end
    table.insert(uv_index_txt,utx)
    table.insert(uv_index_txt_caps,string.upper(utx))
    table.insert(uv_index_txt_lc,string.lower(utx))
    end
--match humidity
local s,f,t=string.find(allweather,"Humidity:</strong> (%d*)<br />",start)
table.insert(humidity,t)
--match ppt
local s,f,t=string.find(allweather,"Precipitation:</strong> (%d*)<br />",start)
table.insert(precipitation,t)
--match snow %
local s,f,t=string.find(allweather,"Snow Probability:</strong>%s*(%d*)<br />",start)
table.insert(snow,t)
--match cloud coveage
local s,f,t=string.find(allweather,"Cloud Coverage:</strong> (%d*)<br />",start)
table.insert(cloud_cover,t)
--match moon phase
local s,f,t=string.find(allweather,"Moon Phase:</strong> ([%a%s]*) <br />",start)
--set moon phase text
    if t~= nil then
    --set moon phase font and icon
    table.insert(moon_font,moonfontt[t])
    table.insert(moon_icon,moonicont[t])
        if translate==1 then
        t=moonphases[t]
        else
        t=t
        end
    table.insert(moon_phase,t)
    table.insert(moon_phase_caps,string.upper(t))
    table.insert(moon_phase_lc,string.lower(t))
    end
--match wind speeds
local s,f,tmph=string.find(allweather,"Wind Speed:</strong> (%d*)Mph",start)
local tmph=tonumber(tmph)
table.insert(wind_mph,tmph)
local s,f,t=string.find(allweather,"Mph%s*%((%d*)Km,",start)
table.insert(wind_km,t)
local s,f,t=string.find(allweather,"Km,%s*(%d*)Kts%)",start)
table.insert(wind_kts,t)
--match wind direction
local s,f,twd=string.find(allweather,"Wind Direction:</strong> ([%d&;%s%(%a%)]*)%s*</div>",start)
    if twd~=nil then
    local a,b,tdeg=string.find(twd,"(%d*)&deg;")
    table.insert(wind_deg,tdeg)
    --match wind font and nesw   
    local a,b,tnesw=string.find(twd,"%((%a*)%)")
    table.insert(wind_font,windfontt[tnesw])
        if tmph>0 and tmph<19 then
        table.insert(wind_icon,weathericons.."green_"..string.lower(tnesw)..".png")
        elseif tmph>18 and tmph<38 then
        table.insert(wind_icon,weathericons.."yellow_"..string.lower(tnesw)..".png")
        elseif tmph>37 and tmph<64 then
        table.insert(wind_icon,weathericons.."orange_"..string.lower(tnesw)..".png")
        elseif tmph>63 then
        table.insert(wind_icon,weathericons.."green_"..string.lower(tnesw)..".png")
        elseif tmph==0 then
        table.insert(wind_icon,weathericons.."no_wind.png")
        end
        if translate==1 then
        tnesw=neswtext[tnesw]
        else
        tnesw=tnesw
        end
    table.insert(wind_nesw,tnesw)
    end
if f==nil then break end
start=f
end--while
--#########################################################################################################################################

--#########################################################################
--get location
local a,b,wl=string.find(allweatherdata,"<title>%s*Intellicast%s%p%s(.*)</title>")
weather_location=string.gsub(wl," Extended Forecast in",",")
--#########################################################################

--#########################################################################
--format now weather
--extract current data
--get now weather chunk
local a,b,nowweather=string.find(allweatherdata,">Current Conditions&nbsp(.*)>View Detailed Observations for the last<br />")
now={}
monthlong={Jan="January",Feb="February",Mar="March",Apr="April",May="May",Jun="June",Jul="July",Aug="August",Sep="September",Oct="October",Nov="November",Dec="December"}
local s,f,tnow=string.find(nowweather,"<div style=\"float:right;color:#666;\">  As of ([%d%p%a%s]*) %(Local Time%)")
local s,f,t=string.find(tnow,"(%d*%p%d*%s%a*) on")
--get time only
local a,b,ntm=string.find(t,"(%d*%p%d*)")
--get suffix only
local a,b,nsf=string.find(t,"(%u%u)")
if translate==1 then
suf=tsuffix[nsf]
else
suf=nsf
end
now["time"]=ntm.." "..suf
now["time_lc"]=string.lower(ntm.." "..suf)
now["time_num"]=ntm
now["time_ampm"]=suf
now["time_ampm_lc"]=string.lower(suf)
--get day
local s,f,t=string.find(tnow,"on (%a*)%s%d*")
if translate==1 then
day=daynames[t]
else
day=t
end
now["day"]=day
now["day_caps"]=string.upper(day)
now["day_lc"]=string.lower(day)
--short day names
local ds=dayshort[t]
now["day_short"]=ds
now["day_short_caps"]=string.upper(ds)
now["day_short_lc"]=string.lower(ds)
--get date
local s,f,t=string.find(tnow,"%s(%d%d)%s")
now["date"]=t
--get months
local s,f,t=string.find(tnow,"%d%d%s(%a*)%s%d")
if translate==1 then
mnth=monthlong[t]
now["month_short"]=monthshort[mnth]
now["month_short_caps"]=string.upper(monthshort[mnth])
now["month_short_lc"]=string.lower(monthshort[mnth])
mnth=monthnames[mnth]
else
now["month_short"]=t
now["month_short_caps"]=string.upper(t)
now["month_short_lc"]=string.lower(t)
mnth=monthlong[t]
end
now["month"]=mnth
now["month_caps"]=string.upper(mnth)
now["month_lc"]=string.lower(mnth)
--get year
local s,f,t=string.find(tnow,"%a%a%a%s(%d%d%d%d)")
now["year"]=t
--get weather icon
local s,f,t=string.find(nowweather,"40_white/(wx_[%d]*)%ppng%p%stitle=%p")
now["weather_icon"]=weathericons..wimage[t]..".png"
now["weather_font"]=wfont[t]
--class=%pIcon%p /> ([%a%s]*)%s*</td>
local s,f,t=string.find(nowweather,"class=%pIcon%p /> ([%a%s%p]*)%s*%s*</td>%s*<td class=%pEmpty%p>&nbsp;")
now["conditions"]=t
now["conditions_caps"]=string.upper(t)
now["conditions_lc"]=string.lower(t)
--set short versions------------------------
    local cons=t
    for k,v in pairs(con_short) do
    cons=string.gsub(cons,k,v)
    end
    now["conditions_short"]=cons
    now["conditions_short_caps"]=string.upper(cons)
    now["conditions_short_lc"]=string.lower(cons)
--------------------------------------------
local s,f,t=string.find(nowweather,"Temperature\">([%p%d]*)&deg")
now["temp"]=t
local s,f,t=string.find(nowweather,">Feels Like: ([%p%d]*)&deg;</a>")
now["feels_like"]=t
local s,f,t=string.find(nowweather,">Wind Chill: </a></td>%s*<td>([%p%d]*)&deg;</td>")
now["wind_chill"]=t
local s,f,t=string.find(nowweather,">Ceiling: </a></td>%s*<td>([%a%d]*)</td>")
if t~="Unl" then
local s,f,t=string.find(t,"([%d%p]*)")
tc=t..ceiling_unit
else
    if translate==1 then unlset=additional.Unl else unlset=t end
tc=unlset
end
now["ceiling"]=tc
now["ceiling_caps"]=string.upper(tc)
now["ceiling_lc"]=string.lower(tc)
--get heat index
local s,f,t=string.find(nowweather,">Heat Index: </a></td>%s*<td>([%p%d]*)&deg;</td>")
now["heat_index"]=t
--get visibility
local s,f,t=string.find(nowweather,">Visibility: </a></td>%s*<td>([%a%d%p]*)</td>")
if t~="Unl" then
local s,f,t=string.find(t,"([%d%p]*)")
tv=t..visibility_unit
else
    if translate==1 then unlset=additional.Unl else unlset=t end
tv=unlset
end
now["visibility"]=tv
now["visibility_caps"]=string.upper(tv)
--get dew point
local s,f,t=string.find(nowweather,">Dew Point: </a></td>%s*<td>([%p%d]*)&deg;</td>")
now["dew_point"]=t
--get wind speed
local s,f,t=string.find(nowweather,">Wind: </a></td>%s*<td>(%d*)mph</td>")
local tmph=tonumber(t)
now["wind_mph"]=t..wind_mph_unit
now["wind_mph_caps"]=string.upper(t..wind_mph_unit)
--convert mph to km and knots #################################################
--[[1 mile per hour = 0.869 international nautical mile per hour (knot)
     1 mile per hour = 1.609 kilometers per hour
     1 mile per hour = 0.4470 meter per second
     1 knot = 1.852 kilometers per hour
     1 knot = 0.5144 meter per second
     1 meter per second = 3.6 kilometers per hour]]
now["wind_km"]=round(tonumber(t)*1.609)..wind_km_unit
now["wind_km_caps"]=string.upper(round(tonumber(t)*1.609)..wind_km_unit)
now["wind_kts"]=round(tonumber(t)*0.869)..wind_kts_unit
now["wind_kts_caps"]=string.upper(round(tonumber(t)*0.869)..wind_kts_unit)
--#############################################################################
local s,f,t=string.find(nowweather,">Humidity: </a></td>%s*<td>(%d*)</td>")
now["humidity"]=t
--get wind direction #######################################################
local s,f,twd=string.find(nowweather,">Direction: </a></td>%s*<td style=[%p%a]*>([%d&;%s%(%a%)]*)</td>%s*</tr>")
--check for NA
local a,b,t=string.find(twd,"(%a*)")
local tnesw=t
if tnesw~="NA" then
local a,b,t=string.find(twd,"(%d*)&deg;")
now["wind_deg"]=t..wind_degrees_unit
local a,b,tnesw=string.find(twd,"%((%a*)%)")
    if tmph>0 and tmph<19 then
    now["wind_icon"]=weathericons.."green_"..string.lower(tnesw)..".png"
    elseif tmph>18 and tmph<38 then
    now["wind_icon"]=weathericons.."yellow_"..string.lower(tnesw)..".png"
    elseif tmph>37 and tmph<64 then
    now["wind_icon"]=weathericons.."orange_"..string.lower(tnesw)..".png"
    elseif tmph>63 then
    now["wind_icon"]=weathericons.."green_"..string.lower(tnesw)..".png"
    end
now["wind_font"]=windfontt[tnesw]
--################################
    if translate==1 then
    tnesw=neswtext[tnesw]
    else
    tnesw=tnesw
    end
--################################
now["wind_nesw"]=tnesw        
else
    if translate==1 then naset=additional.NA else naset="NA" end
now["wind_deg"]=naset
now["wind_icon"]=weathericons.."no_wind.png"
now["wind_nesw"]=naset
now["wind_font"]=windfontt["N"]
end
--END WIND DIRECTION #######################################################
--get pressure
local s,f,t=string.find(nowweather,">Pressure: </a></td>%s*<td>([%d%p]*)\"</td>")
now["pressure"]=t
--convert pressures ########################################################
--[[ 1 inch of mercury = 25.4 mm of mercury = 33.86 millibars
     = 33.86 hectoPascals]]
now["pressure_mb"]=round(tonumber(t)*33.86)
--##########################################################################
local s,f,t=string.find(nowweather,">Gusts: </a></td>%s*<td>([%d%a]*)</td>")
if t~="NA" then
local s,f,t=string.find(t,"(%d*)")
tg=t..wind_mph_unit
tgkm=round(tonumber(t)*1.609)..wind_km_unit
tgkts=round(tonumber(t)*0.869)..wind_kts_unit
else
    if translate==1 then naset=additional.NA else naset="NA" end
tg=naset
tgkm=naset
tgkts=naset
end
now["wind_gusts"]=tg
now["wind_gusts_caps"]=string.upper(tg)
now["wind_gusts_km"]=tgkm
now["wind_gusts_km_caps"]=string.upper(tgkm)
now["wind_gusts_kts"]=tgkts
now["wind_gusts_kts_caps"]=string.upper(tgkts)
--##########################################################################
--get hourly forecast options hour1--------------------
--get day 1 bit
local s,f,hfc=string.find(nowweather,"<td class=%pHour%p%sstyle=%ppadding%pleft([%a%d%p%s]*)%pdeg%p</strong>",1)
--get time and conditions
--<strong>1 PM</strong><br />%s*P Cloudy%s*</td>%s*<td class=%pHour%p
local a,b,t=string.find(hfc,"<strong>([%d%p]*)[%s%a]*</strong><br",1)
now["fc_hour1_time"]=t
local a,b,t=string.find(hfc,"<strong>[%d%p%s]*([%a]*)</strong><br",1)
        if translate==1 then
        t=tsuffix[t]
        else
        t=t
        end
now["fc_hour1_ampm"]=t
now["fc_hour1_ampm_lc"]=string.lower(t)
local a,b,t=string.find(hfc,"</strong><br%s/>%s*([%p%s%a]*)%s*</td>%s*<td class=%pHour%p",1)
now["fc_hour1_cond"]=t
now["fc_hour1_cond_lc"]=string.lower(t)
now["fc_hour1_cond_caps"]=string.upper(t)
----------set short versions--------------------------------
    local cons=t
        for k,v in pairs(con_short) do
        cons=string.gsub(cons,k,v)
        end
    now["fc_hour1_cond_short"]=cons
    now["fc_hour1_cond_short_caps"]=string.upper(cons)
    now["fc_hour1_cond_short_lc"]=string.lower(cons)
-------------------------------------------------------------
--get weather icon and font
local a,b,t=string.find(hfc,"32_white/(wx_[%d]*)%ppng%p%stitle=%p",1)
now["fc_hour1_wicon"]=weathericons..wimage[t]..".png"
now["fc_hour1_wfont"]=wfont[t]
--get temperature
--><strong>-5&deg;</strong></td>
local a,b,t=string.find(hfc,"><strong>([%p%d]*)&deg;</strong></td>",1)
now["fc_hour1_temp"]=t
--end of hour1 data gathering--repeat 2 more times
--get hourly forecast options hour2--------------------
local start=tonumber(b)
--get time and conditions
--<strong>1 PM</strong><br />%s*P Cloudy%s*</td>%s*<td class=%pHour"%p
local a,b,t=string.find(hfc,"<strong>([%d%p]*)[%s%a]*</strong><br",start)
now["fc_hour2_time"]=t
local a,b,t=string.find(hfc,"<strong>[%d%p%s]*([%a]*)</strong><br",start)
        if translate==1 then
        t=tsuffix[t]
        else
        t=t
        end
now["fc_hour2_ampm"]=t
now["fc_hour2_ampm_lc"]=string.lower(t)
local a,b,t=string.find(hfc,"</strong><br%s/>%s*([%a%s%p]*)%s*</td>%s*<td class=%pHour%p",start)
now["fc_hour2_cond"]=t
now["fc_hour2_cond_lc"]=string.lower(t)
now["fc_hour2_cond_caps"]=string.upper(t)
----------set short versions--------------------------------
    local cons=t
        for k,v in pairs(con_short) do
        cons=string.gsub(cons,k,v)
        end
    now["fc_hour2_cond_short"]=cons
    now["fc_hour2_cond_short_caps"]=string.upper(cons)
    now["fc_hour2_cond_short_lc"]=string.lower(cons)
-------------------------------------------------------------
--get weather icon and font
local a,b,t=string.find(hfc,"32_white/(wx_[%d]*)%ppng%p%stitle=%p",start)
now["fc_hour2_wicon"]=weathericons..wimage[t]..".png"
now["fc_hour2_wfont"]=wfont[t]
--get temperature
--><strong>-5&deg;</strong></td>
local a,b,t=string.find(hfc,"><strong>([%p%d]*)&deg;</strong></td>",start)
now["fc_hour2_temp"]=t
--end of hour2 data gathering--repeat 1 more times
--get hourly forecast options hour3--------------------
local start=tonumber(b)
--get time and conditions
--<strong>1 PM</strong><br />%s*P Cloudy%s*</td>%s*<td class=%pHour"%p
local a,b,t=string.find(hfc,"<strong>([%d%p]*)[%s%a]*</strong><br",start)
now["fc_hour3_time"]=t
local a,b,t=string.find(hfc,"<strong>[%d%p%s]*([%a]*)</strong><br",start)
        if translate==1 then
        t=tsuffix[t]
        else
        t=t
        end
now["fc_hour3_ampm"]=t
now["fc_hour3_ampm_lc"]=string.lower(t)
local a,b,t=string.find(hfc,"</strong><br%s/>%s*([%a%s%p]*)%s*</td>%s*<td class=%pHour%p",start)
now["fc_hour3_cond"]=t
now["fc_hour3_cond_lc"]=string.lower(t)
now["fc_hour3_cond_caps"]=string.upper(t)
----------set short versions--------------------------------
    local cons=t
        for k,v in pairs(con_short) do
        cons=string.gsub(cons,k,v)
        end
    now["fc_hour3_cond_short"]=cons
    now["fc_hour3_cond_short_caps"]=string.upper(cons)
    now["fc_hour3_cond_short_lc"]=string.lower(cons)
-------------------------------------------------------------
--get weather icon and font
local a,b,t=string.find(hfc,"32_white/(wx_[%d]*)%ppng%p%stitle=%p",start)
now["fc_hour3_wicon"]=weathericons..wimage[t]..".png"
now["fc_hour3_wfont"]=wfont[t]
--get temperature
--><strong>-5&deg;</strong></td>
local a,b,t=string.find(hfc,"><strong>([%p%d]*)",start)
now["fc_hour3_temp"]=t
--end of hour3 data gathering--finished for all hours
--ALERTS###############################################################
if alert_check==1 then
--set tables
alert_type={}
alert_issued={}
if alerttest~=0 then
alert_icon=weathericons.."icon_alert_1.gif"
--extract information into tables
local start=0
local f=1
while f~=nil do
local s,f,t=string.find(alertdata,"><strong class='Alert'>([%a%s]*)</strong><br/>",start)
    if t~=nil then
    table.insert(alert_type,string.upper(t))
    end--if t~=nil
local s,f,t=string.find(alertdata,"<br />([%d%a%s:]*)<br /><br />",start)
    if t~=nil then
    table.insert(alert_issued,t)
    end--if t~=nil
if f==nil then break end
start=f
alert_number=#alert_type
end--while
else
alert_icon=weathericons.."icon_alert_0.gif"
table.insert(alert_type,"NO ALERTS")
table.insert(alert_issued,"")
alert_number=0
end--alerttest~=nil
else
alert_type={}
alert_issued={}
alert_icon=weathericons.."icon_alert_0.gif"
table.insert(alert_type,"alerts turned off")
table.insert(alert_issued,"")
alert_number=0
end--if alert check ###########################################
--###############end of data processing########################

--#########################################################################
if testing==0 then
processall=0
print ("processing complete")
elseif testing==1 then
processall=1
end--if testing ==0
--###################################################################################
end--of data processing section #####################################################
--###################################################################################
if processall==0 or testing==1 then
_G.weather_script()
end
--#########################################################################################################
--###UNCOMMENT THE BELOW LINE TO ENABLE CPU DELAY##########################################################
--end--####### end of if updates>5 #############################
--#########################################################################################################

cairo_destroy(cr)
cairo_surface_destroy(cs)
cr=nil
--######################################
end-- end main function ################
--######################################
function round(num)
    local idp=tonumber(settings_table[5])
    local mult = 10^(idp or 0)
    return math.floor(num * mult + 0.5) / mult
end--of round function #################################################################
function string:split(delimiter)--######################################################
local result = { }
local from  = 1
local delim_from, delim_to = string.find( self, delimiter, from  )
while delim_from do
table.insert( result, string.sub( self, from , delim_from-1 ) )
from  = delim_to + 1
delim_from, delim_to = string.find( self, delimiter, from  )
end
table.insert( result, string.sub( self, from  ) )
return result
end--string split #######################################################################
function xout(txj)--c,a,f,fs,x,y,txt,j ##################################################
c=nil
c=(txj.c or default_color)
a=nil
a=(txj.a or default_alpha)
f=nil
f=(txj.f or default_font)
fs=nil
fs=(txj.fs or default_font_size)
x=nil
x=(txj.x or 0)
y=nil
y=(txj.y or 0)
txt=nil
txt=(txj.txt or "set txt")
j=nil
j=(txj.j or "l")
    local function col(c,a)
    return ( (c/0x10000) % 0x100)/255,( (c/0x100) % 0x100)/255,(c % 0x100)/255,a
    end--local function
cairo_select_font_face (cr, f, CAIRO_FONT_SLANT_NORMAL, CAIRO_FONT_WEIGHT_NORMAL);
cairo_set_font_size (cr, fs)
local text=string.gsub(txt," ","_")
extents=cairo_text_extents_t:create()
cairo_text_extents(cr,text,extents)
local wx=extents.width
cairo_set_source_rgba (cr,col(c,a))
if j=="l" then
cairo_move_to (cr,x,y)
adx=wx
elseif j=="c" then
cairo_move_to (cr,x-(wx/2),y)
adx=wx/2
elseif j=="r" then
cairo_move_to (cr,x-wx,y)
adx=0
end
cairo_show_text (cr,txt)
cairo_stroke (cr)
nextx=nil
nextx=adx+x
return nextx
end--function xout ###################################################################
function out(tx)--####################################################################
c=nil
c=(tx.c or default_color)
a=nil
a=(tx.a or default_alpha)
f=nil
f=(tx.f or default_font)
fs=nil
fs=(tx.fs or default_font_size)
x=nil
x=(tx.x or 0)
y=nil
y=(tx.y or 0)
txt=nil
txt=(tx.txt or "set txt")
local function col(c,a)
return ( (c/0x10000) % 0x100)/255,( (c/0x100) % 0x100)/255,(c % 0x100)/255,a
end--local function
cairo_select_font_face (cr, f, CAIRO_FONT_SLANT_NORMAL, CAIRO_FONT_WEIGHT_NORMAL);
cairo_set_font_size (cr, fs)
cairo_set_source_rgba (cr,col(c,a))
cairo_move_to (cr,x,y)
cairo_show_text (cr,txt)
cairo_stroke (cr)
end--function out ###################################################################
function image(im)--#################################################################
x=nil
x=(im.x or 0)
y=nil
y=(im.y or 0)
w=nil
w=(im.w or default_image_width)
h=nil
h=(im.h or default_image_height)
file=nil
file=tostring(im.file)
if file==nil then print("set image file") end
---------------------------------------------
local show = imlib_load_image(file)
if show == nil then return end
imlib_context_set_image(show)
if tonumber(w)==0 then 
width=imlib_image_get_width() 
else
width=tonumber(w)
end
if tonumber(h)==0 then 
height=imlib_image_get_height() 
else
height=tonumber(h)
end
imlib_context_set_image(show)
local scaled=imlib_create_cropped_scaled_image(0, 0, imlib_image_get_width(), imlib_image_get_height(), width, height)
imlib_free_image()
imlib_context_set_image(scaled)
imlib_render_image_on_drawable(x, y)
imlib_free_image()
show=nil
end--function image ##################################################################
--END OF SCRIPT
```

s11template.lua
```
--[[
 The latest script is a lua only weather script. aka: v9000
 http://crunchbanglinux.org/forums/topic/16100/weather-in-conky/

 the file:
http://dl.dropbox.com/u/19008369/v9000.tar.gz

 mrppeachys LUA Tutorial
 http://crunchbanglinux.org/forums/topic/17246/how-to-using-lua-scripts-in-conky/
]]
_G.weather_script = function()--#### DO NOT EDIT THIS LINE ##############
--these tables hold the coordinates for each repeat do not edit #########
top_left_x_coordinate={}--###############################################
top_left_y_coordinate={}--###############################################
--#######################################################################
--SET DEFAULTS ##########################################################
--set defaults do not localise these defaults if you use a seperate display script
default_font="Anonymous Pro:bold"--font must be in quotes
default_font_size=11
default_color=0xffffff--white
default_alpha=1--fully opaque
default_image_width=50
default_image_height=50
--END OF DEFAULTS #######################################################
--START OF WEATHER CODE -- START OF WEATHER CODE -- START OF WEATHER CODE
out({c=0x00BFFF,a=1,x=10,y=15,txt=now["date"].." "..now["month_short"].." "..now["year"]..": Fetched @ "..now["time"]})
image({x=20,y=20,h=40,w=40,file=now["weather_icon"]})
-- Temp / FeelsLike & CONDITIONS TEXT
out({c=0x48D1CC,a=1,f="digitalk",fs=50,x=80,y=60,txt=now["temp"]})
out({c=0x00BFFF,a=1,f="digitalk",fs=50,x=140,y=60,txt=now["feels_like"]})
out({c=0xA4FFA4,a=1,x=81,y=72,txt="Temp          WC · HI"})

out({c=0x48D1CC,a=1,f="Zekton",fs=18,x=10,y=94,txt=now["conditions"]})

-- data titles
--    data output 
datay=110   -- y=datay or
datayy=15   -- y=datay+(datayy*1) use 1 or more

out({c=0xFAFAEC,a=1,x=10,y=datay,txt="Wind Chill:"})
   out({c=0x48D1CC,a=1,x=70,y=datay,txt=now["wind_chill"].."°"})
out({c=0xFAFAEC,a=1,x=100,y=datay,txt="Heat Index:"})
   out({c=0xFF8C00,a=1,x=165,y=datay,txt=now["heat_index"].."°"})
out({c=0xFAFAEC,a=1,x=10,y=datay+(datayy*1),txt="Today's Hi·Lo:"})
   out({c=0xFF8C00,a=1,x=100,y=datay+(datayy*1),txt=high_temp[1].."°"})
   out({c=0x48D1CC,a=1,x=140,y=datay+(datayy*1),txt=low_temp[1].."°"})
out({c=0xFAFAEC,a=1,x=10,y=datay+(datayy*2),txt="Wind:"})
   out({c=0x48D1CC,a=1,x=60,y=datay+(datayy*2),txt=now["wind_km"]})
   out({c=0x48D1CC,a=1,x=110,y=datay+(datayy*2),txt=now["wind_nesw"]})
   out({c=0xFAFAEC,a=1,x=140,y=datay+(datayy*2),txt="@"})
   out({c=0x48D1CC,a=1,x=165,y=datay+(datayy*2),txt=now["wind_deg"]})
out({c=0xFAFAEC,a=1,x=10,y=datay+(datayy*3),txt="Hum:"})
   out({c=0x48D1CC,a=1,x=60,y=datay+(datayy*3),txt=now["humidity"].."%"})
out({c=0xFAFAEC,a=1,x=110,y=datay+(datayy*3),txt="DP:"})
   out({c=0x48D1CC,a=1,x=145,y=datay+(datayy*3),txt=now["dew_point"].."°"})
out({c=0xFAFAEC,a=1,x=10,y=datay+(datayy*4),txt="Bar:"})
   out({c=0x48D1CC,a=1,x=60,y=datay+(datayy*4),txt=now["pressure_mb"]})
out({c=0xFAFAEC,a=1,x=110,y=datay+(datayy*4),txt="Vis:"})
   out({c=0x48D1CC,a=1,x=145,y=datay+(datayy*4),txt=now["visibility"]})
out({c=0xFAFAEC,a=1,x=10,y=datay+(datayy*5),txt="Ceil:"})
   out({c=0x48D1CC,a=1,x=60,y=datay+(datayy*5),txt=now["ceiling"]})
out({c=0xFAFAEC,a=1,x=10,y=datay+(datayy*6),txt="Precip:"})
   out({c=0x48D1CC,a=1,x=60,y=datay+(datayy*6),txt=precipitation[1].."%"})
out({c=0xFAFAEC,a=1,x=110,y=datay+(datayy*6),txt="Cloud:"})
   out({c=0x48D1CC,a=1,x=150,y=datay+(datayy*6),txt=cloud_cover[1].."%"})
out({c=0xFAFAEC,a=1,x=10,y=datay+(datayy*7),txt="UV:"})
   out({c=0x48D1CC,a=1,x=60,y=datay+(datayy*7),txt=uv_index_num[1]})
   out({c=0x48D1CC,a=1,x=110,y=datay+(datayy*7),txt=uv_index_txt[1]})
out({c=0xFAFAEC,a=1,x=10,y=datay+(datayy*8),txt="Sun:"})
   out({c=0xFAFAEC,a=1,x=60,y=datay+(datayy*8),txt=sun_rise_lc[1]})
   out({c=0x48D1CC,a=1,x=120,y=datay+(datayy*8),txt=sun_set_lc[1]})
out({c=0xFAFAEC,a=1,x=10,y=datay+(datayy*9),txt="Moon:"})
   out({c=0xFAFAEC,a=1,x=60,y=datay+(datayy*9),txt=moon_rise_lc[1]})
   out({c=0x48D1CC,a=1,x=120,y=datay+(datayy*9),txt=moon_set_lc[1]})
out({c=0xFAFAEC,a=1,x=10,y=datay+(datayy*10),txt="Phase:"})
   out({c=0x48D1CC,a=1,x=55,y=datay+(datayy*10),txt=moon_phase[1]})

-- line
image({x=205,y=5,w=1,h=260,file="/home/sector11/Conky/images/cyan-1.png"})
-- 3 hour output
out({c=0x48D1CC,a=1,f="Anonymous Pro:bold",fs=12,x=220,y=15,txt="Next 3"})
out({c=0x48D1CC,a=1,f="Anonymous Pro:bold",fs=12,x=220,y=30,txt="Hours"})
-- 1st hour
out({c=0xA4FFA4,x=220,y=50,txt=now["fc_hour1_time"].."  "..now["fc_hour1_ampm"]})
image({w=30,h=30,x=223,y=55,file=now["fc_hour1_wicon"]}) -- image({w=30,h=30,x=223,y=55,file="/home/sector11/Conky/images/red-1.png"})
out({x=228,y=100,txt=now["fc_hour1_temp"] .."°"})
-- 2nd hour
out({c=0xA4FFA4,x=220,y=datay+(datayy*1),txt=now["fc_hour2_time"].."  "..now["fc_hour2_ampm"]})
image({w=30,h=30,x=223,y=130,file=now["fc_hour2_wicon"]}) -- image({w=30,h=30,x=223,y=130,file="/home/sector11/Conky/images/red-1.png"})
out({x=228,y=180,txt=now["fc_hour2_temp"] .."°"})
-- 3rd hour
out({c=0xA4FFA4,x=220,y=210,txt=now["fc_hour3_time"].."  "..now["fc_hour3_ampm"]})
image({w=30,h=30,x=223,y=215,file=now["fc_hour3_wicon"]}) -- image({w=30,h=30,x=223,y=215,file="/home/sector11/Conky/images/red-1.png"})
out({x=228,y=datay+(datayy*10),txt=now["fc_hour3_temp"] .."°"})
-- line
image({x=275,y=5,w=1,h=260,file="/home/sector11/Conky/images/cyan-1.png"})

--start or weather forecast table section
--set start forecast day
start_day=1
--set total forecast days you want to display
number_of_days=5
topy=15
topyy=135 -- topy+(topyy*1)
topx=285
topxx=137.5
--set coordinates for top lef corners for each repeat
top_left_x_coordinate[1],top_left_y_coordinate[1]        =topx            ,topy
   top_left_x_coordinate[2],top_left_y_coordinate[2]     =topx ,150
top_left_x_coordinate[3],top_left_y_coordinate[3]        =10  ,290
   top_left_x_coordinate[4],top_left_y_coordinate[4]     =10+(topxx*1) ,290
top_left_x_coordinate[5],top_left_y_coordinate[5]        =10+(topxx*2)  ,290
--########################################################################################
for i=start_day,number_of_days-(start_day-1) do --start of day repeat, do not edit #######
tlx=top_left_x_coordinate[i] --sets top left x position for each repeat ##################
tly=top_left_y_coordinate[i] --sets top left y position for each repeat ##################
--########################################################################################
out({c=0xA4FFA4,a=1,x=tlx,y=tly,txt=forecast_day_short[i].."  "..forecast_date[i].."  "..forecast_month_short[i]})
image({x=tlx,y=tly+5,h=30,w=30,file=weather_icon[i]})
out({c=0xFF8C00,a=1,x=tlx+35,y=tly+15,txt=high_temp[i].."°"})
out({c=0x48D1CC,a=1,x=tlx+35,y=tly+30,txt=low_temp[i].."°"})
out({c=0x48D1CC,a=1,x=tlx,y=tly+50,txt=conditions_short[i]})

out({c=0xFAFAEC,a=1,x=tlx,y=tly+65,txt="P: "..precipitation[i].."%"})
   out({c=0xFAFAEC,a=1,x=tlx+50,y=tly+65,txt="UV: "..uv_index_num[i]})
out({c=0xFAFAEC,a=1,x=tlx,y=tly+80,txt="H: "..humidity[i].."%"})
out({c=0xFAFAEC,a=1,x=tlx,y=tly+95,txt="S: "..sun_rise_lc[i]})
   out({c=0x48D1CC,a=1,x=tlx+73,y=tly+95,txt=sun_set_lc[i]})
out({c=0xFAFAEC,a=1,x=tlx,y=tly+110,txt="M: "..moon_rise_lc[i]})
   out({c=0x48D1CC,a=1,x=tlx+73,y=tly+110,txt=moon_set_lc[i]})
--########################################################################################
end--of forecast repeat section ##########################################################
--########################################################################################
--END OF WEATHER CODE ----END OF WEATHER CODE ----END OF WEATHER CODE ---
--#######################################################################
end--of weather_display function do not edit this line ##################
--#######################################################################AAA

```

I am running Linux Mint 14, Cinnamon 1.6.7, kernel 3.5.0-44. I am thinking that it has to be a recent update to something that has caused this. I would appreciate any help.

---

### Post by stinkeye on 2013-12-22
Ask mrpeachy ...... [http://crunchbang.org/forums/viewtopic.php?id=16100&p=38](http://crunchbang.org/forums/viewtopic.php?id=16100&p=38)

---

### Post by MichaelGld on 2013-12-24
> **stinkeye said:**
> Ask mrpeachy ...... [http://crunchbang.org/forums/viewtopic.php?id=16100&p=38](http://crunchbang.org/forums/viewtopic.php?id=16100&p=38)

OK, thanks.

---

### Post by Paulgirardin on 2013-12-24
I'd stop working if they did that to me, too!

.....Wether may refer to:

    A castrated male goat
    A castrated male sheep

Merry Christmas ;)

---

