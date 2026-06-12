---
title: "Another gDesklets problem after update."
date: 2005-04-05
forum: General Help
---

### Post by haaglin on 2005-04-05
After i updated my ubuntu today, my gDesklets weather desklet dont work anymore. When i try to run it, i get this error:
```

Deprecation: Sensors are deprecated since v0.30.                                     
Please consider using controls and inline scripts.                                   
==========================================================[04/06/05-00:19:54]===     
Adding "/usr/share/gdesklets/Displays/lt-desklet/weather.display" with ID            
"id11127395944824" to the desklet list.                                              
Unhandled exception in thread started by <bound method                               
WeatherSensor.__get_weather_thread of <Weather.WeatherSensor object at 0xb6bb470c>>  
==========================================================[04/06/05-00:19:54]===     
=== Error in the core! Please report this bug!                                       
exceptions.KeyError:                                                                 
'url'                                                                                
in /usr/share/gdesklets/Sensors/Weather/__init__.py: line 246 __get_weather_thread   
in /usr/lib/gdesklets/sensor/Sensor.py: line 154 get_config                          
/usr/lib/gdesklets/sensor/Sensor.py                                                  
  149         if (value == self.__config_manager.UNDEF):                             
  150             value = self.__defaults.get(key, "")                               
  151                                                                                
  152         if (type(value) == str):                                               
  153             from utils import typeconverter                                    
> 154             dtype = self.__datatypes[key]                                      
  155             value = typeconverter.str2type(dtype, value)                       
  156                                                                                
  157         return value                                                           
  158                                                                                
  159                                                                                
  160                                                                                

``` 

The version i have now is 0.34.3

---

### Post by NeoChaosX on 2005-04-05
The lt desklets for some reason are broken in later versions of gDesklets. Try another weather desklet, like GoodWeather.

---

### Post by MetalMusicAddict on 2005-04-05
Synaptic shows "gdesklets-data" as "v33.1". Shouldnt that be updated as well?

---

