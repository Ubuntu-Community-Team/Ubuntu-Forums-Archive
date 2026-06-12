---
title: "Unwanted FireFox Link"
date: 2024-09-07
forum: General Help
---

### Post by mikegreen8 on 2024-09-07
Hi.
A link has suddenly appeared on my Firefox 130.0 under ubuntu 22.04.  (Weather Gatineau)

I never put it there, in fact I don't use links at all. 

I've cleared all history and bookmarks and it's still there. For now I use private browsing.

How do I get rid of this ?
Thanks,
M...

---

### Post by Frogs Hair on 2024-09-07
Have you installed a weather extension by chance ? If so you can remove it.

---

### Post by mikegreen8 on 2024-09-07
Hi.

No I've never installed a weather extension.

I'm worried about this link - and how did it get there ??

Thanks for the prompt reply,
M...

---

### Post by 1fallen on 2024-09-07
Just a little info on that, Nightly builds of Firefox, which represent Firefox 128, now include a weather widget. It appears every time you open a new tab page, and has a few options.


The widget uses AccuWeather as the data source, and offers a few customization options. You can switch it from Fahrenheit to Celsius, enable more detailed view, hide it from the new tab page, and visit the help page on the Mozilla website. All the options reside in the menu of the three button next to the forecast.

More on that here: [https://www.omgubuntu.co.uk/2024/06/firefox-127-weather-new-tab-feature](https://www.omgubuntu.co.uk/2024/06/firefox-127-weather-new-tab-feature)

---

### Post by nicolasdentremont on 2024-09-07
Possibly from a recent update

From the Mozilla website:

> 
Users in the United States and Canada can view local weather directly on the new tab page. Additionally, they have the option to select a specific location to see current weather conditions.

---

### Post by mikegreen8 on 2024-09-07
Hi and thanks for the informative response.

So how do I get rid of this widget ?? I don't see why they put it there in the first place.  I can't find any option to delete it.

Thanks,
M...

---

### Post by 1fallen on 2024-09-07
This disables it, It dose not remove it, that's on mozilla end.
Go to "**about:config**" in the URL, then search for:
```
browser.newtabpage.activity-stream.system.showWeather
```
And there just toggle to disable it (true false)

Screenshot added to help.

---

### Post by mikegreen8 on 2024-09-07
Thank you 1fallen2

I did toggle to disable and that worked just fine.

So is Mozilla doing this to get add revenue ?? If so, NOT NICE.

I have read that widgets can be planted by 'bad players', and that they can act as holes to allow them to get into the system. That's why I got nervous about it.

Is there a way to tell Mozilla to not plant these widgets in the future ??

Thanks for your help,
M...

---

### Post by 1fallen on 2024-09-07
> **mikegreen8 said:**
> Thank you 1fallen2

I did toggle to disable and that worked just fine.
Nice
> **mikegreen8 said:**
> 
So is Mozilla doing this to get add revenue ?? If so, NOT NICE.
It was actually a request by users, but yes it's a convince at a price. ;)
> **mikegreen8 said:**
> 
I have read that widgets can be planted by 'bad players', and that they can act as holes to allow them to get into the system. That's why I got nervous about it.
I understand and actually traced it to this code, but it is Mozzilla Devs that are writing it. (Not that it makes it completely safe>>>Experimental currently)
> **mikegreen8 said:**
> 
Is there a way to tell Mozilla to not plant these widgets in the future ??
Telling someone or something has a negative reaction, asking or a polite request would serve better. (Just saying :))

---

### Post by mikegreen8 on 2024-09-08
Thanks 1fallen2. Have a nice day.
M...

---

### Post by Frogs Hair on 2024-09-10
Accuweather is now a FF sponsor , hence the widget.

---

### Post by mikegreen8 on 2024-09-11
Hi.
Yes I figured it was ad revenue. How many more widgets can we expect as more sponsors come on board ??

I would like to see a 'right click' on the widget with an option to delete.

A little disappointed in Mozilla. Maybe if there were enough complaints.......

Thanks for the info and have a nice day,
M...

---

