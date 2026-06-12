---
title: "Problem with dconf Editor re: panel clock format"
date: 2019-10-01
forum: General Help
---

### Post by kesetyan on 2019-10-01
Hi,

I am running a dual boot Windows 7 / Lubuntu 18.04 desktop pc.  I have recently installed the Mate desktop which I now use in preference to the LXDE desktop in Lubuntu (Mate seems more stable on my system).

One thing I have found with Mate is it is more difficult to modify certain panel settings, specifically the clock.  Apparently it is necessary to use the dconf Editor so I downloaded and installed it.  I seem to have made an error using the editor as now it doesn't list the clock after I tried unsuccessfully to edit the clock format settings. Initially, when I navigated to 'org.mate.panel.applet.clock' and edited the format for the clock, it gave an error relating to the schema.  Mistakenly, thinking I needed to clear the path in the search field, I clicked the 'Reset Visible Keys' item.  Since then, any search for  'org.mate.panel.applet.clock' results in a 'No Matches' message.

'org.mate.panel.applet.clock.gschema.xml' is still safely located in the /usr/share/glib-2.0 folder and the clock is still showing in the panel and running correctly.  I don'[t fully understand dconf Editor and don't know if the problem I have caused with it can be easily corrected.  I wonder also, is there any other way i might be able to edit the clock format?

I'd be grateful for any assistance, thank you.  Cheers.

---

