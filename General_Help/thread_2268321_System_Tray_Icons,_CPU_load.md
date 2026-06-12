---
title: "System Tray Icons, CPU load"
date: 2015-03-07
forum: General Help
---

### Post by pmi2 on 2015-03-07
I need a little help to understand how system tray icons work in Compiz, and why some of them seem to consume more CPU time than others.  (A link to a document would be great.)

Here's the specific issue:

I use Handbrake to encode videos to play on my codec-challenged TV.

When I enable the Handbrake system tray icon (the icon shows % of completion), Compiz goes from ~1% CPU (icon disabled) to 18~20% CPU (icon enabled), as reported in System Monitor.  This seems excessive on a quad core 3Ghz processor, or just plain wrong.  

At the same time, desktop performance goes from almost perfect to poor, and just dragging an open window across the screen is jerky and laggy, let alone anything else.  Enabling/disabling the system tray icon has a bigger effect on desktop performance than the encode process itself (!)

It happens regardless of adjusting Handbrake "nice-ness" until System Monitor shows "Low" priority in the right-hand column for the Handbrake process.  

(I can post screen shots from System monitor if that would help)

Thanks.

---

### Post by mc4man on 2015-03-07
I would say the Hb systray icon adds little to nothing here as far as compiz cpu use.
What session are you using? 
Here I'm on an ubuntu (unity) session but it's been patched to allow the systray, the  default 14.04 ubuntu session doesn't support  systray, only application-indicators.

---

### Post by pmi2 on 2015-03-07
> **mc4man said:**
> ...the  default 14.04 ubuntu session doesn't support  systray, only application-indicators.Thanks for the correction. It's a fairly new installation of Ubuntu/Unity.  I am avoiding any patches or add-ons, for now.  I did not even realize they were called Application Indicators, tbh.

In any case..., "application icons in the notification area in the top-right part of the screen" per ubuntu documentation.  In the Handbrake Preferences, the option is labeled "Show system tray icon".  

With the option checked, the % of completion appears in line with the rest of the indicators, and the Compiz CPU % (as reported in the System Monitor (Process Tab)  goes from 1% to ~18%.

---

### Post by pmi2 on 2015-03-08
Maybe some screen shots would explain this better.  

The first attachment is a System Monitor screen with the Handbrake system tray icon enabled (App Indicator w. % of Completion being displayed in the upper right corner of the screen).

The second attachment is with the system tray icon disabled, and the indicator with % of Completion NOT displayed.

Running Top in the terminal basically shows the same thing, with a little more detail, but in either case, turning on the System tray icon/App indicator results in Compiz going from 1% to about 18% of CPU time - on a Quad Core processor.

Putting this in perspective, playing the same video in SMPlayer only takes 8~10% of the CPU, or half as much as one tiny application indicator with a single numeric value.

---

### Post by pmi2 on 2015-03-10
I will mark this SOLVED, since I have found some answers in the Ubuntu online docs and other Forums.

---

