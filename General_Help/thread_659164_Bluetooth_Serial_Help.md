---
title: "Bluetooth Serial Help?"
date: 2008-01-05
forum: General Help
---

### Post by rentacop on 2008-01-05
Hey guys i have a quick question for you. I have been researching this for the past few days and still have not found an answer for it. 

I am trying to connect my tomtom One to ubuntu over bluetooth and dump the NMEA data over the bluetooth virtual serial port.

In order for me to connect my tomtom i type in the following code (xx:xx) being the mac address and the 1 after the mac address is to let the app on the tomtom know to dump the Nmea data.

 ```
rfcomm connect /dev/rfcomm1 XX:XX:XX:XX:XX:XX 1 
```

After i enter that code it shows my connection the screen of my tomtom so that works well.

Heres the part i am suck at. When i type the code below it should dump the NMEA data though the seiral port.

```
cat /dev/rfcomm1
```

whatever it starts to dump it is completely unreadable 

```

)&#65533;e&#65533;&#65533;a&#65533; &#65533;*
           Dx&#65533;
                 &#65533;
                  &#65533;&#65533;&#65533;g&#65533; &#65533;Q  â  &#138;  @    F  K
  üý&#9252;&#159;     &#9148;  ¢  3    ð     7  £  üý&#9229;&#159;           £  "
                                                         V  ³  [&#65533;
                                                                  #&#65533;&#65533;
A
&#65533;
>G
  &#134;


 ·
  &#139;&#140;
&#137;
&#131;
J&#135;
&#131;
@
üþ


```

If anyone knows what i need to do to make the text readable i would be very grateful for your help.

---

### Post by rentacop on 2008-01-06
bump

---

