---
title: "Redshift on Xubuntu"
date: 2015-10-12
forum: General Help
---

### Post by michael-piziak on 2015-10-12
Unlike my Ubuntu 12.04 lts hp desktop,

When I open RedShift on my Xubuntu laptop, it closes itself before it executes - ?

---

### Post by howefield on 2015-10-12
Try opening it via the terminal, you may get some clues in the output. I think it is ..

```
gtk-redshift
```

---

### Post by michael-piziak on 2015-10-12
> **howefield said:**
> Try opening it via the terminal, you may get some clues in the output. I think it is ..

```
gtk-redshift
```


michael@michael-HP-2000-Notebook-PC:~$ gtk-redshift
Trying location provider `geoclue'...
Started Geoclue provider `Geoclue Master'.
Using provider `geoclue'.

** (process:2308): WARNING **: Could not get location, 3 retries left.


** (process:2308): WARNING **: Could not get location, 2 retries left.


** (process:2308): WARNING **: Could not get location, 1 retries left.


** (process:2308): WARNING **: Provider does not have a valid location available.
Unable to get location from provider.
michael@michael-HP-2000-Notebook-PC:~$

---

### Post by tristan16 on 2015-10-12
The easiest solution would be to manually set your location. Follow the guide here: [http://jonls.dk/redshift/](http://jonls.dk/redshift/) and get your latitude and longitude from here: [http://www.latlong.net/](http://www.latlong.net/)

---

### Post by howefield on 2015-10-12
Might also be worth checking which version you have, the current version is 1.10.

---

### Post by michael-piziak on 2015-10-12
I'm on my hp desktop right now and would like to set it's location (Ubuntu 12.04 lts)

I live in Beckley, West Virginia, USA, zipcode 25801

Can someone tell me exactly what to type in terminal to set my redshift location?


Michael


Then I'll try it on the Xubuntu hp notebook

p.s. the instructions on the page are a bit over my head.
For example Denmark is this, but I don't really know where the coordinates come from:   [COLOR=#2f4f4f][FONT=Menlo]$ redshift -l 55.7:12.6 -t 5700:3600 -g 0.8 -m randr -v[/FONT][/COLOR]

---

### Post by tristan16 on 2015-10-12
> **michael-piziak said:**
> I'm on my hp desktop right now and would like to set it's location (Ubuntu 12.04 lts)

I live in Beckley, West Virginia, USA, zipcode 25801

Can someone tell me exactly what to type in terminal to set my redshift location?


Michael


Then I'll try it on the Xubuntu hp notebook

p.s. the instructions on the page are a bit over my head.
For example Denmark is this, but I don't really know where the coordinates come from:   [COLOR=#2f4f4f][FONT=Menlo]$ redshift -l 55.7:12.6 -t 5700:3600 -g 0.8 -m randr -v[/FONT][/COLOR]

In your home folder, press Ctr+H to show hidden files, go to the .config folder, and create a file called redshift.conf. Copy and paste this into it:

```

temp-day=6500
temp-night=3500
transition=1
brightness=1.0
brightness-day=1.0
brightness-night=1.0
gamma=0.8:0.7:0.8
gamma-day=0.8:0.7:0.8
gamma-night=0.6
location-provider=manual
adjustment-method=randr
[manual]
lat=37.778170
lon=-81.188156
[randr]
screen=0

```

Now when you start Redshift, it will set its location to Beckley, West Virginia.

---

### Post by michael-piziak on 2015-10-12
> **tristan16 said:**
> In your home folder, press Ctr+H to show hidden files, go to the .config folder, and create a file called redshift.conf. Copy and paste this into it:

```

temp-day=6500
temp-night=3500
transition=1
brightness=1.0
brightness-day=1.0
brightness-night=1.0
gamma=0.8:0.7:0.8
gamma-day=0.8:0.7:0.8
gamma-night=0.6
location-provider=manual
adjustment-method=randr
[manual]
lat=37.778170
lon=-81.188156
[randr]
screen=0

```

Now when you start Redshift, it will set its location to Beckley, West Virginia.


ok, I know how to create a folder, but how to create a file in there?

---

### Post by CantankRus on 2015-10-12
...or without using a config...
```
gtk-redshift -l 37.78:-81.19 -t 5500:3500 -g 0.8 -b 0.9 -m randr -v
```

From **man redshift**...
```
NAME
       redshift - Set color temperature of display according to time of day.

SYNOPSIS
       redshift
        -l LAT:LON -t DAY:NIGHT [OPTIONS...]

DESCRIPTION
       redshift  adjusts  the  color  temperature of your screen according to your surroundings. This may help
       your eyes hurt less if you are working in front of the screen at night.

       The color temperature is set according to the position of the sun. A different color temperature is set
       during night and daytime. During twilight and early morning, the color temperature transitions smoothly
       from night to daytime temperature to allow your eyes to slowly adapt.


       -h     Display this help message

       -v     Verbose output

       -V     Show program version

       -b N   Screen brightness to apply (max is 1.0)

       -c FILE
              Load settings from specified configuration file

       -g R:G:B
              Additional gamma correction to apply

       -l LAT:LON
              Your current location

       -l PROVIDER
              Select provider for automatic location updates (Type `list' to see available providers)

       -m METHOD
              Method to use to set color temperature (Type `list' to see available methods)

       -o     One shot mode (do not continuously adjust color temperature)

       -O TEMP
              One shot manual mode (set color temperature)

       -x     Reset mode (remove adjustment from screen)

       -r     Disable temperature transitions

       -t DAY:NIGHT
              Color temperature to set at daytime/night
```

---

### Post by tristan16 on 2015-10-12
> **CantankRus said:**
> ...or without using a config...
```
gtk-redshift -l 37.78:-81.19 -t 5500:3500 -g 0.8 -b 0.9 -m randr -v
```

From **man redshift**...
```
NAME
       redshift - Set color temperature of display according to time of day.

SYNOPSIS
       redshift
        -l LAT:LON -t DAY:NIGHT [OPTIONS...]

DESCRIPTION
       redshift  adjusts  the  color  temperature of your screen according to your surroundings. This may help
       your eyes hurt less if you are working in front of the screen at night.

       The color temperature is set according to the position of the sun. A different color temperature is set
       during night and daytime. During twilight and early morning, the color temperature transitions smoothly
       from night to daytime temperature to allow your eyes to slowly adapt.


       -h     Display this help message

       -v     Verbose output

       -V     Show program version

       -b N   Screen brightness to apply (max is 1.0)

       -c FILE
              Load settings from specified configuration file

       -g R:G:B
              Additional gamma correction to apply

       -l LAT:LON
              Your current location

       -l PROVIDER
              Select provider for automatic location updates (Type `list' to see available providers)

       -m METHOD
              Method to use to set color temperature (Type `list' to see available methods)

       -o     One shot mode (do not continuously adjust color temperature)

       -O TEMP
              One shot manual mode (set color temperature)

       -x     Reset mode (remove adjustment from screen)

       -r     Disable temperature transitions

       -t DAY:NIGHT
              Color temperature to set at daytime/night
```

That would require running this command every time you want to use redshift. Creating a config file allows the same settings to be used each time the program is launched.

---

### Post by CantankRus on 2015-10-12
> **tristan16 said:**
> That would require running this command every time you want to use redshift. Creating a config file allows the same settings to be used each time the program is launched.
Obviously, so you put that command into startups.
Just another option.

---

