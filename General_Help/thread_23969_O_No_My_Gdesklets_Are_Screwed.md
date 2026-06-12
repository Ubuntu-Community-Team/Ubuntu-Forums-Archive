---
title: "O No My Gdesklets Are Screwed"
date: 2005-04-04
forum: General Help
---

### Post by somuchfortheafter on 2005-04-04
obviously as you can tell my gdesklets are no longer working, I just did the latest hoary updates and I had a crash after installing the large ammounts of skins for xmms as mentioned in the graphics thread. Well umm I kind of need gdesklets. The program will run and all of my desklets will load however with the execption of my rss viewers all applications have returned to their default values of crap.... this kinda sucks. Also whenever I try to configure the desklet I am prompted by this error
```

exceptions.NameError:                                                                
global name 'runner' is not defined                                                  
  216     step_count = int((Dsp.gauge_f.width.as_px() - 2)/step_width)               
  217     Dsp.gauge_g.width = Unit(step_count*step_width, PX)                        
  218                                                                                
  219 def run():                                                                     
  220     if cf_command != "":                                                       
> 221         runner.command = "%s &"%cf_command                                     
  222                                                                                
  223 def set_gauge(val):                                                            
  224     sn = 100.0/step_count                                                      
  225     Dsp.gauge.fill = int(sn*int(val/sn))+1                                     
  226                                                                                
  227 def font_size(font, size, mod = None):                                         

```
any ideas anyone. lastly this is called an error in the script by the announcement on screen.

---

### Post by erkki70 on 2005-04-05
Hi,
Did you have a look to this post?
[http://www.ubuntuforums.org/showthread.php?t=23901&highlight=gdesklets](http://www.ubuntuforums.org/showthread.php?t=23901&highlight=gdesklets)

Hope this helps,

Cheers,
Erkki

---

### Post by somuchfortheafter on 2005-04-05
sorry but it doesnt but thanks for the  help.

---

