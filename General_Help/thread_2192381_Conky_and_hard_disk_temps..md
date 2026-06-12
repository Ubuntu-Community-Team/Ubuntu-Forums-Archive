---
title: "Conky and hard disk temps."
date: 2013-12-07
forum: General Help
---

### Post by philinux on 2013-12-07
I got two temps from laptop but not hard drive.

Disks utility can see it no problem. But hddtemp needs sudo. If disks can see it what is it using. I can use that then.
Maybe have to look at disks source code.

Anyone sorted this without resorting to sudoers etc etc.

---

### Post by ajgreeny on 2013-12-07
Here's the line I use in my .conkyrc file to get hddtemp showing the temperature of the disk
```
Disk Temperature:        ${execi 60 hddtemp /dev/sda | cut -c 30-32} C
```
You may need to change the figures I use in the "pipe to cut" to suit your system hardware without extraneous text.

To get the output of hddtemp to show without using sudo you can simply change the mode of the hddtemp executable with command ```
sudo chmod u+s /usr/sbin/hddtemp
``` which allows it to run as user.

I do the same for vnstat output in conky, with the exception being that the executable for that is in /usr/bin not /usr/sbin

---

### Post by philinux on 2013-12-07
Ah righto that seems safe enough.  I still wonder how Disks gets it though.

---

### Post by r-senior on 2013-12-08
Another way is to run hddtemp as a daemon and get the data from it using netcat:

[http://linux.die.net/man/8/hddtemp](http://linux.die.net/man/8/hddtemp)

See 'Tcp/Ip Daemon Mode'

Being curious, I had a quick poke around in the code for the gnome-disks program and it uses 'udisks_drive_ata_get_smart_temperature()' from the udisks library to get the temperatures, i.e. it is not using a command line utility, it goes straight to the udisks daemon.

[http://udisks.freedesktop.org/docs/latest/](http://udisks.freedesktop.org/docs/latest/)

However ... there is a command line utility called udisks that should give you hours of fun with Conky because it shows all the SMART data -- temperatures, power cycle counts, power on time.

```
$ udisks --show-info /dev/sda
```

---

### Post by philinux on 2013-12-08
Nice one r-senior this works a treat.

```
udisks --show-info /dev/sda | grep temp | cut -c 52-53
```

[edit] this is now working in conky. ${execi 60 udisks --show-info /dev/sda | grep temp | cut -c 52-54}

---

### Post by Mopar1973Man on 2013-12-08
After installing the hddtemp daemon you can use the hddtemp variable from Conky.

[http://conky.sourceforge.net/variables.html](http://conky.sourceforge.net/variables.html)

---

### Post by r-senior on 2013-12-08
Nice! For anyone whose daemon is not started:

```
sudo dpkg-reconfigure hddtemp
```

This also gives the option of making hddtemp suid root.

---

### Post by philinux on 2013-12-08
Question is how come udisks doesn't need sudo but hddtemp does. I'd be interested if anyone knows.

---

### Post by stinkeye on 2013-12-08
> **philinux said:**
> Question is how come udisks doesn't need sudo but hddtemp does. I'd be interested if anyone knows.
Don't know the answer to that one, but **r-senior's** answer, installing hddtemp with the SUID, allowing it to be run by regular users
 is the way to use hddtemp with conky.

Then you can just use in conky...
```
${execpi 10 hddtemp -n /dev/sda}
```

To change color according to temperature you can also send it to a colorize script...
_ColorTempHDD.sh_
```
#!/bin/bash
# colorize.sh
# by: Crinos512

COOL=[COLOR="#FF8C00"]25[/COLOR]
WARM=[COLOR="#FF0000"]50[/COLOR]

if [[ $1 < $COOL ]]
   then echo "\${color7}"$1    # COOL
elif [[ $1 > $WARM ]]
   then echo "\${color9}"$1    # HOT
else echo "\${color8}"$1       # WARM
fi

exit 0
```
Set your [COLOR="#FF8C00"]temp[/COLOR] [COLOR="#FF0000"]ranges[/COLOR].
Define color7, color8 and color9 in your conky config or change "**color7**" etc to a color in the script...eg "**color FF0000**" or "**color red**"

eg this is my conky line...
```
${execpi 10 hddtemp -n /dev/sda | xargs /home/glen/conky/ColorTemp/ColorTempHDD.sh}°C
```

You can use copies of the same script to colorize cpu and gpu temps.

---

### Post by philinux on 2013-12-08
I decided to do away with hddtemp and use this.

${execi 60 udisks --show-info /dev/sda | grep temp | cut -c 52-54}

Seems to work well.

---

### Post by stinkeye on 2013-12-08
> **philinux said:**
> I decided to do away with hddtemp and use this.

${execi 60 udisks --show-info /dev/sda | grep temp | cut -c 52-54}

Seems to work well.

Try just using awk instead of grep and cut...
```
udisks --show-info /dev/sda | awk '/temp/ {print $6}'
```

---

### Post by r-senior on 2013-12-08
That doesn't work on all disks because udisks puts '|' characters in that bottom section and sometimes you lose spaces:

```
$ udisks --show-info /dev/sda | awk '/temp/'
 temperature-celsius-2       104[color="red"]| 91|[/color]  0    n/a    39C / 102F  Old-age  Online
$ udisks --show-info /dev/sdb | awk '/temp/'
 temperature-celsius-2        41[color="red"]|253|[/color]  0    n/a    42C / 108F  Old-age  Online 

```

But it's easily fixed by replacing all the '|' with a space:

```
udisks --show-info /dev/sda | awk '/temp/ {gsub(/\|/, " ", $0); print $6}'
```

This is a useful pattern for anything in that bottom section:

```
udisks --show-info /dev/sda | awk '/reallocated-sector-count/ {gsub(/\|/, " ", $0); print $6}'
```

---

### Post by philinux on 2013-12-08
I never checked up on awk. You know copy and paste stuff. I didn't realise it was small c type language for manipulating strings. I used to do high level cobol so I will use awk as you suggested.

Cheers r-senior and stinkeye.

I find it bizarre that you would need sudo to get at a system temp.

---

### Post by appo2 on 2014-05-23
> **stinkeye said:**
> Don't know the answer to that one, but **r-senior's** answer, installing hddtemp with the SUID, allowing it to be run by regular users
 is the way to use hddtemp with conky.

Then you can just use in conky...
```
${execpi 10 hddtemp -n /dev/sda}
```

To change color according to temperature you can also send it to a colorize script...
_ColorTempHDD.sh_
```
#!/bin/bash
# colorize.sh
# by: Crinos512

COOL=[COLOR=#FF8C00]25[/COLOR]
WARM=[COLOR=#FF0000]50[/COLOR]

if [[ $1 < $COOL ]]
   then echo "\${color7}"$1    # COOL
elif [[ $1 > $WARM ]]
   then echo "\${color9}"$1    # HOT
else echo "\${color8}"$1       # WARM
fi

exit 0
```
Set your [COLOR=#FF8C00]temp[/COLOR] [COLOR=#FF0000]ranges[/COLOR].
Define color7, color8 and color9 in your conky config or change "**color7**" etc to a color in the script...eg "**color FF0000**" or "**color red**"

eg this is my conky line...
```
${execpi 10 hddtemp -n /dev/sda | xargs /home/glen/conky/ColorTemp/ColorTempHDD.sh}°C
```

You can use copies of the same script to colorize cpu and gpu temps.

My ColorTempHDD.sh

```

#!/bin/bash
# ColorTempHDD.sh
# by: appo
# color3 = Green
# color1 = Yellow
# color2 = Red

GOOD=43 # From 1 to 43 Green
WARM=49 # From 41 to 49 Yellow
ALARM=70 # From 49 to &#8734; Red

if   [[ $1 = $GOOD ]]
   then echo "\${color3}"$1    
elif [[ $1 < $GOOD ]]
   then echo "\${color3}"$1   
elif [[ $1 = $WARM ]]
   then echo "\${color1}"$1    
elif [[ $1 < $WARM ]]
   then echo "\${color1}"$1  
elif [[ $1 = $ALARM ]]
   then echo "\${color2}"$1    
elif [[ $1 < $ALARM ]]
   then echo "\${color2}"$1    
fi

exit 0

```

---

