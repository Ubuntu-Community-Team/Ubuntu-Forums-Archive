---
title: "Conky - TransparentTiles2dayweather"
date: 2015-11-11
forum: General Help
---

### Post by v3.xx on 2015-11-11
Its not displaying the forcast.  I changed my location in the conky_weather file.

```
${execi 300 curl -s "http://weather.yahooapis.com/forecastrss?w=[COLOR="#FF0000"]USMT0031[/COLOR]&u=c"
```

[ATTACH=CONFIG]265492[/ATTACH]

~/.cache/weather.xml reads..

```
<?xml version="1.0" encoding="UTF-8" standalone="yes" ?>
<rss version="2.0" xmlns:yweather="http://xml.weather.yahoo.com/ns/rss/1.0" xmlns:geo="http://www.w3.org/2003/01/geo/wgs84_pos#">
<channel>
<title>Yahoo! Weather - Error</title>
<description>Yahoo! Weather Error</description>
<item><title>City not found</title><description>
[COLOR="#FF0000"]Invalid Input /forecastrss?w=USMT0031&amp;u=c[/COLOR]
</description></item></channel></rss>
<!-- fan485.sports.gq1.yahoo.com Wed Nov 11 07:25:48 PST 2015 -->
```

I have tried another location with the same result.

---

### Post by QDR06VV9 on 2015-11-11
Do you have curl installed?

---

### Post by v3.xx on 2015-11-11
> **runrickus said:**
> Do you have curl installed?

Hi runrickus

Yes it is installed and I should mention this is Mate 16.04

---

### Post by QDR06VV9 on 2015-11-11
If you would give me a location that you want weather from(City, State)
You can PM me with that if you want.
Oh and by the way this is not on a VMBox is it?

---

### Post by QDR06VV9 on 2015-11-11
Ok here is your  WOEID "2364254"
Without the Quotes of course.:D
So yours should look like this now
> ${execi 300 curl -s "http://weather.yahooapis.com/forecastrss?w=2364254&u=f" -o ~/.cache/weather.xml}

I also took the liberty to change Celsius to Ferinheight, If you want to change it back, Just change the** &u=f**  to   **&u=c**

---

### Post by v3.xx on 2015-11-11
Yes, yes and yes.  All is well :D

Your WOEID provided the correct link.  And the change to f was a nice plus that I needed.

Thanks runrickus

[ATTACH=CONFIG]265505[/ATTACH]

---

### Post by QDR06VV9 on 2015-11-11
Glad I could help my friend
Best Regards

---

### Post by v3.xx on 2015-11-12
And just to let you know, it tweaked out nicely

[ATTACH=CONFIG]265523[/ATTACH]

Edit:
When I take the VM off of pause, it takes several minutes for the weather to update.  I think I need a refresh button for weather.xml.

---

### Post by QDR06VV9 on 2015-11-12
Well you can try to come up with some sort of refresh mechanism, Or you could just install Conky Manager.
And it will do that for you along with managing multiple conkyrc's.
I use it because i like to change my conkys from day to day, everything is done on the fly.
More information on conky manager
[http://www.teejeetech.in/p/conky-manager.html](http://www.teejeetech.in/p/conky-manager.html)
Cheers

---

### Post by v3.xx on 2015-11-12
This refresh rate is controlled by conkyrc_weather/update_interval 600

I have set it to 6 seconds and now getting prompt updates.  But I wonder if this constant updating is a good idea.  I think I still want a refresh button.

And I am running conky-manager :)

---

### Post by QDR06VV9 on 2015-11-12
You could make a script along the lines of something like this
```
killall -SIGUSR1 conky
```
Mod it to your Liking, Then add to a panel or shortcut or whatever.
Sheesh, Picky Picky Picky.:D

---

### Post by v3.xx on 2015-11-12
> **runrickus said:**
> You could make a script along the lines of something like this
```
killall -SIGUSR1 conky
```
Mod it to your Liking, Then add to a panel or shortcut or whatever.
Sheese Picky Picky Picky.:D

From what I understand, this forces conky configuration files to reconfigure, but this did not refresh the weather.

More pondering necessary :)  But that will be later, wife says I can't play anymore, time to do my errands.  I reset the refresh rate to 60 seconds, I can live with this, I guess, if I have to :p

---

### Post by vasa1 on 2015-11-12
> **v3.xx said:**
> This refresh rate is controlled by conkyrc_weather/update_interval 600

I have set it to 6 seconds and now getting prompt **updates**.  But I wonder if this constant **updating** is a good idea.  I think I still want a refresh button.

And I am running conky-manager :)

What is the distinction between updating versus refreshing?

Isn't the value after *execi* all you need to tweak as far as this particular conky goes?

```
${execi 300 curl -s "http://weather.yahooapis.com/forecastrss?w=USMT0031&u=c"
```

---

### Post by v3.xx on 2015-11-13
Good morning to you both.

> What is the distinction between updating versus refreshing?

None, I just want the widget to refresh.

> Isn't the value after execi all you need to tweak as far as this particular conky goes?

It may be, I do not understand that value.

During my search for a weather widget I came across one that had a refresh button built into it.  I am going to find that one again and see if I can import the code to my current widget (that would be sweet).  If I cannot, I should be able to use the code to create a refresh button in my panel.

---

