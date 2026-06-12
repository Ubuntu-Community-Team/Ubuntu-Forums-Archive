---
title: "fprint log in sudo"
date: 2014-12-18
forum: General Help
---

### Post by ddhuy on 2014-12-18
[LEFT][COLOR=#333333][FONT=UbuntuRegular]A while ago I was trying to get my fingerprint reader to work, compiling an experimental version of fprint. Since then, every time I sudo, in stead of asking for my password I get an fprint log. Actually, I do get the question to fill in my password, but it is immediately filled with the output of the fprint log.[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]How do I get rid of this? 
I can press enter and then get a second chance to fill in my sudo password, so I'm not completely stuck, it's just anoying to get this every time and I would like to get rid of it.
[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]I assume I somehow accidentally made an incorrect pipe or something. But I have no idea how or how to undo it.[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]Here is an example:[/FONT][/COLOR][/LEFT]
```
$ sudo su
[sudo] password for dimi: 1418130792.818 fp:debug [fp_init] 
1418130792.819 fp:debug [register_driver] registered driver upekts
1418130792.819 fp:debug [register_driver] registered driver upeke2
1418130792.820 fp:debug [register_driver] registered driver aes4000
1418130792.820 fp:debug [register_driver] registered driver aes2501
1418130792.820 fp:debug [register_driver] registered driver aes2550
1418130792.820 fp:debug [register_driver] registered driver uru4000
1418130792.820 fp:debug [register_driver] registered driver vcom5s
1418130792.820 fp:debug [register_driver] registered driver upeksonly
1418130792.820 fp:debug [register_driver] registered driver aes1610
1418130792.820 fp:debug [register_driver] registered driver aes1660
1418130792.820 fp:debug [register_driver] registered driver aes2660
1418130792.820 fp:debug [register_driver] registered driver vfs101
1418130792.820 fp:debug [register_driver] registered driver vfs301
1418130792.820 fp:debug [register_driver] registered driver vfs5011
1418130792.820 fp:debug [register_driver] registered driver upektc
1418130793.014 fp:debug [find_supporting_driver] driver vfs5011 supports USB device 138a:0011
1418130793.014 fp:debug [find_supporting_driver] selected driver vfs5011 supports USB device 138a:0011
1418130793.014 sync:debug [fp_dev_open] 
1418130793.014 async:debug [fp_async_dev_open] 
1418130793.014 async:error [fp_async_dev_open] usb_open failed, error -3
1418130793.016 fp:debug [fp_exit]
```

---

### Post by bapoumba on 2014-12-20
You said you compiled an experimental version of fprint. Could you please provide more info ? I have no fingerprint reader, so I'm not sure I would know how to test or help you further, but how is this package supposed to behave when the sudo password has to be entered in a terminal ?

---

