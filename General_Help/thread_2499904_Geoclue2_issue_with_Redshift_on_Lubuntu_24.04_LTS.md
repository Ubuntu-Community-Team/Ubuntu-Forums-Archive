---
title: "Geoclue2 issue with Redshift on Lubuntu 24.04 LTS"
date: 2024-08-14
forum: General Help
---

### Post by hessajee on 2024-08-14
I've done a clean install of Lubuntu 24.04 LTS on my laptop alongside a Windows 7 installation (I'm aware of the security implications hence the transition to a Linux distro) where I use f.lux to avoid eye strain. I chose Lubuntu as it is meant to be a lightweight Ubuntu flavour. 

Now, I discovered Lubuntu uses LXQt and Redshift. As Redshift has a limited GUI, I read [#1]("https://manual.lubuntu.me/stable/2/2.4/2.4.8/Redshift.html") and [#2 ]("https://help.ubuntu.com/community/Redshift") to understand how to configure Redshift to work to my needs. (N.B. There are typos/missing info in the details shared in both links which I've figured out.) I created redshift.conf and placed it in my $HOME/.config directory after discovering how to enable hidden files and folders (Ctrl + H).

First, I set:
```

location-provider=geoclue2

```

#2 said 'geoclue' but this doesn't work hence I set it to 'geoclue2' after finding info on the topic.

Then I run redshift-qt via the terminal. It outputs the following and then hangs when trying to obtain the location information:
```

"Solar elevations: day above 3.0, night below -6.0"
"Temperatures: 6500K at day, 3000K at night"
"Brightness: 1.00:1.00"
"Gamma (Daytime): 0.900, 0.900, 0.900"
"Gamma (Night): 0.900, 0.900, 0.900"

```

It is not obvious that it hangs until I click on the Redshift icon in the panel. It states the following:
```

"Waiting for initial location to become available..."
"poll: Interrupted system call"
"Unable to get location from provider."

```

The same occurs when I run Redshift from the start menu. 

If I set the location-provider=manual and input my latitude and longitude, I have no issues.

Is there a way to obtain the location information automatically please or is it no longer possible so I have to manually set longitude and latitude? The answers that I've found from other posts with users experiencing the same issues tend to revolve around manual settings or older posts where they just uninstalled and reinstalled redshift and it somehow worked. 

I'm not quite sure where to ask this last question in the forums, so I'll leave it here: Will Lubuntu 24.10 go in the same direction as Ubuntu and provide something like Night Light?

Thanks in advance.

---

### Post by #&amp;thj^% on 2024-08-14
Important read: [https://discourse.mozilla.org/t/retiring-the-mozilla-location-service/128693](https://discourse.mozilla.org/t/retiring-the-mozilla-location-service/128693)
The cause looks to be that Redshift by default automatically determines its location using the geoclue library which in turn uses the Mozilla Location Service. That service has been shut down on June 12.

Hopefully Redshift can be patched to work without this. For right now the solution is to manually specify a location in Redshift, so that it doesn't need to use that service. For that you need the latitude and longitude of your location. Here's an example how to manually specify the location: [https://wiki.archlinux.org/title/Redshift#Specify_location_manually](https://wiki.archlinux.org/title/Redshift#Specify_location_manually) ... n_manually

```
/usr/lib/geoclue-2.0/demos/where-am-i
Client object: /org/freedesktop/GeoClue2/Client/2

New location:
Latitude:    33.438279°
Longitude:   -112.017829°
Accuracy:    3202952.431633 meters
Speed:       29714.929652 meters/second
Heading:     180.169710°
Description: GeoIP
Timestamp:   Wed 14 Aug 2024 10:53:15 AM MDT (1723654395 seconds since the Epoch)

```

---

### Post by hessajee on 2024-08-20
Thank you for your reply. 

I have manually specified my location using latittude and longitude as mentioned in my initial post. However, I don't know if that can be classified as a solution to a problem where it would previously run automatically, thereby not requiring user intervention if one moves location/travels frequently. So I don't think I should mark this post as solved.

I've tried where-am-i but I get no response. I manually installed GeoClue2 as well and still have the same problem. 

It seems that RedShift was updated a long time ago and I don't forsee any future updates to resolve this issue. Hopefully the Lubuntu developers can incorporate their own version of Redshift or Night Light similar to Ubuntu.

---

### Post by #&amp;thj^% on 2024-08-20
For now I use something like this:
```
redshift-gtk -l $lat:$lon 2>/dev/null &

```
We all seem to classify things differently for the means to an end>>>solution or work-around.

---

