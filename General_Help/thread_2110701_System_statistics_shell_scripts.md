---
title: "System statistics shell scripts"
date: 2013-01-30
forum: General Help
---

### Post by Gotti on 2013-01-30
I'm not sure if this is the correct forum for this, so mods feel free to move it as you see fit.

I started this a few years ago, and it's been sitting dormant until a few weeks ago.

The idea here is to use conky (an awesome lightweight system stats monitior,) and instead of using the available variables conky provides (which can be quite limiting,) to write small shell scripts to display the information instead. 

I have all the obvious ones done (disk free information, network information, battery, etc.,) and it looks (IMO) quite clean and nice. (I'll have a screenshot and link at the end of this post.)

I guess what I'm hoping for with this post is a spitballing of ideas session for new scripts to write, or maybe even some script submissions. Ultimately, I'd like to get a gtk frontsend going where you can load different scripts and change the order in which they're displayed. As of right now, all fo that has to be done by manually editing either the actual scripts themselves or .conkyrc.)

Anyhoo...I'll post of few examples of scripts I've done, and the output will be visible on the provided screenshot.

System Info:
```
life=$(acpi | awk '{ print $4 }' | awk -F , '{ print $1 }')
temp=$(sudo hddtemp /dev/sda | awk -F: {' print $3 '} | awk {' print $1 '})
status=$(acpi | awk '{ print $3 }' | awk -F , '{ print $1 }')


echo CPU Temperature: $temp
echo Battery Life: $life
echo "Battery:" $status
```

Network Info:
```
# Variables. Change 'wlan0' to reflect your network adapter.
network=$(iwconfig wlan0 | grep ESSID | awk -F'"' '{ print $2 }')
one=$(iwconfig wlan0 | grep Quality | awk -F= {' print $2 '} | awk -F/ {' print $1 '})
two=$(iwconfig wlan0 | grep Quality | awk -F= {' print $2 '} | awk -F/ {' print $2 '} | awk {' print $1 '})
quality=$(calc $one/$two | awk -F. '{ print $2 }' | head -c 2)
qualitychars=$(calc $one/$two | awk -F. '{ print $2 }' | head -c 2 | wc | awk {' print $3-$1 '})
netaddr=$(ifconfig wlan0 | grep "inet addr" | awk -F: {' print $2 '} | awk {' print $1 '})

# Output
echo "Connected to:" $network
# This loop was added to fix a bug that displayed
# percentages ending in "0" (40, 50, 60) as one digit.
# Ex. 50% was displayed as 5%. This loop checks the word count
# of the quality variable and acts accordingly.
if [ $qualitychars = 2 ]
then
echo "Link Quality:" $quality%
elif [ $one = $two ]
then
echo "Link Quality: 100%"
else
echo "Link Quality:" $quality"0%"
fi
# End of Link Quality loop.
echo "Address:" $netaddr
```

IP's of machines connected to current network:
```
rawlist=$(nmap -sP 192.168.1.0/24 | grep 'Nmap scan report' | sed 's/[^0-9.]*//g')
while :
do
rm ~/.rawlist
rm ~/.hostsonline
echo $rawlist >> ~/.rawlist
tr ' ' '\n' < ~/.rawlist >> ~/.hostsonline
sleep 30
done
```

As you can see, the scripts are quite small and rudimentary, so it isn't hard to do.

Here's the link to the blog that's covering the project. Any submissions would be posted and credited on here. (It's not that big of a deal...this thing gets no view lol.)

[http://spiritusproject.blogspot.com/](http://spiritusproject.blogspot.com/)

It's just something I did in my free time, and I enjoyed it...so I guess I'm just looking to fuel the fire.

Lastly, here's a screenshot of it in action. (Top right corner.) Also, feel free to tell me how absolutely amazing my fluxbox setup is =P.

[http://i45.tinypic.com/mcur77.jpg](http://i45.tinypic.com/mcur77.jpg)

---

### Post by Habitual on 2013-01-31
[quote=]Wow...this is still on the internet?[/quote]

I love[d] conky but after much conky.fu, I have grown to be tired of it's rather limited output, but good one for recognizing the modular approach to conky. :)

I stopped after this [IMG]http://i771.photobucket.com/albums/xx360/E522260/desktop_9_21_2010.png[/IMG]

---

