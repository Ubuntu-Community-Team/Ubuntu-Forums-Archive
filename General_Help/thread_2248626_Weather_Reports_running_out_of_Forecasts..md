---
title: "Weather Reports running out of Forecasts."
date: 2014-10-15
forum: General Help
---

### Post by BlinkinCat on 2014-10-15
Hi all,

I am currently running 14.04.1. It would appear that my Weather Reports are currently running out of Forecasts. (see screenshots). I have another user set up which has its Weather Reports from another location. This user presently has no Weather data recording at all. (No Forecasts either)

Does anyone have any suggestions ?

Cheers - :p

---

### Post by buzzingrobot on 2014-10-16
Some of these weather applets/indicators pull data from various servers and then format it for display. Most likely, the server(s) you are using are down or offline for a bit, or have changed their URL. You can wait it out, or try to use another location.

Others I've seen use a single source for all forecasts.

---

### Post by kc1di on 2014-10-16
I'll be following this thread with interest as I have a problem on one install that find no information not matter what location I enter :(

---

### Post by BlinkinCat on 2014-10-16
Hi @buzzingrobot - thanks for replying.

I tried changing the locations with no luck. The "recent changes" on [http://goodies.xfce.org/projects/panel-plugins/xfce4-weather-plugin](http://goodies.xfce.org/projects/panel-plugins/xfce4-weather-plugin) apparently indicate that there have been some recent issues. I've tried to muddle my way through the various recommendations but it is technically a little hard for me.
I really need step by step directions - that would really help me.

Thanks just the same!

---

### Post by mc4man on 2014-10-16
(- I don't use xfce so just a suggestion that's untested
Open up whatever you use for software sources & enable the -proposed repo, then update sources
You should then see an update for xfce4-weather-plugin to 0.8.3-1ubuntu0.1 as in screen (synaptic
Try that version
(then re-open your software sources & disable the proposed repo, ect.

---

### Post by buzzingrobot on 2014-10-16
Just FYI, that XFCE-goodies page shows 'met.no' -- the Norwegian weather service --as the source the plugin uses.

---

### Post by BlinkinCat on 2014-10-16
> **buzzingrobot said:**
> Just FYI, that XFCE-goodies page shows 'met.no' -- the Norwegian weather service --as the source the plugin uses.

Hi,

Yes I saw that, I think that is O.K. as their site indicated they collect data World-wide.

@mc4man - I'm afraid that I am not bright enough to implement your suggestions!

---

### Post by Mike_Walsh on 2014-10-16
> **kc1di said:**
> I'll be following this thread with interest as I have a problem on one install that find no information not matter what location I enter :(

Xubuntu, by any chance, Dave? My Xfce desktop on Ubuntu has been showing nothing in ITS weather window for the last couple of days, so I suspect you're not the only one who's noticed this..! :-k

I, too, shall be following this with interest.

Regards,

Mike.

---

### Post by CantankRus on 2014-10-16
Doing as mc4man said fixed here.
Im running Xubuntu and this is what I did.
Opened synaptic and in 
menu > settings > repositories > updates
enabled proposed.
Close software-properties and reload sources.

Search for **xfce4-weather-plugin** and mark for upgrade.
Once upgraded open **software-properties** again and disable the proposed repo.
Not a good idea to leave proposed enabled.
Remove and re-add the weather applet to the panel.

---

### Post by slickymaster on 2014-10-16
> **BlinkinCat said:**
> <...snip...>

@mc4man - I'm afraid that I am not bright enough to implement your suggestions!

Here's how you can do it, BlinkinCat:
[LIST=1]
[*]In a terminal window, issue the following command```
software-properties-gtk
```
[*]Once the Software & Updates dialog open, click the 'Updates' tab
[*]Tick the 'Pre-released updates (trusty-proposed)' option and enter your password when requested
[*]Click the 'Reload' button in the 'The information about available software is out-of-date' dialog+
[*]Run the 'Software Updater' application
[/LIST]

---

### Post by BlinkinCat on 2014-10-16
Hi slickymaster,

At first I couldn't see the dialog option 4.

I then unticked the other 3 options and was then able to click Reload.

The following error showed up :

$ software-properties-gtk

** (software-properties-gtk:26635): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-JKkEi4q3Ih: Connection refused

---

### Post by Elfy on 2014-10-16
nvm - sorry mc4man - didn't see you mention the SRU :)

---

### Post by slickymaster on 2014-10-16
> **BlinkinCat said:**
> Hi slickymaster,

At first I couldn't see the dialog option 4.

I then unticked the other 3 options and was then able to click Reload.

The following error showed up :

$ software-properties-gtk

** (software-properties-gtk:26635): WARNING **: Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-JKkEi4q3Ih: Connection refused

You shouldn't untick those three options. You have to end up with all the four options selected/ticked under "Install updates from:". Open again the 'Software & Updates' dialog, but this time through WhiskerMenu -> Settings -> Software & Updates, so you want see/get those warnings, and repeat the procedure.

---

### Post by mc4man on 2014-10-16
This thread does remind me of something that I have thought about but never pursed  - Can a normal repo be added and or disabled via cli like one  would do with a ppa?
(- the add-apt-repository deal

---

### Post by BlinkinCat on 2014-10-16
Hi all,

Hooray it is working at last ! I would like to thank all those who contributed to this thread - :p

Edit : I will mark thread as solved shortly unless someone wishes to reply to mc4man's question.

---

### Post by kc1di on 2014-10-16
> **Mike_Walsh said:**
> Xubuntu, by any chance, Dave? My Xfce desktop on Ubuntu has been showing nothing in ITS weather window for the last couple of days, so I suspect you're not the only one who's noticed this..! :-k

I, too, shall be following this with interest.

Regards,

Mike.

Yes Mike xubuntu 14.04.1 Will try the other suggestions about proposed and see if it fixes the problem.

---

### Post by kc1di on 2014-10-16
CantankRus  your fixed worked here - many thanks -- :) ;)

---

### Post by mc4man on 2014-10-16
> **BlinkinCat said:**
> Hi all,

Hooray it is working at last ! I would like to thank all those who contributed to this thread - :p

Edit : I will mark thread as solved shortly unless someone wishes to reply to mc4man's question.
Sorta have checked out & can't find a generic cli solution
add-apt-repository will work but doesn't seem to allow proposed to be enabled/disabled as a distro component which would allow a generic command.
(- it does work if using a specific, for instance here **if I'm using the US server**. So in that case  - 
this enables - 
```
sudo add-apt-repository 'deb http://us.archive.ubuntu.com/ubuntu/ trusty-proposed main multiverse restricted universe' && \
sudo apt-get update

```
This disables - 
```
sudo add-apt-repository -r 'deb http://us.archive.ubuntu.com/ubuntu/ trusty-proposed main multiverse restricted universe' && \
sudo apt-get update
```

So because one would need to find out what server someone is using to craft a command not all that useful vs. a gui method description,ect.

---

### Post by pqwoerituytrueiwoq on 2014-10-16
> **CantankRus said:**
> Doing as mc4man said fixed here.
Im running Xubuntu and this is what I did.
Opened synaptic and in 
menu > settings > repositories > updates
enabled proposed.
Close software-properties and reload sources.

Search for **xfce4-weather-plugin** and mark for upgrade.
Once upgraded open **software-properties** again and disable the proposed repo.
Not a good idea to leave proposed enabled.
Remove and re-add the weather applet to the panel.
thanks, that has been annoying me for a few days now
We can download the debs from here
[https://launchpad.net/ubuntu/+source/xfce4-weather-plugin](https://launchpad.net/ubuntu/+source/xfce4-weather-plugin)
* 64 bit deb: [https://launchpad.net/ubuntu/+source/xfce4-weather-plugin/0.8.3-1ubuntu0.1/+build/6459193/+files/xfce4-weather-plugin_0.8.3-1ubuntu0.1_amd64.deb](https://launchpad.net/ubuntu/+source/xfce4-weather-plugin/0.8.3-1ubuntu0.1/+build/6459193/+files/xfce4-weather-plugin_0.8.3-1ubuntu0.1_amd64.deb)
* 32 bit deb: [https://launchpad.net/ubuntu/+source/xfce4-weather-plugin/0.8.3-1ubuntu0.1/+build/6459196/+files/xfce4-weather-plugin_0.8.3-1ubuntu0.1_i386.deb](https://launchpad.net/ubuntu/+source/xfce4-weather-plugin/0.8.3-1ubuntu0.1/+build/6459196/+files/xfce4-weather-plugin_0.8.3-1ubuntu0.1_i386.deb)

---

### Post by Mike_Walsh on 2014-10-17
@slickymaster, mc4man & Cantankrus;

Nice one, guys; the fix worked perfectly, and everything's running nicely again.

Cheers! :D

Regards,

Mike.

---

### Post by ian-weisser on 2014-10-17
If you enable the -proposed repository, you must later disable it again.

-proposed is not intended for popular use.
It's the testing repo before updates are pushed to the -updates repo,
It's normally used for automated testing,
And packages in -proposed do occasionally cause breakage during that testing.

You can disable at any time after you have installed the relevant update.

---

