---
title: "conky weather issue"
date: 2007-10-10
forum: General Help
---

### Post by Nick w on 2007-10-10
where am i going wrong.  i have the Weather title load into conky but no weather
this is my configc

#!/bin/sh

#
# Grab weather data from weather.com and format it according to the given XSLT
# Script written by boojit
# Modified by Hellf[i]re
# Modified by Vredfreak
# The orignal script and xslt can be downloaded from [http://pondol.com/weather.tar.gz](http://pondol.com/weather.tar.gz)

# Usage:
# ${execi 1800 /path/to/weather/weather.sh location}
# Usage Example:
# ${execi 1800 /home/user/weather/weather.sh 03833}

# your Location ID: use [http://xoap.weather.com/search/search?where=](http://xoap.weather.com/search/search?where=)[yourcity] to find it 
# U.S. users can just use their zip code; doubt that works for anyone else though (YMMV)
LOCID=LONDON

# s=standard units, m=metric units
UNITS=s

# where this script and the XSLT lives
RUNDIR=/home/nick/Mine/conky/conky-weather/

# there's probably other stuff besides CURL that will work for this, but i haven't 
# tried any others. 
# you can get curl at [http://curl.haxx.se/](http://curl.haxx.se/)
CURLCMD=/usr/bin/curl

# get it at [http://xmlsoft.org/XSLT/](http://xmlsoft.org/XSLT/)
XSLTCMD=/usr/bin/xsltproc

# you probably don't need to modify anything below this point....

# CURL url. Use cc=* for current forecast or dayf=10 to get a multi-day forecast
CURLURL="http://xoap.weather.com/weather/local/$LOCID?dayf=10&unit=$UNITS&cc=*"

# The XSLT to use when translating the response from weather.com
# You can modify this xslt to your liking 
XSLT=$RUNDIR/weather.xslt 

#filter (if you want to convert stuff to lower-case or upper case or something)
#FILTER="|gawk '{print(tolower(\$0));}'"


#####
eval "$CURLCMD \"$CURLURL\" 2>/dev/null| $XSLTCMD $XSLT - $FILTER"

---

### Post by Nick w on 2007-10-11
bump

---

### Post by rand0m on 2007-10-21
Did you try LOCID: UKXX0085 ?

---

