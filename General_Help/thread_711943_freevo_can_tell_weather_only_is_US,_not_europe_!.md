---
title: "freevo can tell weather only is US, not europe !"
date: 2008-03-01
forum: General Help
---

### Post by frenchn00b on 2008-03-01
add this to your freevo config

```
 

plugin.activate('weather', level=45)
PLUGIN_WEATHER_LOCATIONS = [ 
      ("USNC0559", 1, "en", "Home sweet home"), 
      ("12603", 0), 
      ("15235"), 
      ("GMXX0154", 1, "de", "Aachen, Germany") 
    ]

```


how to fix it and make it wokr ? thansk !

---

