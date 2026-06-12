---
title: "[SOLVED] Ubuntu partition read-only??"
date: 2008-03-26
forum: General Help
---

### Post by VIPea on 2008-03-26
[SIZE="3"]I've just installed Ubuntu 7.10 on my PC, 
I have 2 hard drives - **75GB NTFS Windows** and from what I can gather **35GB ext3 Ubuntu**. The 2nd one is read-only but I can access the 1st and it's read-write. [/SIZE] 


[IMG]http://img441.imageshack.us/img441/7773/screenshotcomputerfilebrc3.png[/IMG]
**[SIZE="3"]sda1[/SIZE]**
[IMG]http://img441.imageshack.us/img441/4885/screenshot745gbvolumesdwi3.png[/IMG]
**[SIZE="3"]Filesystem[/SIZE]**
[IMG]http://img248.imageshack.us/img248/7298/screenshotfilesystemprozm7.png[/IMG]

[IMG]http://img338.imageshack.us/img338/3294/screenshotnautilusme0.png[/IMG]

[SIZE="4"]
I'm confused as to how this works? Please help me out and enlighten me[/SIZE]:confused:

---

### Post by ajmorris on 2008-03-26
hi there,
can you please post the output of the following commands:
```
sudo dmesg
```
```
sudo less /var/syslog
```

AJ

---

### Post by VIPea on 2008-03-26
```
[12494.948078] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[12494.948186] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[12495.055994] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[12495.171785] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[12495.299535] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[12495.434614] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[12495.535058] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[12495.535167] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[12495.638978] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[12495.758752] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[12495.895118] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[12496.033239] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[12496.140229] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3090 with error -110.
[12496.140352] phy0 -> rt73usb_rf_write: Error - PHY_CSR4 register busy. Write failed.
[12496.253778] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3024 with error -110.
[12496.361565] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3024 with error -110.
[12496.461494] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3020 with error -110.
[12496.581194] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3020 with error -110.
[12496.705030] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -110.
[12496.848750] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -110.
[12497.012426] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3050 with error -110.
[12497.120974] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3050 with error -110.
[12497.256909] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3064 with error -110.
[12497.391768] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3064 with error -110.
[12497.531541] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x01 failed for offset 0x0000 with error -110.
[12497.663269] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12497.810989] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3030 with error -110.
[12497.961281] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12498.122481] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12498.298287] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12498.464411] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12498.597589] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12498.614664] phy0 -> rt73usb_enable_radio: Error - Register initialization failed.
[12536.075228] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3008 with error -110.
[12536.175034] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3024 with error -110.
[12536.274963] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3024 with error -110.
[12536.374768] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3020 with error -110.
[12536.474569] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3020 with error -110.
[12536.574369] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -110.
[12536.674175] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -110.
[12536.773979] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3050 with error -110.
[12536.873915] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3050 with error -110.
[12536.973713] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3064 with error -110.
[12537.073519] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3064 with error -110.
[12537.173329] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x01 failed for offset 0x0000 with error -110.
[12537.273132] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12537.373059] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3030 with error -110.
[12537.472740] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12537.588637] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12537.704410] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12537.820192] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12537.935959] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12537.951852] phy0 -> rt73usb_enable_radio: Error - Register initialization failed.
[12538.171502] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3008 with error -110.
[12538.271299] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3024 with error -110.
[12538.371228] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3024 with error -110.
[12538.471033] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3020 with error -110.
[12538.570838] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3020 with error -110.
[12538.670643] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -110.
[12538.770449] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -110.
[12538.870377] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3050 with error -110.
[12538.970188] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3050 with error -110.
[12539.069991] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3064 with error -110.
[12539.169791] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3064 with error -110.
[12539.269595] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x01 failed for offset 0x0000 with error -110.
[12539.369399] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12539.469205] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3030 with error -110.
[12539.569009] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12539.684952] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12539.800682] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12539.916455] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12540.032232] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12540.048134] phy0 -> rt73usb_enable_radio: Error - Register initialization failed.
[12540.247938] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3008 with error -110.
[12540.347744] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3024 with error -110.
[12540.447547] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3024 with error -110.
[12540.547353] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3020 with error -110.
[12540.647158] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3020 with error -110.
[12540.747145] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -110.
[12540.846765] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -110.
[12540.946697] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3050 with error -110.
[12541.046500] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3050 with error -110.
[12541.146556] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3064 with error -110.
[12541.246109] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3064 with error -110.
[12541.345913] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x01 failed for offset 0x0000 with error -110.
[12541.445718] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12541.545523] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3030 with error -110.
[12541.645451] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12541.761222] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12541.876993] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12541.992767] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12542.108542] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12542.124505] phy0 -> rt73usb_enable_radio: Error - Register initialization failed.
[12584.900929] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3008 with error -110.
[12585.000612] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3024 with error -110.
[12585.100407] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3024 with error -110.
[12585.200220] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3020 with error -110.
[12585.304014] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3020 with error -110.
[12585.403811] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -110.
[12585.503751] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -110.
[12585.603547] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3050 with error -110.
[12585.703352] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3050 with error -110.
[12585.803157] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3064 with error -110.
[12585.902961] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3064 with error -110.
[12586.002764] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x01 failed for offset 0x0000 with error -110.
[12586.103341] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12586.203268] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3030 with error -110.
[12586.302305] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12586.418078] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12586.533978] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12586.649632] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12586.765401] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12586.781327] phy0 -> rt73usb_enable_radio: Error - Register initialization failed.
[12587.001959] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3008 with error -110.
[12587.100876] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3024 with error -110.
[12587.200676] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3024 with error -110.
[12587.300485] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3020 with error -110.
[12587.400287] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3020 with error -110.
[12587.500088] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -110.
[12587.600016] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -110.
[12587.699821] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3050 with error -110.
[12587.799629] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3050 with error -110.
[12587.910812] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3064 with error -110.
[12588.007237] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3064 with error -110.
[12588.140256] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x01 failed for offset 0x0000 with error -110.
[12588.302771] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12588.402577] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3030 with error -110.
[12588.502382] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12588.618154] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12588.733926] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12588.849827] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12588.965599] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12588.981427] phy0 -> rt73usb_enable_radio: Error - Register initialization failed.
[12589.181176] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3008 with error -110.
[12589.280976] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3024 with error -110.
[12589.380790] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3024 with error -110.
[12589.480715] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3020 with error -110.
[12589.580522] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3020 with error -110.
[12589.680326] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -110.
[12589.780129] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -110.
[12589.879936] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3050 with error -110.
[12589.979738] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3050 with error -110.
[12590.079546] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3064 with error -110.
[12590.179350] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3064 with error -110.
[12590.279280] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x01 failed for offset 0x0000 with error -110.
[12590.379082] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12590.478890] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3030 with error -110.
[12590.578692] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12590.694585] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12590.810232] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12590.926140] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12591.044036] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12591.057758] phy0 -> rt73usb_enable_radio: Error - Register initialization failed.
[12651.307094] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3008 with error -110.
[12651.407025] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3024 with error -110.
[12651.506828] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3024 with error -110.
[12651.606635] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3020 with error -110.
[12651.706436] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3020 with error -110.
[12651.806243] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -110.
[12651.906047] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -110.
[12652.005852] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3050 with error -110.
[12652.105781] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3050 with error -110.
[12652.205586] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3064 with error -110.
[12652.305389] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3064 with error -110.
[12652.405197] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x01 failed for offset 0x0000 with error -110.
[12652.504999] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12652.604805] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3030 with error -110.
[12652.704608] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12652.820381] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12652.936156] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12653.052053] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12653.167827] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12653.183690] phy0 -> rt73usb_enable_radio: Error - Register initialization failed.
[12660.255212] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3008 with error -110.
[12660.355015] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3024 with error -110.
[12660.454945] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3024 with error -110.
[12660.554754] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3020 with error -110.
[12660.654552] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3020 with error -110.
[12660.754357] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -110.
[12660.854163] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -110.
[12660.953965] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3050 with error -110.
[12661.053897] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3050 with error -110.
[12661.153702] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3064 with error -110.
[12661.253506] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3064 with error -110.
[12661.353310] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x01 failed for offset 0x0000 with error -110.
[12661.453116] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12661.553045] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3030 with error -110.
[12661.652868] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12661.768623] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12661.884396] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12662.000167] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12662.117447] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12662.131848] phy0 -> rt73usb_enable_radio: Error - Register initialization failed.
[12662.351485] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3008 with error -110.
[12662.451411] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3024 with error -110.
[12662.551214] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3024 with error -110.
[12662.651018] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3020 with error -110.
[12662.750824] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3020 with error -110.
[12662.850630] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -110.
[12662.950433] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -110.
[12663.050238] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3050 with error -110.
[12663.150174] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3050 with error -110.
[12663.249979] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3064 with error -110.
[12663.349777] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3064 with error -110.
[12663.449582] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x01 failed for offset 0x0000 with error -110.
[12663.549386] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12663.649191] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3030 with error -110.
[12663.748994] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12663.864894] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12663.980668] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12664.096442] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12664.213845] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12664.228123] phy0 -> rt73usb_enable_radio: Error - Register initialization failed.
[12664.427924] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3008 with error -110.
[12664.527729] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3024 with error -110.
[12664.627530] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3024 with error -110.
[12664.727334] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3020 with error -110.
[12664.827139] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3020 with error -110.
[12664.926945] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3040 with error -110.
[12665.026876] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3040 with error -110.
[12665.126679] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3050 with error -110.
[12665.226484] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3050 with error -110.
[12665.326288] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3064 with error -110.
[12665.426094] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3064 with error -110.
[12665.525896] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x01 failed for offset 0x0000 with error -110.
[12665.625703] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12665.726047] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x06 failed for offset 0x3030 with error -110.
[12665.825438] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12665.941206] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12666.056982] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12666.172753] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12666.288528] phy0 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x3030 with error -110.
[12666.304448] phy0 -> rt73usb_enable_radio: Error - Register initialization failed.
[12744.436132] usb 5-4: USB disconnect, address 3
[12746.410565] usb 5-4: new high speed USB device using ehci_hcd and address 5
[12746.728356] usb 5-4: configuration #1 chosen from 1 choice
[12746.991361] wmaster0: Selected rate control algorithm 'simple'
[12747.727785] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[12768.734794] wlan0: Initial auth_alg=0
[12768.734802] wlan0: authenticate with AP 00:1c:10:bf:97:de
[12768.741552] wlan0: RX authentication from 00:1c:10:bf:97:de (alg=0 transaction=2 status=0)
[12768.741557] wlan0: authenticated
[12768.741560] wlan0: associate with AP 00:1c:10:bf:97:de
[12768.745032] wlan0: RX AssocResp from 00:1c:10:bf:97:de (capab=0x401 status=0 aid=1)
[12768.745037] wlan0: associated
[12768.747518] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[12779.036779] wlan0: no IPv6 routers present
[12814.570973] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[12814.571070] wlan0: deauthenticate(reason=3)
[12876.460159] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[12878.492629] wlan0: Initial auth_alg=0
[12878.492637] wlan0: authenticate with AP 00:1c:10:bf:97:de
[12878.494269] wlan0: RX authentication from 00:1c:10:bf:97:de (alg=0 transaction=2 status=0)
[12878.494273] wlan0: authenticated
[12878.494276] wlan0: associate with AP 00:1c:10:bf:97:de
[12878.496628] wlan0: RX AssocResp from 00:1c:10:bf:97:de (capab=0x401 status=0 aid=1)
[12878.496631] wlan0: associated
[12878.499079] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[12879.495576] wlan0: duplicate address detected!
[12887.470960] wlan0: duplicate address detected!
[13558.265864] phy1 -> rt2x00usb_vendor_request: Error - Vendor Request 0x07 failed for offset 0x308c with error -110.

```

```
/var/syslog: No such file or directory

```

---

### Post by ajmorris on 2008-03-26
oh sorry, the second command, the log is in /var/log/syslog

---

### Post by LK_gandalf_ on 2008-03-26
maybe you can't change the permission because you need to be root. try launching your file manager from the console "sudo yourfilemanager" (I don't know the name, I use kubuntu and dolphin)
then change the option, and try.

---

### Post by VIPea on 2008-03-27
I tried that, it didn't work. 

Can anyone help? Why can I access my windows drive but not my ubuntu?

---

### Post by mikewhatever on 2008-03-27
Ubuntu system partition is, in fact, read only for a regular user. It may seem strange, especially to a Windows adim by default, for more info check [http://psychocats.net/ubuntu/permissions](http://psychocats.net/ubuntu/permissions)

---

### Post by VIPea on 2008-03-27
> **mikewhatever said:**
> Ubuntu system partition is, in fact, read only for a regular user. It may seem strange, especially to a Windows adim by default, for more info check [http://psychocats.net/ubuntu/permissions](http://psychocats.net/ubuntu/permissions)

Thank you! Finally an answer that makes sense. I suspected something of the sort. 
The "Filesystem" partition is **35GB** but only **5.4GB** is being used. 

[SIZE="2"]**Is there a way that I can create another partition from this drive that can hold my Ubuntu files?**[/SIZE] 
If so, how do I do it safely?

---

### Post by mikewhatever on 2008-03-27
You can hold them in /home/your_user_name, where you have full read/write access. Only the / is protected.

---

### Post by VIPea on 2008-03-27
:roll: I'm feeling kinda stupid now. lol. Just getting used to Ubuntu.

And the home folder's files are held on the same HD?

---

### Post by mikewhatever on 2008-03-27
> **VIPea said:**
> :roll: I'm feeling kinda stupid now. lol. Just getting used to Ubuntu.

And the home folder's files are held on the same HD?

No worries, I feel like that all the time. :popcorn:

---

### Post by VIPea on 2008-03-27
Hehehe. 
Thank you so much for the help! Now I'm set and ready to use Ubuntu! [-o<:guitar::mrgreen:

---

